---
title: 製作和發佈架構概觀
seo-title: 製作和發佈架構概觀
description: AEM Screens架構類似傳統的AEM Sites架構。 內容是在AEM作者例項上編寫，然後轉送複製至多個發佈例項。 請依照本頁進一步瞭解作者和發佈架構概觀。
seo-description: AEM Screens架構類似傳統的AEM Sites架構。 內容是在AEM作者例項上編寫，然後轉送複製至多個發佈例項。 請依照本頁進一步瞭解作者和發佈架構概觀。
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 0%

---


# 製作和發佈架構概觀 {#author-and-publish-architectural-overview}

本頁反白說明下列主題：

* **發佈伺服器簡介**
* **架構概觀**
* **註冊程式**

## 必備條件 {#prerequisites}

在開始使用作者和發佈伺服器之前，您應具備下列相關知識：

* **AEM Topology**
* **建立和管理AEM畫面專案**
* **裝置註冊程式**

>[!NOTE]
>
>只有在您已安裝AEM 6.4 Screens Feature Pack 2時，才能使用此AEM Screens功能。 若要存取此功能套件，您必須聯絡Adobe支援並要求存取權。 一旦您擁有權限，就可從「套件共用」下載。

## 簡介 {#introduction}

AEM Screens架構類似傳統的AEM Sites架構。 內容是在AEM作者例項上編寫，然後轉送複製至多個發佈例項。 AEM Screens裝置現在可以透過負載平衡器連線至AEM發佈群。 可新增多個AEM發佈例項，以繼續縮放發佈群。

*例如*,AEM Screens內容作者會在製作系統上針對設定為與發佈群組互動的特定裝置發出指令，或是針對AEM Screens內容作者發出指令，以取得有關設定為與發佈群組互動的裝置的資訊。

下圖說明作者和發佈環境。

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## 建築設計 {#architectural-design}

有五個體系結構元件，有助於此解決方案：

* ***將內容從作者複製*** ，以發佈至裝置以供顯示

* ***將二進位內容*** （從裝置接收）從發佈反向複製至作者
* ***從作者*** 傳送命令以透過特定REST API發佈
* ***在發佈例項*** 之間傳訊，以同步化裝置資訊更新和命令
* ***由發佈*** 例項的作者輪詢，以透過特定REST API取得裝置資訊

### 內容和配置的複製（轉發）  {#replication-forward-of-content-and-configurations}

標準複製代理用於複製螢幕通道內容、位置配置和設備配置。 這可讓作者更新渠道的內容，並選擇性地在發佈渠道更新之前先執行某種核准工作流程。 需要為發佈群中的每個發佈實例建立複製代理。

下圖說明了複製過程：

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>需要為發佈群中的每個發佈實例建立複製代理。

### 螢幕複製代理和命令  {#screens-replication-agents-and-commands}

「自訂畫面」特定的複製代理會建立，以將指令從「作者」例項傳送至AEM Screens裝置。 AEM Publish執行個體可做為將這些指令轉送至裝置的中介。

這可讓作者繼續管理裝置，例如傳送裝置更新並從作者環境擷取螢幕擷取。 AEM Screens複製代理具有自訂傳輸設定，例如標準複製代理。

### 發佈例項之間的訊息傳送  {#messaging-between-publish-instances}

在許多情況下，命令僅指一次傳送到設備。 但是，在負載平衡的發佈架構中，未知裝置要連接的發佈例項。

因此，作者實例會將消息發送到所有Publish實例。 但是，只應將單條消息中繼到設備。 為確保傳訊正確，發佈例項之間必須進行一些通訊。 這是使用 *Apache ActiveMQ Artemis實現的*。 每個發佈實例都使用Oak-based Sling發現服務放置在鬆散耦合的拓撲中，並且ActiveMQ被配置，以便每個發佈實例能夠通信並建立單個消息隊列。 「畫面」裝置會透過負載平衡器輪詢發佈群組，並從佇列頂端接收命令。

### 反向複製 {#reverse-replication}

在許多情況下，在執行命令後，Screens裝置會有某種回應，才會轉送至Author執行個體。 為了達到此AEM ***Reverse複製*** ，請使用。

* 為每個發佈實例建立一個反向複製代理，類似於標準複製代理和螢幕複製代理。
* 工作流程啟動程式設定會監聽在發佈例項上修改的節點，然後觸發工作流程，將裝置回應置於發佈例項的外框中。
* 此上下文中的反向複製僅用於設備提供的二進位資料（如日誌檔案和螢幕截圖）。 非二進位資料通過輪詢來檢索。
* 從AEM作者例項輪詢的反向複製會擷取回應並儲存至作者例項。

### 發佈例項的輪詢  {#polling-of-publish-instances}

作者實例需要能夠輪詢設備以獲得心跳並知道已連接設備的運行狀況。

裝置ping負載平衡器，並路由至發佈例項。 然後，發佈例項會透過Publish API公開裝置狀態，此API在 **api/screens-dcc/devices/static** ，針對所有作用中裝置提供；而 **api/screens-dcc/devices/&lt;device_id>/status.json** ，則適用於單一裝置。

作者實例輪詢所有發佈實例，並將設備狀態響應合併為單一狀態。 在作者上輪詢的已排程作 `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` 業是，可以根據cron運算式進行設定。

## 註冊 {#registration}

註冊會繼續產生於AEM作者例項。 AEM Screens Device會指向作者例項，且註冊已完成。

在作者環境中註冊裝置後，裝置設定和頻道／排程指派就會複製到AEM發佈例項。 接著會更新AEM Screens Device設定，以指向AEM發佈群組前方的負載平衡器。 這是一次性設定，當畫面裝置成功連線至發佈環境後，它就可繼續接收來自作者環境的指令，而不需將畫面裝置直接連接至作者環境。

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### 後續步驟 {#the-next-steps}

在您瞭解AEM畫面中作者的架構設計和發佈設定後，請參閱「設定AEM畫面的作者 [和發佈](author-and-publish.md) 」以取得詳細資訊。

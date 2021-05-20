---
title: 製作與發佈架構概觀
seo-title: 製作與發佈架構概觀
description: AEM Screens架構類似傳統AEM Sites架構。 內容是在AEM製作例項上製作，然後轉送複製到多個發佈例項。 請依照本頁所述，深入了解作者和發佈架構概觀。
seo-description: AEM Screens架構類似傳統AEM Sites架構。 內容是在AEM製作例項上製作，然後轉送複製到多個發佈例項。 請依照本頁所述，深入了解作者和發佈架構概觀。
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
feature: 管理畫面
role: Administrator, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 0%

---

# 製作與發佈架構概述{#author-and-publish-architectural-overview}

本頁面重點說明下列主題：

* **發佈伺服器簡介**
* **架構概述**
* **註冊過程**

## 必備條件 {#prerequisites}

開始使用作者和發佈伺服器之前，您應先了解：

* **AEM拓撲**
* **建立和管理AEM Screens專案**
* **設備註冊過程**

>[!NOTE]
>
>只有在您已安裝AEM 6.4 Screens Feature Pack 2時，才能使用此AEM Screens功能。 若要存取此Feature Pack，您必須聯絡Adobe支援並要求存取權。 擁有權限後，您就可以從「封裝共用」下載。

## 簡介 {#introduction}

AEM Screens架構類似傳統AEM Sites架構。 內容是在AEM製作例項上製作，然後轉送複製到多個發佈例項。 AEM Screens裝置現在可以透過負載平衡器連線至AEM發佈伺服器陣列。 可新增多個AEM發佈例項，以繼續調整發佈伺服器陣列。

*例如*,AEM Screens內容作者在製作系統上針對特定裝置發出命令，該裝置設定為與發佈伺服器陣列互動，或AEM Screens內容作者會取得關於已設定為與發佈伺服器陣列互動之裝置的資訊。

下圖說明製作和發佈環境。

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## 架構設計{#architectural-design}

有五個體系結構元件，可促進此解決方案：

* ***將內*** 容從作者複製到發佈以供裝置顯示

* ****** 將二進位內容從發佈（從裝置接收）複製到製作
* ****** 透過特定REST API從作者傳送命令以發佈
* ****** 在發佈實例之間傳送消息，以同步設備資訊更新和命令
* ****** 由發佈例項作者進行輪詢，透過特定REST API取得裝置資訊

### 內容和配置的複製（轉發）{#replication-forward-of-content-and-configurations}

標準複製代理用於複製螢幕通道內容、位置配置和設備配置。 這可讓作者更新管道的內容，並選擇性地在發佈管道更新之前，先執行某種核准工作流程。 需要為發佈伺服器陣列中的每個發佈執行個體建立復寫代理。

下圖說明了複製過程：

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>需要為發佈伺服器陣列中的每個發佈執行個體建立復寫代理。

### 螢幕複製代理和命令{#screens-replication-agents-and-commands}

會建立自訂Screens特定的復寫代理，以將命令從Author例項傳送至AEM Screens裝置。 AEM Publish執行個體可做為中間工具，將這些命令轉送至裝置。

這可讓作者繼續管理裝置，例如傳送裝置更新，並從製作環境中擷取螢幕擷取畫面。 AEM Screens復寫代理具有自定義傳輸配置，如標準複製代理。

### 發佈實例之間的消息傳遞{#messaging-between-publish-instances}

在許多情況下，命令只能一次傳送至裝置。 不過，在負載平衡的發佈架構中，未知裝置要連線至哪個發佈執行個體。

因此，製作例項會傳送訊息至所有發佈例項。 但是，只應將一個消息中繼到設備。 為確保傳訊正確，發佈執行個體之間必須進行一些通訊。 這是使用&#x200B;*Apache ActiveMQ Artemis*&#x200B;來實現的。 每個發佈執行個體都會放置在鬆散耦合的拓撲中，使用Oak型Sling探索服務，並設定ActiveMQ，讓每個發佈執行個體能通訊並建立單一訊息佇列。 Screens裝置會透過負載平衡器輪詢發佈伺服器陣列，並從佇列頂端擷取命令。

### 反向複製{#reverse-replication}

在許多情況下，在執行命令後，Screens裝置會傳送某種回應至Author例項。 為了達到此AEM ***使用反向復寫***。

* 為每個發佈實例建立反向複製代理，類似於標準複製代理和螢幕複製代理。
* 工作流程啟動器設定會監聽發佈執行個體上修改的節點，並進而觸發工作流程，將裝置的回應置於發佈執行個體的寄件匣中。
* 此上下文中的反向複製僅用於設備提供的二進位資料（如日誌檔案和螢幕截圖）。 非二進位資料由輪詢檢索。
* 從AEM製作例項輪詢的反向復寫會擷取回應並儲存至製作例項。

### 輪詢發佈實例{#polling-of-publish-instances}

製作例項必須能夠輪詢裝置以取得心率，並了解已連線裝置的健康狀態。

偵測負載平衡器並路由至發佈執行個體的裝置。 接著，發佈執行個體會透過在&#x200B;**api/screens-dcc/devices/static**&#x200B;中針對所有作用中裝置提供的發佈API，以及在單一裝置上透過&#x200B;**api/screens-dcc/devices/&lt;device_id>/status.json**&#x200B;公開裝置狀態。

製作例項會輪詢所有發佈例項，並將裝置狀態回應合併為單一狀態。 在作者上輪詢的排程作業為`com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob`，且可根據cron運算式進行設定。

## 註冊 {#registration}

註冊仍源自於AEM製作例項。 AEM Screens裝置會指向製作執行個體，且註冊已完成。

在製作環境上註冊裝置後，裝置設定和通道/排程指派會複製至AEM發佈執行個體。 接著會更新AEM Screens裝置設定，以指向AEM發佈伺服器陣列前面的負載平衡器。 這是一次性設定，當Screens裝置成功連線至發佈環境後，就可繼續接收來自製作環境的命令，而且不需要將Screens裝置直接連線至製作環境。

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### 後續步驟{#the-next-steps}

了解AEM Screens中作者和發佈設定的架構設計後，如需詳細資訊，請參閱[為AEM Screens設定作者和發佈](author-and-publish.md) 。

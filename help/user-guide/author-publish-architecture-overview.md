---
title: 製作與發佈架構概覽
description: AEM Screens架構類似於傳統AEM Sites架構。 內容是在AEM製作執行個體上製作，然後轉送復寫到多個發佈執行個體。
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 0%

---

# 製作與發佈架構概覽 {#author-and-publish-architectural-overview}

本頁面主要說明下列主題：

* **發佈伺服器簡介**
* **架構概觀**
* **註冊程式**

## 先決條件 {#prerequisites}

開始使用作者伺服器和發佈伺服器之前，您應具備以下預先知識：

* **AEM拓撲**
* **建立和管理AEM Screens專案**
* **裝置註冊程式**

>[!NOTE]
>
>此AEM Screens功能僅在您已安裝AEM 6.4 Screens Feature Pack 2時可用。 若要存取此Feature Pack，請聯絡Adobe支援並請求存取權。 取得許可權後，請從「封裝共用」下載。

## 簡介 {#introduction}

AEM Screens架構類似於傳統AEM Sites架構。 內容是在AEM製作執行個體上製作，然後轉送復寫到多個發佈執行個體。 AEM Screens上的裝置現在可以透過負載平衡器連線至AEM發佈陣列。 可以新增多個AEM發佈執行個體，以繼續擴充發佈陣列。

*例如*，AEM Screens內容作者會在特定裝置的編寫系統上發出命令。 該裝置已設定為與發佈伺服器陣列互動。 或者，與AEM Screens內容作者互動，後者取得已設定為與發佈伺服器陣列互動之裝置的相關資訊。

下圖說明作者環境和發佈環境。

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## 架構設計 {#architectural-design}

有五個架構元件有助於此解決方案：

* ***正在將內容***&#x200B;從作者復寫到發佈，以供裝置顯示

* ***反向***&#x200B;將二進位內容從發佈環境（從裝置接收）複製到編寫環境。
* ***從作者傳送***&#x200B;命令，以透過特定REST API發佈。
* ***在發佈執行個體之間傳訊***，以同步處理裝置資訊更新和命令。
* ***由發佈執行個體的作者輪詢***，以透過特定REST API取得裝置資訊。

### 內容和設定的復寫（轉送） {#replication-forward-of-content-and-configurations}

標準復寫代理程式用於復寫AEM Screens通道內容、位置設定和裝置設定。 此功能可讓作者更新管道內容，並在發佈管道更新前，選擇性地透過某種核准工作流程。 必須為發佈伺服器陣列中的每個發佈執行個體建立復寫代理程式。

下圖說明了復製程式：

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>必須為發佈伺服器陣列中的每個發佈執行個體建立復寫代理程式。

### Screens復寫代理和命令 {#screens-replication-agents-and-commands}

自訂Screens專用的復寫代理程式是用來從Author例項傳送命令至AEM Screens裝置。 AEM發佈執行個體可作為中介，將這些命令轉送至裝置。

此工作流程可讓作者繼續管理裝置，例如傳送裝置更新，以及從作者環境擷取熒幕擷圖。 AEM Screens復寫代理程式具有自訂傳輸設定，例如標準復寫代理。

### 發佈執行個體之間的傳訊 {#messaging-between-publish-instances}

通常命令只適用於傳送至裝置。 然而，在負載平衡的發佈架構中，裝置連線的發佈執行個體不明。

因此，作者執行個體會將訊息傳送給所有發佈執行個體。 不過，之後只應將單一訊息轉送至裝置。 為確保傳訊功能正確無誤，發佈執行個體之間必須通訊。 此通訊是使用&#x200B;*Apache ActiveMQ Artemis*&#x200B;達成。 每個發佈執行個體都會使用Oak型Sling探索服務，放置於鬆散耦合的拓撲中。 ActiveMQ的設定方式讓每個發佈執行個體都可以通訊並建立單一訊息佇列。 AEM Screens裝置透過負載平衡器輪詢AEM發佈陣列，並從佇列頂端挑選命令。

### 反向複寫 {#reverse-replication}

通常，在命令之後，會從Screens裝置將某種回應轉送至作者執行個體。 若要實現此AEM ***已使用反向復寫***。

* 為每個發佈執行個體建立反向復寫代理，類似於標準復寫代理和AEM Screens復寫代理。
* 工作流程啟動器設定會監聽在AEM發佈執行個體上修改的節點，然後觸發工作流程將裝置的回應放入AEM發佈執行個體的寄件匣中。
* 此內容中的反向復寫僅適用於裝置提供的二進位資料（例如記錄檔和熒幕擷取畫面）。 擷取非二進位資料的輪詢。
* 從AEM製作執行個體反向復寫輪詢會擷取回應，並將其儲存至製作執行個體。

### 輪詢發佈執行個體 {#polling-of-publish-instances}

製作執行個體必須能夠輪詢動裝置，才能取得心率並瞭解連線裝置的健康狀態。

裝置ping負載平衡器並路由至發佈執行個體。 之後，AEM發佈執行個體會透過為所有使用中裝置提供的@ **api/screens-dcc/devices/static**&#x200B;發佈應用程式開發介面，以及為單一裝置提供的&#x200B;**api/screens-dcc/devices/&lt;device_id>/status.json**，來公開裝置的狀態。

製作執行個體輪詢所有發佈執行個體，並將裝置狀態回應合併為單一狀態。 在作者上輪詢的排程工作是`com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob`，可以根據cron運算式進行設定。

## 註冊 {#registration}

註冊作業會持續源自AEM作者例項。 AEM Screens裝置指向作者例項且註冊完成。

在AEM製作環境中註冊裝置後，裝置設定和管道/排程指派會複製到AEM發佈執行個體。 AEM Screens裝置設定接著會更新，以指向AEM發佈伺服器陣列前的負載平衡器。 此安排旨在一次性設定。 Screens裝置成功連線至發佈環境後，即可繼續接收源自製作環境的命令。 應該不需要直接將AEM Screens裝置連線到AEM作者環境。

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### 後續步驟 {#the-next-steps}

當您瞭解AEM Screens中作者與發佈設定的架構設計時，如需詳細資訊，請參閱[設定AEM Screens的作者與發佈](author-and-publish.md)。

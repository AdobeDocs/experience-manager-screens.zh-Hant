---
title: 作者和發佈體系結構概述
seo-title: Author and Publish Architectural Overview
description: AEM Screens的建築與AEM Sites的傳統建築很相似。 內容在作者實例AEM上創作，然後轉發複製到多個發佈實例。 按照本頁瞭解有關作者的詳細資訊並發佈體系結構概述。
seo-description: AEM Screens architecture resembles a traditional AEM Sites architecture. Content is authored on an AEM author instance and then forward-replicated to multiple publish instances. Follow this page to learn more on author and publish architectural overview.
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 0%

---

# 作者和發佈體系結構概述 {#author-and-publish-architectural-overview}

此頁突出顯示以下主題：

* **發佈伺服器簡介**
* **架構概述**
* **註冊流程**

## 必備條件 {#prerequisites}

在開始使用作者和發佈伺服器之前，您應先瞭解：

* **拓AEM撲**
* **建立和管理AEM Screens項目**
* **設備註冊過程**

>[!NOTE]
>
>只有安裝了6.4螢幕功能包2AEM時，此AEM Screens功能才可用。 要訪問此功能包，必須聯繫Adobe支援並請求訪問。 擁有權限後，您可以從包共用下載它。

## 簡介 {#introduction}

AEM Screens的建築與AEM Sites的傳統建築很相似。 內容在作者實例AEM上創作，然後轉發複製到多個發佈實例。 AEM Screens設備現在可以通過負AEM載平衡器連接到發佈場。 可以添AEM加多個發佈實例以繼續擴展發佈場。

*例如*,AEM Screens內容作者在創作系統上為配置為與發佈場交互的特定設備發出命令，或者AEM Screens內容作者獲取關於配置為與發佈場交互的設備的資訊。

下圖說明了作者和發佈環境。

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## 建築設計 {#architectural-design}

有五個體系結構元件，可促進此解決方案：

* ***複製內容*** 從作者發佈到按設備顯示

* ***反向*** 將二進位內容從發佈（從設備接收）複製到作者
* ***發送*** 通過特定REST API發佈的命令
* ***消息*** 在發佈實例之間同步設備資訊更新和命令
* ***輪詢*** 由發佈實例的作者通過特定的REST API獲取設備資訊

### 內容和配置的複製（轉發）  {#replication-forward-of-content-and-configurations}

標準複製代理用於複製螢幕通道內容、位置配置和設備配置。 這允許作者在發佈渠道更新之前更新渠道內容，並可選地通過某種審批工作流。 需要為發佈場中的每個發佈實例建立複製代理。

下圖說明了複製過程：

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>需要為發佈場中的每個發佈實例建立複製代理。

### 螢幕複製代理和命令  {#screens-replication-agents-and-commands}

建立特定於自定義螢幕的複製代理，以將命令從作者實例發送到AEM Screens設備。 AEM發佈實例用作將這些命令轉發到設備的中介。

這允許作者繼續管理設備，例如，發送設備更新並從作者環境拍攝螢幕截圖。 AEM Screens複製代理具有自定義傳輸配置，如標準複製代理。

### 發佈實例之間的消息傳遞  {#messaging-between-publish-instances}

在許多情況下，命令只能一次發送到設備。 但是，在負載平衡的發佈體系結構中，設備正在連接到哪個發佈實例是未知的。

因此，作者實例將消息發送到所有發佈實例。 但是，只應將一條消息中繼到設備。 為了確保消息傳遞正確，必須在發佈實例之間進行一些通信。 這是通過 *Apache ActiveMQ Artemis*。 每個發佈實例都使用基於Oak的Sling發現服務放置在松耦合的拓撲中，並配置ActiveMQ，以便每個發佈實例能夠通信並建立單個消息隊列。 「螢幕」設備通過負載平衡器輪詢發佈場，並從隊列頂部提取命令。

### 反向複製 {#reverse-replication}

在許多情況下，在執行命令後，Screens設備會有某種響應被轉發到Author實例。 為了達到這AEM個 ***反向複製*** 的子菜單。

* 為每個發佈實例建立一個反向複製代理，類似於標準複製代理和螢幕複製代理。
* 工作流啟動程式配置偵聽在發佈實例上修改的節點，然後觸發工作流將設備的響應放在發佈實例的發件箱中。
* 在此上下文中的反向複製僅用於設備提供的二進位資料（例如，日誌檔案和螢幕截圖）。 通過輪詢來檢索非二進位資料。
* 從作者實例輪詢AEM的反向複製將檢索響應並將其保存到作者實例。

### 發佈實例的輪詢  {#polling-of-publish-instances}

作者實例需要能夠輪詢設備以獲取心跳並瞭解已連接設備的運行狀況。

設備ping負載平衡器並被路由到發佈實例。 然後，發佈實例通過提供@的發佈API公開設備的狀態 **api/screens dcc/devices/static** 用於所有活動設備和 **api/screens/dcc/devices/&lt;device_id>/status.json** 單個設備。

作者實例輪詢所有發佈實例，並將設備狀態響應合併為單個狀態。 輪詢作者的計畫作業是 `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` 可以基於cron表達式進行配置。

## 註冊 {#registration}

註冊繼續源於提交AEM人實例。 AEM Screens設備指向作者實例並完成註冊。

在作者環境上註冊設備後，設備配置和通道/計劃分配將複製到發AEM布實例。 然後，將更新AEM Screens設備配置，以指向發佈場前面的負AEM載平衡器。 這是一次性設定，一旦螢幕設備成功連接到發佈環境，它就可以繼續接收來自作者環境的命令，並且永遠不需要將螢幕設備直接連接到作者環境。

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### 後續步驟 {#the-next-steps}

一旦您瞭解作者的建築設計並在AEM Screens發佈設定，請參閱 [為AEM Screens配置作者和發佈](author-and-publish.md) 的子菜單。

---
title: 從ContentSync過渡到SmartSync
seo-title: Transitioning from ContentSync to SmartSync
description: 請按照此頁瞭解SmartSync功能以及如何從ContentSync過渡到SmartSync。
seo-description: Follow this page to learn about SmartSync feature and how you can transition from ContentSync to SmartSync.
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b8d0c089-af79-403e-870f-fb46b66fecd3
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 1%

---

# 從ContentSync過渡到SmartSync {#transitioning-from-contentsync-to-smartsync}

本節概述SmartSync功能，以及它如何將伺服器負載/儲存和網路流量降至最低以降低成本。

## 概觀 {#overview}

SmartSync是AEM Screens使用的最新機制。 它替代了當前用於快取離線通道並將它們傳送到播放器的方法。

它在伺服器端和客戶端都執行。

**在伺服器端**:

* 頻道內容（包括資產）快取在 */var/contentsync*。
* 通過描述用於顯示的可用內容的清單向玩家公開快取。

**客戶端**:

* 播放器根據上面生成的清單更新其內容。

### 使用SmartSync的好處 {#benefits-of-using-smartsync}

SmartSync功能為您的AEM Screens項目提供了許多好處。 它允許

* 大幅減少網路流量和伺服器端儲存需求
* 僅當資產丟失或更改時，Player才智慧地下載資產
* 伺服器端和客戶端儲存優化

>[!NOTE]
>
>Adobe強烈建議將SmartSync用於AEM Screens項目。

## 從ContentSync遷移到SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>如果已安裝AEM6.3功能包5和AEM6.4功能包3，則可以啟用SmartSync來使用資產，以提高磁碟空間利用率。 要啟用SmartSync，請按照下面的部分從ContentSync過渡到SmartSync，從而啟用SmartSync。
>
>SmartSync可用於支援伺服器AEM6.4.3 FP3的Screens Player。
>
>請參閱 [AEM Screens播放器下載](https://download.macromedia.com/screens/) 下載最新播放器。 下表說明了每個平台所需的最低播放器版本：

| **Platform** | **支援的最低播放器版本** |
|---|---|
| Android | 3.3.72 |
| Chrome作業系統 | 1.0.136 |
| Windows | 1.0.136 |

按照以下步驟從ContentSync過渡到SmartSync:

1. 從ContentSync遷移到SmartSync需要先清除ContentSync快取，然後再激活SmartSync。

   使用連結從實例導航到ContentSync控制台 ***https://localhost:4502/libs/cq/contentsync/content/console.html*** 按一下 **清除快取**，如下圖所示：

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >首次使用SmartSync之前必須清除所有內容快取。

1. 導航到 **Adobe Experience ManagerWeb控制台配置** 通AEM過實例 — >錘表徵圖 —  **操作** —> **Web控制台**。

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Adobe Experience ManagerWeb控制台配置** 的上界。 搜索 *offlinecontentservice（離線連接服務）*。

   搜索 **螢幕離線內容服務** 屬性，按 **命令+F** 為 **Mac** 和 **控制項+F** 為 **窗口**。

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. 按一下 **保存** 啟用 **螢幕離線內容服務** 屬性，因此將SmartSync用於AEM Screens。
1. 啟用SmartSync後，必須導航到項目並按一下 **更新離線內容** *（從操作欄）,* 如下圖所示。

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)

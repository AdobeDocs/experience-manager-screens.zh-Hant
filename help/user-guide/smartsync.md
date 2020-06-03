---
title: 從ContentSync轉換到SmartSync
seo-title: 從ContentSync轉換到SmartSync
description: 請依照本頁瞭解SmartSync功能，以及如何從ContentSync轉換到SmartSync。
seo-description: 請依照本頁瞭解SmartSync功能，以及如何從ContentSync轉換到SmartSync。
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
translation-type: tm+mt
source-git-commit: 112aa2a89578243bad49e61839d781e0f29893b4
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 1%

---


# 從ContentSync轉換到SmartSync {#transitioning-from-contentsync-to-smartsync}

本節概述了SmartSync功能，以及它如何最大限度地減少伺服器負載／儲存和網路流量以降低成本。

## 概覽 {#overview}

SmartSync是AEM Screens使用的最新機制。 它可取代目前用來快取離線頻道並將它們傳送至播放器的方法。

它同時在伺服器端和用戶端執行。

**在伺服器端**:

* 頻道的內容（包括資產）會快取至 */var/contentsync*。
* 快取通過描述顯示器的可用內容的清單公開給播放器。

**在用戶端**:

* 播放器會根據上述產生的資訊清單更新其內容。

### 使用SmartSync的優點 {#benefits-of-using-smartsync}

SmartSync功能為您的AEM Screens專案提供許多優點。 它允許

* 大幅降低網路流量和伺服器端儲存需求
* Player只會在資產遺失或變更時智慧下載資產
* 伺服器端和用戶端儲存空間最佳化

>[!NOTE]
>
>Adobe強烈建議您針對AEM Screens專案使用SmartSync。

## 從ContentSync遷移到SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>如果您已安裝AEM 6.3 Feature Pack 5和AEM 6.4 Feature Pack 3，則可以啟用SmartSync for assets，以改善磁碟空間使用。 要啟用SmartSync，請按照以下章節從ContentSync轉換到SmartSync，從而啟用SmartSync。
>
>SmartSync適用於支援的伺服器AEM 6.4.3 FP3的Screens Player。
>
>請參閱「 [AEM Screens Player Downloads](https://download.macromedia.com/screens/) 」（AEM畫面播放器下載）以下載最新的播放器。 下表說明每個平台所需的最低播放器版本：

| **平台** | **最低支援播放器版本** |
|---|---|
| Android | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

請依照下列步驟，從ContentSync轉換至SmartSync:

1. 從ContentSync遷移到SmartSync需要在激活SmartSync之前清除ContentSync快取。

   使用連結https://localhost:4502/libs/cq/contentsync/content/console.html從您的例項導覽至ContentSync主控台 ****** ，然後按一下 **清除快取**，如下圖所示：

   ![clear_contensync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >首次使用SmartSync之前，必須清除所有內容快取。

1. 透過 **AEM例項** —> hammer圖示—> **Operations** —> **Web Console導覽至Adobe Experience Manager Web Console Configuration**。

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Adobe Experience Manager Web Console設定**開啟。 搜尋offlinecontentservice **。

   若要搜尋 **Screens Offline Content** Service **，請按** Command+F **(尋找** Mac)和 **F(F)****** Control+F（針對WindowsWindows）屬性。

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. 按一 **下「儲存** 」以啟用「畫面 **** 離線內容服務」屬性，因此可針對AEM畫面使用SmartSync。
1. 啟用SmartSync後，您必須導覽至您的專案，然後按一下「 **Update Offline Content***（從動作列）* 」，如下圖所示。

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)
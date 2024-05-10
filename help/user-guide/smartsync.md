---
title: 從ContentSync轉換為SmartSync
description: 深入瞭解該SmartSync功能，以及如何從ContentSync轉換至SmartSync。
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b8d0c089-af79-403e-870f-fb46b66fecd3
source-git-commit: 6b4fc934c31640168528fa3e72cf634773f4f8e6
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# 從ContentSync轉換為SmartSync {#transitioning-from-contentsync-to-smartsync}

本節提供SmartSync功能的概觀，並說明如何最小化伺服器負載/儲存及網路流量，以降低成本。

## 概觀 {#overview}

SmartSync是AEM Screens使用的最新機制。 這是目前快取離線頻道，並將這些頻道傳送給播放器的方法的替代方案。

它會在伺服器端和使用者端執行。

**在伺服器端**

* 管道的內容（包括資產）會快取在 *`/var/contentsync`*.
* 快取會透過描述顯示可用內容的資訊清單向播放器公開。

**在使用者端**

* 播放器會根據上述產生的資訊清單更新其內容。

### 使用SmartSync的優點 {#benefits-of-using-smartsync}

SmartSync功能可為您的AEM Screens專案提供下列幾項優點：

* 大幅降低網路流量與伺服器端儲存需求。
* 只有在資產遺失或變更時，播放器才會智慧地下載資產。
* 伺服器端和使用者端儲存最佳化。

>[!NOTE]
>
>Adobe強烈建議對AEM Screens專案使用SmartSync。

## 從ContentSync移轉至SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>如果您已安裝AEM 6.3 Feature Pack 5和AEM 6.4 Feature Pack 3，您可以啟用資產的SmartSync來改善磁碟空間使用量。 若要啟用SmartSync，請遵循以下章節，從ContentSync轉換到SmartSync，進而啟用SmartSync。
>
>SmartSync適用於支援伺服器AEM 6.4.3 FP3的Screens Player。
>
>請參閱 [AEM Screens播放器下載](https://download.macromedia.com/screens/) 以下載最新的播放器。 下表說明每個平台所需的最低播放器版本：

| **Platform** | **最低支援的播放器版本** |
|---|---|
| Android™ | 3.3.72 |
| Chrome作業系統 | 1.0.136 |
| Windows | 1.0.136 |

請依照下列步驟，從ContentSync轉換為SmartSync：

1. 從ContentSync移轉至SmartSync需要先清除ContentSync快取，才能啟用SmartSync。

   使用連結從您的執行個體導覽至ContentSync主控台 ***https://localhost:4502/libs/cq/contentsync/content/console.html*** 並按一下 **清除快取**，如下圖所示：

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >第一次使用SmartSync前，必須先清除所有內容快取。

1. 瀏覽至 **Adobe Experience Manager Web主控台設定** 透過AEM執行個體> hammer圖示> **作業** > **網頁主控台**.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Adobe Experience Manager Web主控台設定** 隨即開啟。 搜尋 *offlinecontentservice*.

   若要搜尋 **Screens離線內容服務** 屬性，按下 **Command+F** 的 **Mac**、和 **Control+F** 的 **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. 按一下 **儲存** 以啟用 **Screens離線內容服務** 屬性，因此請針對AEM Screens使用SmartSync。
1. 啟用SmartSync後，請瀏覽至您的專案並按一下 **更新離線內容** *（從動作列），* 如下圖所示。

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)

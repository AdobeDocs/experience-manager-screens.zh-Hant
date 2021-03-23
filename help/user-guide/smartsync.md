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
feature: 管理畫面
role: 管理員
level: 中級
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 1%

---


# 從ContentSync轉換到SmartSync {#transitioning-from-contentsync-to-smartsync}

本節概述了SmartSync功能，以及它如何最大限度地減少伺服器負載／儲存和網路流量以降低成本。

## 概覽 {#overview}

SmartSync是AEM Screens最新使用的機制。 它可取代目前用來快取離線頻道並將它們傳送至播放器的方法。

它同時在伺服器端和用戶端執行。

**在伺服器端**:

* 頻道的內容（包括資產）會快取在&#x200B;*/var/contentsync*&#x200B;中。
* 快取通過描述顯示器的可用內容的清單公開給播放器。

**在用戶端**:

* 播放器會根據上述產生的資訊清單更新其內容。

### 使用SmartSync的優點{#benefits-of-using-smartsync}

SmartSync功能為您的AEM Screens項目提供了許多好處。 它允許

* 大幅降低網路流量和伺服器端儲存需求
* Player只會在資產遺失或變更時智慧下載資產
* 伺服器端和用戶端儲存空間最佳化

>[!NOTE]
>
>Adobe強烈建議對AEM Screens項目使用SmartSync。

## 從ContentSync遷移到SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>如果您已安裝AEM6.3 Feature Pack 5和AEM 6.4 Feature Pack 3，則可以啟用SmartSync for assets以改善磁碟空間使用。 要啟用SmartSync，請按照以下章節從ContentSync轉換到SmartSync，從而啟用SmartSync。
>
>SmartSync適用於Screens Player，其支援的伺服器為AEM6.4.3 FP3。
>
>請參閱[AEM Screens播放器下載](https://download.macromedia.com/screens/)以下載最新的播放器。 下表說明每個平台所需的最低播放器版本：

| **平台** | **最低支援播放器版本** |
|---|---|
| Android | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

請依照下列步驟，從ContentSync轉換至SmartSync:

1. 從ContentSync遷移到SmartSync需要在激活SmartSync之前清除ContentSync快取。

   使用連結&#x200B;***https://localhost:4502/libs/cq/contentsync/content/console.html***&#x200B;從您的例項導覽至ContentSync主控台，然後按一下「清除快取」，如下圖所示：****

   ![clear_contensync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >首次使用SmartSync之前，必須清除所有內容快取。

1. 導航至&#x200B;**Adobe Experience ManagerWeb控制台配置**(通過實例AEM—>槌子表徵圖—> **操作** —> **Web控制台**)。

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Adobe Experience ManagerWeb控制台** 配置開啟。搜索&#x200B;*offlinecontentservice*。

   要搜索&#x200B;**螢幕離線內容服務**&#x200B;屬性，請按&#x200B;**Command+F**&#x200B;表示&#x200B;**Mac**，按&#x200B;**Control+F**&#x200B;表示&#x200B;**Windows**。

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. 按一下&#x200B;**保存**&#x200B;以啟用&#x200B;**螢幕離線內容服務**&#x200B;屬性，因此使用SmartSync forAEM Screens。
1. 啟用SmartSync後，必須導航到項目，然後按一下&#x200B;**更新離線內容** *（從操作欄）,* ，如下圖所示。

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)
---
title: 從ContentSync過渡到SmartSync
seo-title: 從ContentSync過渡到SmartSync
description: 請按照本頁了解SmartSync功能，以及如何從ContentSync過渡到SmartSync。
seo-description: 請按照本頁了解SmartSync功能，以及如何從ContentSync過渡到SmartSync。
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
feature: 管理畫面
role: Admin
level: Intermediate
exl-id: b8d0c089-af79-403e-870f-fb46b66fecd3
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 1%

---

# 從ContentSync過渡到SmartSync {#transitioning-from-contentsync-to-smartsync}

本節概述了SmartSync功能，以及它如何最大限度地減少伺服器負載/儲存和網路流量以降低成本。

## 概覽 {#overview}

SmartSync是AEM Screens使用的最新機制。 取代目前快取離線頻道並將頻道傳送至播放器的方法。

會同時在伺服器端和用戶端執行。

**在伺服器端**:

* 管道的內容（包括資產）會快取至&#x200B;*/var/contentsync*。
* 快取會透過描述顯示可用內容的資訊清單公開給播放器。

**在用戶端**:

* 播放器會根據上述產生的資訊清單更新其內容。

### 使用SmartSync的優點 {#benefits-of-using-smartsync}

SmartSync功能為您的AEM Screens專案提供許多優點。 它允許

* 大幅減少網路流量和伺服器端儲存需求
* 播放器只會在資產遺失或變更時聰明地下載資產
* 伺服器端和用戶端儲存最佳化

>[!NOTE]
>
>Adobe強烈建議將SmartSync用於AEM Screens專案。

## 從ContentSync遷移到SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>如果您已安裝AEM 6.3 Feature Pack 5和AEM 6.4 Feature Pack 3，則可以啟用資產的SmartSync以改善磁碟空間使用。 要啟用SmartSync，請按照下面的部分從ContentSync轉變到SmartSync，從而啟用SmartSync。
>
>SmartSync適用於支援伺服器AEM 6.4.3 FP3的Screens Player。
>
>請參考[AEM Screens Player下載](https://download.macromedia.com/screens/)以下載最新播放器。 下表說明每個平台所需的最低播放器版本：

| **平台** | **最低支援播放器版本** |
|---|---|
| Android | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

請按照以下步驟從ContentSync過渡到SmartSync:

1. 從ContentSync遷移到SmartSync需要先清除ContentSync快取，然後才能激活SmartSync。

   使用連結&#x200B;***https://localhost:4502/libs/cq/contentsync/content/console.html***&#x200B;從您的執行個體導覽至ContentSync主控台，然後按一下&#x200B;**清除快取**，如下圖所示：

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >首次使用SmartSync之前，必須清除所有內容快取。

1. 透過AEM例項 — >槌子圖示 — > **Operations** —> **Web主控台**&#x200B;導覽至&#x200B;**Adobe Experience Manager Web主控台設定**。

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Adobe Experience Manager Web主控台設** 定隨即開啟。搜尋&#x200B;*offlinecontentservice*。

   要搜索&#x200B;**Screens Offline Content Service**&#x200B;屬性，請按&#x200B;**Mac**&#x200B;的&#x200B;**Command+F**&#x200B;和&#x200B;**Control+F**&#x200B;以&#x200B;**Windows**。

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. 按一下&#x200B;**Save**&#x200B;以啟用&#x200B;**Screens Offline Content Services**&#x200B;屬性，因此使用SmartSync for AEM Screens。
1. 啟用SmartSync後，必須導航到您的項目，然後按一下&#x200B;**更新離線內容** *（從操作欄）,*，如下圖所示。

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)

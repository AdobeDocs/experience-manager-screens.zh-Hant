---
title: 頻道層級大量影像播放持續時間
description: 瞭解如何在AEM Screens中編輯特定影像元件的播放持續時間。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 95aa761a-1449-4e18-8115-3b151036dc54
TQID: https://experienceleague.adobe.com/6Cq6n8lfTfRC685rE4jWmnAQDPLsDJ4ptNTNjt-qmHc
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 387
ht-degree: 1%

---

# 頻道層級大量影像播放持續時間 {#channel-level-bulk-image-playback-duration}

## 概觀 {#overview}

>[!IMPORTANT]
>此內容對AEM內部部署/AMS （AEM 6.5LTS和AEM 6.5）有效。 如需AEM as a Cloud Service Screens內容，請參閱[AEM as a Cloud Service指南](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

當您建立序列色版並在其中新增影像時，根據預設，所有影像都會採用色版等級設定中定義的播放持續時間。 任何個別影像仍可覆寫預設值，並具有不同的播放持續時間。 此功能可透過編輯特定影像元件的播放持續時間來完成。

### 先決條件 {#prerequisites}

在開始實作此功能之前，請確定您已設定專案作為開始實作此功能的先決條件。 例如，

1. 建立AEM Screens專案範例，**ChannelLevelPlayback**。

1. 在&#x200B;**Channels**&#x200B;資料夾下，將順序頻道建立為&#x200B;**PlaybackChannel**。

1. 將內容新增至&#x200B;**PlaybackChannel**。

## 編輯頻道層級影像播放持續時間指派 {#editing-channel-level-image-playback-duration-assignment}

以下章節說明如何在AEM Screens頻道中編輯內容的播放持續時間。

### 更新頻道中影像的播放持續時間 {#updating-the-playback-duration-for-images-in-a-channel}

請依照下列步驟瞭解如何更新頻道層級影像播放期間指派：

1. 導覽至順序頻道&#x200B;**PlaybackChannel**。

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. 按一下動作列中的&#x200B;**編輯**。

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. 在色版編輯器中新增兩個或多個影像，如下圖所示。

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. 按一下色版中的所有影像，然後按一下左上方的扳手圖示（如下圖所示），即可開啟「色版層級設定」對話方塊。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **頁面**&#x200B;對話方塊開啟。

   >[!NOTE]
   >根據預設，色版中的影像會設為8秒的播放期間。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   編輯&#x200B;**持續時間**，從8000 （毫秒）到3000 （毫秒），即3秒。 按一下&#x200B;**頁面**&#x200B;對話方塊右上方的核取記號，即可儲存變更。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 檢視結果 {#viewing-the-result}

在您更新頻道播放持續時間（在此範例中是三個影像）後，請注意影像現在會播放3秒而非8秒（預設值）。

![channel_preview](assets/channel_preview.gif)


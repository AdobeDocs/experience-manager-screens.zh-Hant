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
source-git-commit: 8a914d4b0237c327b7954c936c84a2c1aa719603
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 1%

---

# 頻道層級大量影像播放持續時間 {#channel-level-bulk-image-playback-duration}

## 概觀 {#overview}

當您建立序列色版並在其中新增影像時，根據預設，所有影像都會採用色版等級設定中定義的播放持續時間。 任何個別影像仍可覆寫預設值，並具有不同的播放持續時間。 此功能可透過編輯特定影像元件的播放持續時間來完成。

### 先決條件 {#prerequisites}

在開始實作此功能之前，請確定您已設定專案作為開始實作此功能的先決條件。 例如，

1. 建立AEM Screens專案範例， **ChannelLevelPlayback**.

1. 建立順序頻道為 **PlaybackChannel** 在 **頻道** 資料夾。

1. 新增內容至 **PlaybackChannel**.

## 編輯頻道層級影像播放持續時間指派 {#editing-channel-level-image-playback-duration-assignment}

以下章節說明如何在AEM Screens頻道中編輯內容的播放持續時間。

### 更新頻道中影像的播放持續時間 {#updating-the-playback-duration-for-images-in-a-channel}

請依照下列步驟瞭解如何更新頻道層級影像播放期間指派：

1. 導覽至順序頻道 **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. 按一下 **編輯** 從動作列移除。

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. 在色版編輯器中新增兩個或多個影像，如下圖所示。

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. 按一下色版中的所有影像，然後按一下左上方的扳手圖示（如下圖所示），即可開啟「色版層級設定」對話方塊。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. 此 **頁面** 對話方塊開啟。

   >[!NOTE]
   >根據預設，色版中的影像會設為8秒的播放期間。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   編輯 **持續時間** 從8000 （毫秒）到3000 （毫秒），即3秒。 按一下右上方的勾號 **頁面** 對話方塊，以便儲存變更。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 檢視結果 {#viewing-the-result}

在您更新頻道播放持續時間（在此範例中是三個影像）後，請注意影像現在會播放3秒而非8秒（預設值）。

![channel_preview](assets/channel_preview.gif)

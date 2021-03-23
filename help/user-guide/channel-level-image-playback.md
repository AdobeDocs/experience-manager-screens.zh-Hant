---
title: 頻道層級大量影像播放持續時間
seo-title: 頻道層級大量影像播放持續時間
description: 本頁說明如何編輯特定影像元件的播放持續時間。
seo-description: 本頁說明如何編輯特定影像元件的播放持續時間。
uuid: 4ebb00a9-b04d-4dfe-9fee-2348a2e2c142
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: df3cf999-0c8d-4754-8b58-5c6ced2c8ca5
docset: aem65
feature: 製作畫面
role: 管理員、開發人員
level: 中級
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 1%

---


# 頻道層級大量影像播放持續時間{#channel-level-bulk-image-playback-duration}

## 概覽 {#overview}

在您建立序列頻道並新增影像後，依預設，所有影像都會採用頻道層級設定中定義的播放持續時間。 任何個別影像仍可覆寫預設值，並有不同的播放持續時間，這是透過編輯特定影像元件的播放持續時間來完成的。

### 必備條件 {#prerequisites}

開始實作此功能之前，請確定您已將專案設定為開始實作此功能的先決條件。 例如，

1. 建立AEM Screens專案範例&#x200B;**ChannelLevelPlayback**。

1. 在&#x200B;**Channels**&#x200B;資料夾下，建立序列頻道為&#x200B;**PlaybackChannel**。

1. 將內容新增至&#x200B;**PlaybackChannel**。

## 編輯頻道層級影像播放持續時間指派{#editing-channel-level-image-playback-duration-assignment}

下節說明如何編輯AEM Screens頻道內容的播放持續時間。

### 更新頻道{#updating-the-playback-duration-for-images-in-a-channel}中影像的播放時長

請依照下列步驟瞭解如何更新頻道層級影像播放持續時間指派：

1. 導覽至序列頻道&#x200B;**PlaybackChannel**。

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. 按一下操作欄中的&#x200B;**編輯**&#x200B;以開啟編輯器。

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. 在色版編輯器中新增兩張或多張影像，如下圖所示。

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. 選取色版中的所有影像，然後按一下左上角的扳手圖示（如下圖所示），以開啟「色版層級設定」對話方塊。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **「頁** 面」對話框開啟。

   >[!NOTE]
   >依預設，頻道中的影像會設為8秒的播放持續時間。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   編輯&#x200B;**持續時間**&#x200B;從8000(ms)到3000(ms)，即3秒。 按一下&#x200B;**Page**&#x200B;對話方塊右上角的核取標籤，以儲存變更。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 查看結果{#viewing-the-result}

一旦更新頻道播放持續時間（在此範例中，所有三張影像）後，您會注意到影像現在會播放3秒，而非8秒（預設值）。

![channel_preview](assets/channel_preview.gif)


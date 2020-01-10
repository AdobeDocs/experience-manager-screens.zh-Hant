---
title: 影像播放持續時間
seo-title: 影像播放持續時間
description: 請依本頁瞭解影像播放持續時間。
seo-description: 請依本頁瞭解影像播放持續時間。
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 69a40e437fa9b19e283bcf1a1322d18e17990a49

---


# 影像播放持續時間 {#image-playback-duration}

## 概覽 {#overview}

在您建立序列頻道並新增影像後，依預設，所有影像都會採用頻道層級設定中定義的播放持續時間。 任何個別影像仍可覆寫預設值，並有不同的播放持續時間，這是透過編輯特定影像元件的播放持續時間來完成的。

### 必備條件 {#prerequisites}

開始實作此功能之前，請確定您已將專案設定為開始實作此功能的先決條件。 例如，

1. 建立AEM Screens專案(在此範例中為 **ChannelLevelPlayback**)

1. 在「頻道」檔案夾 **下建立序列頻道** ，做 **為PlaybackChannel**

1. 將內容新增至 **PlaybackChannel**

## 編輯頻道層級影像播放持續時間指派 {#editing-channel-level-image-playback-duration-assignment}

下節說明如何編輯AEM Screens頻道中內容的播放持續時間。

### 更新頻道中影像的播放持續時間 {#updating-the-playback-duration-for-images-in-a-channel}

請依照下列步驟瞭解如何更新頻道層級影像播放持續時間指派：

1. 導覽至序列頻道 **PlaybackChannel**。

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. 按一 **下動作列** 中的「編輯」以開啟編輯器。

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. 在色版編輯器中新增兩張或多張影像，如下圖所示。

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. 選取色版中的所有影像，然後按一下左上角的扳手圖示（如下圖所示），以開啟「色版層級設定」對話方塊。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **頁面** 」對話方塊。

   >[!NOTE]
   >
   >依預設，頻道中的影像會設為8秒的播放持續時間。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   編輯 **持續時間** (從8000(ms)到3000(ms)，即3秒)。 按一下「頁面」對話方塊右上角的核取 **標籤** ，以儲存您所做的變更。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 查看結果 {#viewing-the-result}

一旦更新頻道播放持續時間（在此範例中，所有三張影像）後，您會注意到影像現在會播放3秒，而非8秒（預設值）。

![channel_preview](assets/channel_preview.gif)


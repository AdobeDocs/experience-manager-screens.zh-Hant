---
title: 專案層級影像播放持續時間
seo-title: 專案層級影像播放持續時間
description: '此功能可讓您在專案層級定義影像播放持續時間。 '
seo-description: '此功能可讓您在專案層級定義影像播放持續時間。 '
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: ae1f7cab650f811ae03f0a2f3dfa49ec855997ee

---


# 專案層級影像播放持續時間 {#project-level-image-playback}

## 概覽 {#overview}

此功能可讓您在專案層級定義影像播放持續時間。 依預設，所有影像都會繼承此播放持續時間。 如果專案層級未定義持續時間，則會繼續預設的8秒播放。

### 必備條件 {#prerequisites}

使用此功能之前，請務必先設定專案作為開始實作此功能的先決條件。 例如，

1. 建立AEM Screens專案(在此範例中為 **ProjectLevelPlayback**)

1. 在「頻道」資料夾下 **建立序列頻道** ，做 **為PlayBackChannel**

1. 新增內容至 **PlayBackChannel**

   ![資產](assets/image_playback1.png)

   例如，下列影像會展示新增至 **PlayBackChannel編輯器的影像** :

   ![資產](assets/image_playback2.png)

## 編輯項目級影像播放持續時間分配 {#editing-project-level-image-playback-duration-assignment}

下節說明如何編輯AEM Screens專案中內容的播放持續時間。

### 在專案層級更新影像的播放持續時間 {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>如果您想要更新影像或頻道層級的播放持續時間，請參閱頻 [道層級影像播放持續時間](channel-level-image-playback.md)。

請依照下列步驟瞭解如何更新專案層級的影像播放持續時間：

1. 導覽至您的專 **案ProjectLevelPlayback** ，然後從動作 **列按一下「屬性** 」。
   ![資產](assets/image_playback3.png)

1. 選取色版中的所有影像，然後按一下左上角的扳手圖示（如下圖所示），以開啟「色版層級設定」對話方塊。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **頁面** 」對話方塊。

   >[!NOTE]
   >
   >依預設，頻道中的影像會設為播放持續時間8秒，而視訊會以其預設持續時間播放。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   編輯 **持續時間** (從8000(ms)到3000(ms)，即3秒)。 按一下「頁面」對話方塊右上角的核取 **標籤** ，以儲存您所做的變更。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 查看結果 {#viewing-the-result}

一旦更新頻道播放持續時間（在此範例中，所有三張影像）後，您會注意到影像現在會播放3秒，而非8秒（預設值）。

![channel_preview](assets/channel_preview.gif)


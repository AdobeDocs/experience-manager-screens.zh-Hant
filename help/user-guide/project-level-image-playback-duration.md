---
title: 項目級影像回放持續時間
seo-title: Project Level Image Playback Duration
description: 此功能允許您在項目級別定義影像回放持續時間。
seo-description: This functionality allows you to define image playback duration at the project level.
contentOwner: jsyal
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 1%

---


# 項目級影像回放持續時間 {#project-level-image-playback}

## 概觀 {#overview}

此功能允許您在項目級別定義影像回放持續時間。 預設情況下，所有影像都繼承此播放持續時間。 如果在項目級別未定義持續時間，則預設的8秒回放將繼續。

### 必備條件 {#prerequisites}

使用此功能之前，請確保將項目設定為開始實施此功能的先決條件。 例如，

1. 建立AEM Screens項目(在本示例中， **項目級別回放**)

1. 將序列通道建立為 **播放回頻道** 在 **頻道** 資料夾

1. 將內容添加到 **播放回頻道**

   ![資產](assets/image_playback1.png)

   例如，以下影像顯示添加到 **播放回頻道** 編輯器：

   ![資產](assets/image_playback2.png)

## 編輯項目級影像回放持續時間分配 {#editing-project-level-image-playback-duration-assignment}

以下部分說明如何編輯AEM Screens項目中內容的播放持續時間。

### 在項目級別更新影像的播放持續時間 {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>如果要更新影像或頻道級播放持續時間，請參閱 [通道級影像播放持續時間](channel-level-image-playback.md)。

按照以下步驟瞭解如何更新項目級影像回放持續時間：

1. 導航到項目 **項目級別回放** 按一下 **屬性** 按鈕。
   ![資產](assets/image_playback3.png)

1. 選擇通道中的所有影像，然後按一下左上角的扳手錶徵圖（如下圖所示）以開啟「通道級別配置」(Channel level Configure)對話框。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **頁面** 對話框。

   >[!NOTE]
   >
   >預設情況下，頻道中的影像被設定為8秒的播放持續時間，視頻以預設持續時間長度播放。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   編輯 **持續時間** 從8000(ms)到3000(ms)，即3秒。 按一下右上角的複選標籤 **頁面** 對話框。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 查看結果 {#viewing-the-result}

更新頻道播放持續時間（在本例中，所有三幅影像）後，您會注意到這些影像現在將播放3秒而不是8秒（預設值）。

![通道預覽](assets/channel_preview.gif)


---
title: 影像播放持續時間
seo-title: Image Playback Duration
description: 按照本頁瞭解影像回放持續時間。
seo-description: Follow this page to learn about image playback duration.
contentOwner: jsyal
source-git-commit: 69a40e437fa9b19e283bcf1a1322d18e17990a49
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 1%

---


# 影像播放持續時間 {#image-playback-duration}

## 概觀 {#overview}

建立序列通道並向其中添加影像後，預設情況下，所有影像都將採用在通道級別配置中定義的播放持續時間。 任何單個影像仍然可以覆蓋預設影像並具有不同的播放持續時間，這可以通過編輯特定影像元件的播放持續時間來完成。

### 必備條件 {#prerequisites}

在開始實施此功能之前，請確保已將項目設定為開始實施此功能的先決條件。 例如，

1. 建立AEM Screens項目(在本示例中， **通道級回放**)

1. 將序列通道建立為 **播放頻道** 在 **頻道** 資料夾

1. 將內容添加到 **播放頻道**

## 編輯頻道級影像播放持續時間分配 {#editing-channel-level-image-playback-duration-assignment}

以下部分說明如何編輯AEM Screens頻道中內容的播放持續時間。

### 更新頻道中影像的播放持續時間 {#updating-the-playback-duration-for-images-in-a-channel}

按照以下步驟瞭解如何更新通道級別影像播放持續時間分配：

1. 導航到序列通道 **播放頻道**。

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. 按一下 **編輯** 的子菜單。

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. 在通道編輯器中添加兩幅或多幅影像，如下圖所示。

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. 選擇通道中的所有影像，然後按一下左上角的扳手錶徵圖（如下圖所示）以開啟「通道級別配置」(Channel level Configure)對話框。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **頁面** 對話框。

   >[!NOTE]
   >
   >預設情況下，頻道中的影像設定為8秒的播放持續時間。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   編輯 **持續時間** 從8000(ms)到3000(ms)，即3秒。 按一下右上角的複選標籤 **頁面** 對話框。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 查看結果 {#viewing-the-result}

更新頻道播放持續時間（在本例中，所有三幅影像）後，您會注意到這些影像現在將播放3秒而不是8秒（預設值）。

![通道預覽](assets/channel_preview.gif)


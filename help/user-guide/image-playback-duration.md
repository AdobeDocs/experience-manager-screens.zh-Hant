---
title: 影像播放持續時間
description: 瞭解AEM Screens中的影像播放持續時間。
contentOwner: jsyal
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---


# 影像播放持續時間 {#image-playback-duration}

## 概觀 {#overview}

建立連續色版並將影像新增至其中後，依預設，所有影像會假設色版層級設定中定義的播放持續時間。 任何個別影像仍可覆寫預設值，並具有不同的播放持續時間，這是透過編輯特定影像元件的播放持續時間來完成的。

### 先決條件 {#prerequisites}

在實作此功能之前，請確定您已設定專案作為開始實作此功能的先決條件。 例如，

1. 建立AEM Screens專案(在此範例中， **ChannelLevelPlayback**)
1. 建立順序頻道為 **PlaybackChannel** 在 **頻道** 資料夾
1. 新增內容至 **PlaybackChannel**

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

1. 選取色版中的所有影像，然後選取左上角的扳手圖示（如下圖所示）。 「通道層級設定」對話方塊開啟。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **頁面** 對話方塊開啟。

   >[!NOTE]
   >
   >根據預設，色版中的影像會設為8秒的播放期間。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   編輯 **持續時間** 從8000 （毫秒）到3000 （毫秒），即3秒。 按一下右上方的勾號 **頁面** 對話方塊，以便儲存變更。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 檢視結果 {#viewing-the-result}

當您更新頻道播放持續時間（在此範例中是三個影像）時，請注意影像現在會播放3秒而非8秒（預設值）。

![channel_preview](assets/channel_preview.gif)


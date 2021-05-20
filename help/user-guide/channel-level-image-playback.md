---
title: 通道層級大量影像播放持續時間
seo-title: 通道層級大量影像播放持續時間
description: 本頁面說明如何編輯特定影像元件的播放期間。
seo-description: 本頁面說明如何編輯特定影像元件的播放期間。
uuid: 4ebb00a9-b04d-4dfe-9fee-2348a2e2c142
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: df3cf999-0c8d-4754-8b58-5c6ced2c8ca5
docset: aem65
feature: 製作畫面
role: Administrator, Developer
level: Intermediate
exl-id: 95aa761a-1449-4e18-8115-3b151036dc54
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 1%

---

# 通道級別大量影像播放持續時間{#channel-level-bulk-image-playback-duration}

## 概覽 {#overview}

建立序列頻道並新增影像後，依預設，所有影像都會採用頻道層級設定中定義的播放持續時間。 任何個別影像仍可覆寫預設值，且有不同的播放期間，這是透過編輯特定影像元件的播放期間來完成。

### 必備條件 {#prerequisites}

開始實作此功能之前，請確定您已將專案設定為開始實作此功能的先決條件。 例如，

1. 建立AEM Screens專案範例， **ChannelLevelPlayback**。

1. 在&#x200B;**Channels**&#x200B;資料夾下，將序列通道建立為&#x200B;**PlaybackChannel**。

1. 將內容新增至&#x200B;**PlaybackChannel**。

## 編輯通道級別影像播放持續時間分配{#editing-channel-level-image-playback-duration-assignment}

下節說明如何編輯AEM Screens頻道中內容的播放期間。

### 更新通道{#updating-the-playback-duration-for-images-in-a-channel}中影像的播放持續時間

請依照下列步驟了解如何更新管道層級影像播放持續時間指派：

1. 導覽至序列頻道&#x200B;**PlaybackChannel**。

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. 按一下動作列中的&#x200B;**編輯**&#x200B;以開啟編輯器。

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. 在通道編輯器中新增兩個或多個影像，如下圖所示。

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. 選取通道中的所有影像，然後按一下左上角的扳手圖示（如下圖所示），以開啟「通道層級設定」對話方塊。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **** 頁面對話方塊開啟。

   >[!NOTE]
   >依預設，頻道中的影像會設為8秒的播放期間。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   編輯從8000(ms)到3000(ms)（即3秒）的&#x200B;**持續時間**。 按一下&#x200B;**Page**&#x200B;對話方塊右上角的勾選記號，儲存您的變更。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 查看結果{#viewing-the-result}

更新頻道播放持續時間（在此範例中為全部三個影像）後，您會發現影像現在會播放3秒，而非8秒（預設值）。

![channel_preview](assets/channel_preview.gif)

---
title: 通道級批量影像播放持續時間
seo-title: Channel Level Bulk Image Playback Duration
description: 此頁介紹如何編輯特定影像元件的回放持續時間。
seo-description: This page describes how you can edit the playback duration of a specific image component.
uuid: 4ebb00a9-b04d-4dfe-9fee-2348a2e2c142
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: df3cf999-0c8d-4754-8b58-5c6ced2c8ca5
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 95aa761a-1449-4e18-8115-3b151036dc54
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 1%

---

# 通道級批量影像播放持續時間 {#channel-level-bulk-image-playback-duration}

## 概觀 {#overview}

建立序列通道並向其中添加影像後，預設情況下，所有影像都將採用在通道級別配置中定義的播放持續時間。 任何單個影像仍然可以覆蓋預設影像並具有不同的播放持續時間，這可以通過編輯特定影像元件的播放持續時間來完成。

### 必備條件 {#prerequisites}

在開始實施此功能之前，請確保已將項目設定為開始實施此功能的先決條件。 例如，

1. 建立AEM Screens項目示例， **通道級回放**。

1. 將序列通道建立為 **播放頻道** 在 **頻道** 的子菜單。

1. 將內容添加到 **播放頻道**。

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
   >預設情況下，頻道中的影像設定為8秒的播放持續時間。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   編輯 **持續時間** 從8000(ms)到3000(ms)，即3秒。 按一下右上角的複選標籤 **頁面** 對話框。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 查看結果 {#viewing-the-result}

更新頻道播放持續時間（在本例中，所有三幅影像）後，您會注意到這些影像現在將播放3秒而不是8秒（預設值）。

![通道預覽](assets/channel_preview.gif)

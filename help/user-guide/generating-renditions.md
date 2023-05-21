---
title: 視頻格式副本
seo-title: Video Renditions
description: 請按照此頁瞭解如何為「螢幕」項目生成全高清格式副本。
seo-description: Follow this page to learn about generating full HD renditions for your Screens project.
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# 視頻格式副本 {#video-renditions}

您可以生成手動和自動的全高清格式副本。 以下部分介紹了向資產中添加格式副本的工作流。

## 自動生成全高清格式副本  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>如果AEM Screens視頻呈現形式在您的設備上沒有最佳播放，請聯繫硬體供應商瞭解視頻的規格。 這將有助於獲得設備上的最佳效能，從而建立您自己的自定義視頻配置檔案，在該配置檔案中，您為FFMPEG提供適當的參數以生成格式副本。 隨後，使用以下步驟將自定義視頻配置檔案添加到配置檔案清單中。
>
>此外，請參見 [視頻故障排除](troubleshoot-videos.md) 調試和排除頻道中播放視頻的故障。

按照以下步驟自動生成全高清格式副本：

1. 選擇Adobe Experience Manager連結（左上），然後按一下錘表徵圖以選擇要選擇的工具 **工作流**。

   按一下 **模型** 中各屬性的附加資訊。

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. 選擇 **DAM更新資產** 模型，然後從操作欄中按一下「編輯」(Edit)以開啟 **DAM更新資產** 的子菜單。

   ![步驟5_ — 編輯_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. 按兩下 **FFmpeg轉碼** 的子菜單。

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. 選擇 **進程** 頁籤。 將全高清配置檔案輸入到 **參數** 為： ***,profile:fullhd-bp,profile:fullhd-hp*** 按一下 **確定**。

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. 按一下 **保存** 左上角 **DAM更新資產** 的上界。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. 導航到 **資產** 上傳新視頻。 按一下視頻並開啟「格式副本」側欄，您會注意到這兩個全高清視頻。

   ![步驟10__open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. 開啟 **格式副本** 從側軌上。

   ![步驟11_-_open_therenditionssiarg](assets/step11_-_open_therenditionssiderail.png)

1. 您會注意到兩個新的全高清格式副本。

   ![步驟12_-_2_new_renditionsaded to thevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## 手動生成全高清格式副本 {#manually-generating-full-hd-renditions}

按照以下步驟手動生成全高清格式副本：

1. 選擇Adobe Experience Manager連結（左上），然後按一下錘表徵圖以選擇要選擇的工具 **工作流**。

   按一下 **模型** 中各屬性的附加資訊。

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. 選擇 **螢幕更新資產** 模型，然後按一下 **啟動工作流** 開啟 **運行工作流** 對話框。

   ![步驟5_ — 開始_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. 在 **負載** 按一下 **運行**。

   ![步驟6_ — 選擇_thederidevideo](assets/step6_-_select_thedesiredvideo.png)

1. 導航到 **資產**，向下鑽取到您的資產，然後按一下。

   ![步驟7_ — 開啟_視頻資產](assets/step7_-_open_thevideoasset.png)

1. 開啟 **格式副本** 並且您會注意到新的全高清格式副本。

   ![步驟8_-open_therenditionssifart](assets/step8_-_open_therenditionssiderail.png)

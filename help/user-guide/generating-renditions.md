---
title: 視訊轉譯
description: 瞭解如何為您的AEM Screens專案產生Full HD轉譯。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# 視訊轉譯 {#video-renditions}

您可以產生手動和自動Full HD轉譯。 下節將說明將轉譯新增至資產的工作流程。

## 自動產生Full HD轉譯 {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>如果AEM Screens視訊轉譯無法在您的裝置上以最佳方式播放，請聯絡硬體廠商，以取得視訊的規格。 這麼做有助於讓裝置發揮最佳效能。 它可協助您建立自己的自訂視訊設定檔，讓您為FFMPEG提供適當的引數以產生轉譯。 然後，使用以下步驟，將您的自訂視訊設定檔新增到設定檔清單。
>
>另請參閱[視訊疑難排解](troubleshoot-videos.md)，對頻道中播放的視訊進行偵錯和疑難排解。

請依照下列步驟，自動產生Full HD轉譯：

1. 按一下Adobe Experience Manager連結（左上方），然後按一下槌子圖示，這樣您就可以按一下&#x200B;**工作流程**。

   按一下&#x200B;**模型**。

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. 在工作流程模型管理中，按一下&#x200B;**DAM更新資產**&#x200B;模型，然後從動作列按一下&#x200B;**編輯**。

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. 在&#x200B;**DAM更新資產**&#x200B;視窗中，按兩下&#x200B;**FFmpeg轉碼**&#x200B;步驟。

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. 按一下「**處理序**」標籤。
1. 在&#x200B;**引數**&#x200B;中輸入清單的Full HD設定檔，如下所示：
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. 按一下&#x200B;**「確定」**。

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. 按一下&#x200B;**DAM更新資產**&#x200B;畫面左上角的&#x200B;**儲存**。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. 導覽至&#x200B;**Assets**&#x200B;並上傳新影片。 按一下視訊，然後開啟「轉譯」側欄。 請注意兩部Full HD影片。

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. 從側邊欄開啟&#x200B;**轉譯**。

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. 請注意兩個新的Full HD轉譯。

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## 手動產生Full HD轉譯 {#manually-generating-full-hd-renditions}

請依照下列步驟，手動產生Full HD轉譯：

1. 按一下Adobe Experience Manager連結（左上方），然後按一下槌子圖示，這樣您就可以按一下[工具]，再按一下[工作流程]&#x200B;**&#x200B;**。

   按一下&#x200B;**模型**。

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. 在工作流程模型管理中，按一下&#x200B;**Screens更新資產**&#x200B;模型，然後按一下&#x200B;**開始工作流程**&#x200B;以開啟&#x200B;**執行工作流程**&#x200B;對話方塊。

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. 按一下&#x200B;**承載**&#x200B;中想要的視訊，然後按一下&#x200B;**執行**。

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. 導覽至&#x200B;**Assets**，深入研究您的資產，然後按一下它。

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. 開啟&#x200B;**轉譯**&#x200B;側邊欄。 請注意新的Full HD轉譯。

   ![step8_-_open_terenditionssiderail](assets/step8_-_open_therenditionssiderail.png)

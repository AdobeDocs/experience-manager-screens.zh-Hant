---
title: 視訊轉譯
seo-title: 視訊轉譯
description: 請依照本頁進一步瞭解如何為您的「螢幕」專案產生完整的HD轉譯。
seo-description: 請依照本頁進一步瞭解如何為您的「螢幕」專案產生完整的HD轉譯。
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
feature: 製作畫面
role: 管理員、開發人員
level: 中級
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---


# 視訊轉譯{#video-renditions}

您可以產生手動和自動的全高清轉譯。 下節說明將轉譯新增至資產的工作流程。

## 自動產生完整HD轉譯{#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>如果AEM Screens視訊轉譯無法在您的裝置上最佳播放，請連絡硬體廠商以取得視訊規格。 這有助於在裝置上取得最佳效能，進而建立您自己的自訂視訊設定檔，供您為FFMPEG提供適當的參數以產生轉譯。 隨後，請使用下列步驟將自訂視訊描述檔新增至描述檔清單。
>
>此外，請參閱[疑難排解視訊](troubleshoot-videos.md)以除錯和疑難排解頻道中的視訊播放。

請依照下列步驟自動產生完整HD轉譯：

1. 選擇「Adobe Experience Manager」連結（左上角），然後按一下「槌子」表徵圖以選擇要選擇&#x200B;**Workflow**&#x200B;的工具。

   按一下&#x200B;**Models**&#x200B;進入工作流模型管理。

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. 選擇&#x200B;**DAM更新資產**&#x200B;模型，然後從操作欄按一下編輯以開啟&#x200B;**DAM更新資產**&#x200B;窗口。

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. 連按兩下&#x200B;**FFmpeg轉碼**&#x200B;步驟。

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. 選擇&#x200B;**Process**&#x200B;頁籤以編輯進程參數。 在&#x200B;**Arguments**&#x200B;的清單中輸入完整的HD配置檔案：***,profile:fullhd-bp,profile:fullhd-hp***，然後按一下&#x200B;**確定**。

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. 按一下&#x200B;**DAM更新資產**&#x200B;螢幕左上角的&#x200B;**Save**。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. 導覽至&#x200B;**Assets**&#x200B;並上傳新視訊。 按一下影片並開啟「轉譯」邊欄，您就會注意到這兩個全高清影片。

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. 從側欄開啟「**轉譯**」。

   ![step11_-_open_therenditionssifrage](assets/step11_-_open_therenditionssiderail.png)

1. 您會注意到兩個新的完整HD轉譯。

   ![step12_-_2_new_renditionsadedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## 手動產生完整HD轉譯{#manually-generating-full-hd-renditions}

請依照下列步驟手動產生完整HD轉譯：

1. 選擇「Adobe Experience Manager」連結（左上角），然後按一下「槌子」表徵圖以選擇要選擇&#x200B;**Workflow**&#x200B;的工具。

   按一下&#x200B;**Models**&#x200B;進入工作流模型管理。

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. 選擇&#x200B;**螢幕更新資產**&#x200B;模型，然後按一下&#x200B;**啟動工作流**&#x200B;以開啟&#x200B;**運行工作流**&#x200B;對話框。

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. 在&#x200B;**Payload**&#x200B;中選擇所需的視頻，然後按一下&#x200B;**Run**。

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. 導覽至&#x200B;**Assets**，下鑽至您的資產，然後按一下。

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. 開啟&#x200B;**轉譯**&#x200B;側邊欄，您就會注意到新的完整HD轉譯。

   ![step8_-_open_therenditionssifarge](assets/step8_-_open_therenditionssiderail.png)


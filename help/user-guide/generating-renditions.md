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
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# 視訊轉譯 {#video-renditions}

您可以產生手動和自動Full HD轉譯。 下節將說明將轉譯新增至資產的工作流程。

## 自動產生Full HD轉譯  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>如果AEM Screens視訊轉譯無法在您的裝置上以最佳方式播放，請聯絡硬體廠商，以取得視訊的規格。 這有助於在裝置上取得最佳效能，因此可建立您自己的自訂視訊設定檔，您可以在其中提供適當的引數讓FFMPEG產生轉譯。 然後，使用以下步驟，將您的自訂視訊設定檔新增到設定檔清單。
>
>另請參閱 [疑難排解影片](troubleshoot-videos.md) 若要在您的頻道中針對視訊播放進行除錯和疑難排解。

請依照下列步驟自動產生Full HD轉譯：

1. 選取Adobe Experience Manager連結（左上方），然後選取槌子圖示，讓您選取 **工作流程**.

   選取 **模型**.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. 在工作流程模型管理中，選取 **DAM更新資產** 模型和選擇 **編輯** 從動作列移除。

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. 在 **DAM更新資產** 視窗，按兩下 **FFmpeg轉碼** 步驟。

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. 選取 **程式** 標籤。
1. 輸入Full HD設定檔至中的清單 **引數** 如下所示：
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. 選取 **確定**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. 選取 **儲存** 左側的 **DAM更新資產** 畫面。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. 瀏覽至 **資產** 並上傳新影片。 選取視訊並開啟「轉譯」側欄。 請注意兩部Full HD影片。

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. 開啟 **轉譯** 從側邊欄移除。

   ![step11_-_open_terenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. 請注意兩個新的Full HD轉譯。

   ![step12_-_2_new_renditionsaredtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## 手動產生Full HD轉譯 {#manually-generating-full-hd-renditions}

請依照下列步驟手動產生Full HD轉譯：

1. 選取Adobe Experience Manager連結（左上方），然後選取槌子圖示，讓您選取工具並選取 **工作流程**.

   選取 **模型**.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. 在工作流程模型管理中，選取 **畫面更新資產** 模型，並選取 **開始工作流程** 以開啟 **執行工作流程** 對話方塊。

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. 在「 」中選取所需的視訊 **裝載** 並選取 **執行**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. 瀏覽至 **資產**，深入研究您的資產，然後選取它。

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. 開啟 **轉譯** 側邊欄。 請注意新的Full HD轉譯。

   ![step8_-_open_theridationssiderail](assets/step8_-_open_therenditionssiderail.png)

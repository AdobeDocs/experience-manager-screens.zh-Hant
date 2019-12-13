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
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# 視訊轉譯 {#video-renditions}

您可以產生手動和自動的全高清轉譯。 下節說明將轉譯新增至資產的工作流程。

## 自動產生完整HD轉譯 {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>如果AEM Screens視訊轉譯無法在您的裝置上最佳播放，請連絡硬體廠商以取得視訊的規格。 這有助於在裝置上取得最佳效能，進而建立您自己的自訂視訊設定檔，供您為FFMPEG提供適當的參數以產生轉譯。 隨後，請使用下列步驟將自訂視訊描述檔新增至描述檔清單。
>
>此外，請參 [閱疑難排解影片](troubleshoot-videos.md) ，以除錯和疑難排解頻道中播放的影片。

請依照下列步驟自動產生完整HD轉譯：

1. 選取Adobe Experience Manager連結（左上），然後按一下槌子圖示以選取「工 **作流程」**。

   按一下「 **模型** 」(Models)以輸入工作流模型管理。

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. 選擇「 **DAM更新資產模型** 」，然後從動作列按一下「編輯」以開啟「 **DAM更新資產」視窗** 。

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. 按兩下 **FFmpeg轉碼步驟** 。

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. 選擇「 **流程** 」頁籤以編輯流程參數。 在「參數」( **Arguments)中，將完整HD配置式輸** 入： ***,profile:fullhd-bp,profile:fullhd-hp*** ，然後按一 **下確定**。

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. 按一 **下** 「 **DAM Update Asset」畫面左上角的「** 儲存」。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. 導覽至「 **資產** 」並上傳新視訊。 按一下影片並開啟「轉譯」邊欄，您就會注意到這兩個全高清影片。

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. 從邊 **欄開啟** 「轉譯」。

   ![step11_-_open_therenditionssifrage](assets/step11_-_open_therenditionssiderail.png)

1. 您會注意到兩個新的完整HD轉譯。

   ![step12_-_2_new_renditionsadedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## 手動產生完整HD轉譯 {#manually-generating-full-hd-renditions}

請依照下列步驟手動產生完整HD轉譯：

1. 選取Adobe Experience Manager連結（左上），然後按一下槌子圖示以選取「工 **作流程」**。

   按一下「 **模型** 」(Models)以輸入工作流模型管理。

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. 選擇「 **畫面更新資產** 」模型，然後按一下「開 **始工作流程** 」以開啟「 **執行工作流程** 」對話方塊。

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. 在「裝載」中選取所要的 **視訊** ，然後按一 **下「執行」**。

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. 導覽至 **資產**、下鑽至資產，然後按一下它。

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. 開啟「 **轉譯** 」側欄，您就會注意到新的全HD轉譯。

   ![step8_-_open_therenditionssifarge](assets/step8_-_open_therenditionssiderail.png)


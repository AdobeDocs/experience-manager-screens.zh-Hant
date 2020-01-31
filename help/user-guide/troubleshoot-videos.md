---
title: 視訊播放設定與疑難排解
seo-title: 疑難排解影片
description: null
seo-description: 請依照本頁瞭解如何疑難排解影片。 當您將視訊上傳至DAM並新增頻道時，可能會遇到視訊無法在Screens播放器中播放的問題，本節說明如何對頻道中播放的視訊進行除錯和疑難排解。
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
translation-type: tm+mt
source-git-commit: 6abe309a8beb264f1505b6f39d786acc035bad05

---


# 視訊播放設定與疑難排解 {#video-playback-configuration-and-troubleshooting}

當您將視訊上傳至DAM並新增頻道時，可能會遇到視訊無法在Screens播放器中播放的問題。

以下章節說明如何對頻道中的視訊播放進行除錯和疑難排解。

## DAM轉譯 {#dam-renditions}

當您將視訊上傳至頻道後，AEM應該會開始為其建立一些轉譯。 您可以在「資產」下檢視您的影片。

若要檢視影片：

1. 例如，導覽至您的影片 `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`。
1. 按一下影片，然後展開左上角的選單，然後按一下「轉 **譯」**。

應該有不同的轉譯（MP4或M4V）。

如果沒有轉譯，請確定您已在執行AEM的作業系統上安裝ffmpeg。

>[!CAUTION]
>
>如果沒有轉譯，請確定您已在執行AEM的作業系統上安裝ffmpeg。
>
>按一 [下這裡](https://www.ffmpeg.org/download.html) ，以安裝ffmpeg。

## 視訊資產 {#video-assets}

如果您在視訊下未看到來源屬性，可能是視訊未轉碼。 如果視訊已正確轉碼，則會顯示在儀表板中，如下圖所示。

檢查ffmpeg是否已安裝並且視訊設定檔。

![chlimage_1-2](assets/chlimage_1-2.png)

### 檢查視訊設定檔 {#checking-video-profile}

1. 導覽至「視 **訊設定檔**」，即，然後按 `http://localhost:4502/etc/dam/video.html` 一下「上 **傳測試視訊」**。

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. 上傳測試視訊，然後按一 **下「確定** 」開始轉碼。

   如果轉碼失敗，請展開ffmpeg輸出，以瞭解ffmpeg的主控台輸出中的任何錯誤。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   此外，如果視訊轉碼成功，則可下載轉碼檔案。

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >請確定您有足夠的時間讓視訊轉碼（在將視訊新增至任何頻道之前，它應該會顯示新標籤而非處理）。

### 使用視訊元件檢查描述檔 {#checking-profile-with-a-video-component}

如果視訊元件未正確設定，請檢查頁面設計的描述檔清單。

1. 導覽至您的頻道並選取 **設計** 模式。

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. 選取視訊並開啟「編 **輯** 」對話方塊。 開啟「描 **述檔** 」標籤。

   選取不同的描述檔（至少應該有「High Quality H.264」描述檔）。

   ![chlimage_1-7](assets/chlimage_1-7.png)

### 在Web Player中檢查視訊 {#checking-the-video-in-the-web-player}

使用 **Web Player**`http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` 來驗證在瀏覽器（Chrome和Safari）中的播放。 Chrome用於Android裝置，而Safari則是OSX和iOS瀏覽器。

如果視訊未在Safari上執行，則不會在OSX和iOS播放器中執行。 這可能是編碼問題，而視訊必須重新編碼。

請依照下列步驟，使用DAM工作流程來建立FullHD轉譯：

1. 導覽至工 *作流程模型管理*，即 `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`。
1. 選取「畫 **面更新資產** 」模型。
1. 從操 **作欄中按一下「啟動工作流** 」(Start Workflow **)，開啟「** 運行工作流」(Run Workflow)對話框。

1. 在「裝載」中選取您的視 **訊資產**。
1. 按一 **下Run**。

>[!NOTE]
>
>請稍許時間建立轉譯，但在數秒／分鐘（視視訊大小而定）後，在Safari上重新載入Web Player。

#### 自動播放策略標幟疑難排解 {#troubleshooting-autoplay-policy-flag}

萬一AEM Screens播放器會接收視訊但未顯示，您需要疑難排解「自動播放原則」標幟。

請依照下列步驟來疑難排解Google的自動播放政策標幟問題：

1. 導覽至 ***chrome://flags/#autoplay-policy ***
1. 將「自 **動播放** 」原則從「 **預設** 」變更 **為不需要使用者手勢**

1. 重新啟動網頁瀏覽器並更新播放器

>[!NOTE]
>
>若要進一步瞭解使用Chrome中新的自動播放政策提供良好使用者體驗的最佳範例，請參閱 *Autoplay政策變更檔案*，即 `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`。

### 同步多個播放器的視訊 {#syncing-video-across-multiple-players}

若要在多種裝置上同步播放視訊，您應對視訊所屬的序列使用絕對策略。

#### 需求 {#requirements}

* 相同的2+播放器
* 理想的相似硬體
* 相同的網路拓撲（播放器連接到NTP伺服器，該伺服器將其內部系統時鐘對齊）

#### 建立絕對策略 {#setting-up-the-absolute-strategy}

絕對策略：

* 計算錨點時間（當天的午夜）
* 計算序列的持續時間（其所有項的持續時間總和）
* 在任何時間點，它都會透過解序列_remaining_time =(current_time - anchor_time)% sequence_duration，來計算目前應播放的項目和下一個項目。

請依照下列步驟設定絕對策略：

1. 導覽至您的頻道作者，並選取順序元件，如下圖所示。
1. 開啟其配置對話框。
1. 編輯策 **略** ，並新增絕對。

![chlimage_1-8](assets/chlimage_1-8.png)

>[!NOTE]
>
>玩家的作業系統必須有相同的時鐘。

**對齊OS x上的時鐘** ：請遵循以下步驟來對齊OSX上的時鐘：

1. 在每 **個OSX方塊上開啟日期** 和時間偏好設定
1. 檢查 **自動設定日期和時間**
1. 將值0.pool.ntp.org、1.pool.ntp.org、2.pool.ntp.org、3.pool.ntp.org、time.apple.com貼上到下拉菜單中，或只運行 *sudo ntpdate -u -v 0.pool.ntp.org*
1. 啟動2位以上的播放器

玩家可能需要一些時間才能開始新的對齊序列。


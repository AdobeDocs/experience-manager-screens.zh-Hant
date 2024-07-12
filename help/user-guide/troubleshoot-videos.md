---
title: 視訊播放設定及疑難排解
description: 瞭解如何針對AEM Screens頻道中的視訊播放進行除錯和疑難排解。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
feature: Channels, Interactive
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 1%

---

# 視訊播放設定及疑難排解 {#video-playback-configuration-and-troubleshooting}

上傳影片至DAM並新增至您的頻道時，您可能會遇到影片無法在AEM Screens Player中播放的問題。

以下章節說明如何在您的頻道中針對播放視訊進行除錯和疑難排解。

## DAM轉譯 {#dam-renditions}

上傳視訊至管道後，AEM應開始為其建立一些轉譯。 您可以在Assets下檢視影片。

若要觀看影片：

1. 導覽至您的視訊，例如`http://localhost:4502/assets.html/content/dam/we-retail/en/videos`。
1. 按一下視訊並展開左上角的功能表，然後按一下&#x200B;**轉譯**。

應該有不同的轉譯（MP4或M4V）。

如果沒有轉譯，請確定您已在執行AEM的作業系統上安裝FFMPEG。

>[!CAUTION]
>
>如果沒有轉譯，請確定您已在執行AEM的作業系統上安裝FFMPEG。
>
>按一下[這裡](https://www.ffmpeg.org/download.html)以安裝FFMPEG。

## 影片Assets {#video-assets}

如果您在視訊底下沒有看到來源屬性，可能是視訊沒有獲得轉解碼。 如果視訊正確轉碼，就會顯示在控制面板中，如下所示：

檢查是否已安裝FFMPEG以及視訊設定檔。

![chlimage_1-2](assets/chlimage_1-2.png)

### 正在檢查視訊設定檔 {#checking-video-profile}

1. 導覽至&#x200B;**視訊設定檔**，也就是`http://localhost:4502/etc/dam/video.html`，然後按一下&#x200B;**上傳測試視訊**。

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. 上傳測試視訊並按一下&#x200B;**確定**，您就可以開始轉碼。

   如果轉碼視訊失敗，請展開FFMPEG輸出以瞭解FFMPEG主控台輸出中的任何錯誤。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   此外，如果視訊轉碼成功，也可以下載轉碼檔案。

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >在新增視訊到任何頻道之前，請務必提供足夠的時間讓視訊轉碼（應該顯示新標籤而不是處理）。

### 使用視訊元件檢查設定檔 {#checking-profile-with-a-video-component}

如果視訊元件未正確設定，請檢查頁面設計中的設定檔清單。

1. 導覽至您的頻道，然後按一下&#x200B;**設計**&#x200B;模式。

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. 按一下視訊並開啟&#x200B;**編輯**&#x200B;對話方塊。 開啟&#x200B;**設定檔**&#x200B;標籤。

   >[!NOTE]
   >按一下不同的設定檔（至少應有「高品質H.264」設定檔）。

### 在網頁播放器中檢查視訊 {#checking-the-video-in-the-web-player}

使用&#x200B;**網頁播放器** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0`驗證瀏覽器(Chrome和Safari)中的播放。 Chrome可在Android™裝置上使用，而Safari則可作為OS X和iOS瀏覽器。

如果影片無法在Safari上執行，則無法在OS X和iOS播放器中執行。 此問題可能是編碼問題，因此必須對視訊重新編碼。

若要使用DAM工作流程來建立FullHD轉譯，請執行以下操作：

1. 導覽至&#x200B;*工作流程模型管理員* （即`http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`）。
1. 按一下&#x200B;**Screens更新資產**&#x200B;模型。
1. 按一下動作列中的&#x200B;**開始工作流程**。
1. 在&#x200B;**執行工作流程**&#x200B;對話方塊中，按一下&#x200B;**承載**&#x200B;中的視訊資產。
1. 按一下&#x200B;**執行**。

>[!NOTE]
>
>允許一些時間建立轉譯，但在幾秒/分鐘後（取決於視訊大小），請在Safari上重新載入網頁播放器。

#### 疑難排解自動播放原則標幟 {#troubleshooting-autoplay-policy-flag}

如果AEM Screens Player擷取視訊但未顯示，請對「自動播放原則」標幟進行疑難排解。

請依照下列步驟，針對Google的自動播放原則標幟問題進行疑難排解：

1. 導覽至&#x200B;***chrome://flags/#autoplay-policy***
1. 將&#x200B;**自動播放原則**&#x200B;從&#x200B;**預設**&#x200B;變更為&#x200B;**不需要使用者手勢**

1. 重新啟動網頁瀏覽器並更新播放器

>[!NOTE]
>
>進一步瞭解Chrome中新的自動播放原則的最佳實務，以便獲得良好的使用者體驗。 在`https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`檢視&#x200B;*自動播放原則變更*。

### 跨多個播放器同步視訊 {#syncing-video-across-multiple-players}

若要跨多部裝置同步播放視訊，您應該對視訊所屬的順序使用絕對策略。

#### 要求 {#requirements}

* 相同的2+個播放器
* 理想上類似的硬體
* 相同的網路拓撲（播放器會連線至與其內部系統時鐘一致的NTP伺服器）

#### 設定絕對策略 {#setting-up-the-absolute-strategy}

絕對策略：

* 計算錨記時間（當天午夜）。
* 計算序列的持續時間（其所有專案的持續時間總和）。
* 在任何時間點，它會透過解決序列_remaining_time = (current_time - anchor_time) % sequence_duration來計算目前應該播放哪個專案以及下一個專案。

請依照下列步驟設定絕對策略：

1. 導覽至您的管道作者，然後按一下順序元件，如下圖所示。
1. 開啟其設定對話方塊。
1. 編輯&#x200B;**策略**&#x200B;並新增絕對。

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >播放器的作業系統必須有相同的時鐘。

**在OS X上對齊時鐘**&#x200B;請依照下列步驟在OS X上對齊時鐘：

1. 開啟每個OS X方塊上的&#x200B;**日期與時間**&#x200B;偏好設定
1. 檢查&#x200B;**自動設定日期和時間**
1. 在下拉式清單中貼上值0.pool.ntp.org、1.pool.ntp.org、2.pool.ntp.org、3.pool.ntp.org、time.apple.com，或直接執行&#x200B;*sudo ntpdate -u -v 0.pool.ntp.org*
1. 啟動2個以上的播放器

播放器開始新的對齊順序可能需要一些時間。

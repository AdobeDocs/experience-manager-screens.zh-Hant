---
title: 視訊播放設定和疑難排解
seo-title: 疑難排解影片
description: 請參照本頁面，了解如何對頻道中的視訊播放進行除錯和疑難排解。
seo-description: 請依照本頁面了解如何疑難排解影片。 將視訊上傳至DAM並將其新增至管道時，您可能會遇到視訊無法在Screens播放器中播放的問題，本區段說明如何對在管道中播放的視訊進行除錯和疑難排解。
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
feature: 頻道，互動式
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 0%

---

# 視訊播放設定與疑難排解{#video-playback-configuration-and-troubleshooting}

將視訊上傳至DAM並將其新增至管道時，您可能會遇到視訊無法在Screens播放器中播放的問題。

以下小節說明如何對頻道中的視訊播放進行除錯和疑難排解。

## DAM轉譯{#dam-renditions}

將視訊上傳至管道後，AEM應開始為其建立一些轉譯。 您可以在「資產」下檢視影片。

若要檢視影片：

1. 導覽至您的視訊，例如`http://localhost:4502/assets.html/content/dam/we-retail/en/videos`。
1. 按一下視訊，然後展開左上角的功能表，然後按一下「轉譯」****。

應有不同的轉譯（MP4或M4V）。

如果沒有轉譯，請確定您已在執行AEM的作業系統上安裝ffmpeg。

>[!CAUTION]
>
>如果沒有轉譯，請確定您已在執行AEM的作業系統上安裝ffmpeg。
>
>按一下[這裡](https://www.ffmpeg.org/download.html)以安裝ffmpeg。

## 視訊資產{#video-assets}

如果您在影片下未看到來源屬性，可能是影片未轉碼。 如果視訊轉譯正確，會顯示在控制面板中，如下圖所示。

檢查已安裝ffmpeg且視訊設定檔。

![chlimage_1-2](assets/chlimage_1-2.png)

### 檢查視訊設定檔{#checking-video-profile}

1. 導覽至&#x200B;**視訊設定檔**，即`http://localhost:4502/etc/dam/video.html`，然後按一下&#x200B;**上傳測試視訊**。

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. 上傳測試影片，然後按一下&#x200B;**確定**&#x200B;開始轉碼。

   如果轉碼失敗，請展開ffmpeg輸出以了解ffmpeg控制台輸出中的任何錯誤。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   此外，如果視訊轉碼成功，可以下載轉碼檔案。

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >在將視訊新增至任何管道之前，請確定您有足夠的時間讓視訊轉碼（應該會先顯示新標籤，而非處理）。

### 使用視訊元件{#checking-profile-with-a-video-component}檢查設定檔

如果視訊元件未正確設定，請檢查頁面設計中的設定檔清單。

1. 導覽至您的通道，並選取&#x200B;**Design**&#x200B;模式。

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. 選擇視頻並開啟&#x200B;**Edit**&#x200B;對話框。 開啟&#x200B;**Profiles**&#x200B;標籤。

   >[!NOTE]
   >選取不同的設定檔（至少「High Quality H.264」設定檔應存在）。

### 正在檢查Web播放器中的視頻{#checking-the-video-in-the-web-player}

使用&#x200B;**Web Player** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0`驗證瀏覽器（Chrome和Safari）中的播放。 Chrome會用於Android裝置，而Safari則是OSX和iOS瀏覽器。

如果影片未在Safari上執行，則不會在OSX和iOS播放器中執行。 這可能是編碼問題，視訊必須重新編碼。

請依照下列步驟，使用DAM工作流程來建立FullHD轉譯：

1. 導覽至&#x200B;*工作流程模型管理員*，即`http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`。
1. 選擇&#x200B;**Screens Update Asset**&#x200B;模型。
1. 從操作欄按一下&#x200B;**啟動工作流**&#x200B;以開啟&#x200B;**運行工作流**&#x200B;對話框。

1. 在&#x200B;**Payload**&#x200B;中選取您的視訊資產。
1. 按一下&#x200B;**運行**。

>[!NOTE]
>
>請留些時間建立轉譯，但幾秒/分鐘後（視視訊大小而定），在Safari上重新載入Web播放器。

#### 自動播放策略標誌{#troubleshooting-autoplay-policy-flag}疑難解答

如果AEM Screens播放器擷取視訊但未顯示，您需要疑難排解自動播放原則旗標。

請依照下列步驟，疑難排解google的自動播放政策旗標問題：

1. 導覽至&#x200B;***chrome://flags/#autoplay-policy***
1. 將&#x200B;**自動播放策略**&#x200B;從&#x200B;**Default**&#x200B;更改為&#x200B;**不需要用戶手勢**

1. 重新啟動網頁瀏覽器並更新播放器

>[!NOTE]
>
>若要進一步了解Chrome中新自動播放原則對良好使用者體驗的最佳作法，請參閱&#x200B;*自動播放原則變更*（亦即`https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`）的檔案。

### 在多個播放器間同步視訊{#syncing-video-across-multiple-players}

若要在多部裝置間同步播放視訊，您應針對視訊所屬的序列使用絕對策略。

#### 需求 {#requirements}

* 相同的2+個玩家
* 理想的硬體
* 相同的網路拓撲（播放器連接到NTP伺服器，使其內部系統時鐘一致）

#### 設定絕對策略{#setting-up-the-absolute-strategy}

絕對策略：

* 計算錨點時間（當天的午夜）
* 計算序列的持續時間（其所有項的持續時間總和）
* 它會在任何時間點通過求解sequence _remaing_time =(current_time - anchor_time)% sequence_duration來計算當前應播放的項目和下一個項目。

請依照下列步驟，設定絕對策略：

1. 導覽至您的管道作者，並選取順序元件，如下圖所示。
1. 開啟其設定對話方塊。
1. 編輯&#x200B;**策略**&#x200B;並添加絕對。

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >玩家的作業系統必須有相同的時鐘。

**在OS XF上對齊** 時鐘按照以下步驟在OSX上對齊時鐘：

1. 在每個OSX框上開啟&#x200B;**日期和時間**&#x200B;首選項
1. 檢查&#x200B;**自動設定日期和時間**
1. 在下拉式清單中貼上值0.pool.ntp.org、1.pool.ntp.org、2.pool.ntp.org、3.pool.ntp.org、time.apple.com，或直接運行&#x200B;*sudo ntpdate -u -v 0.pool.ntp.org*
1. 啟動2+玩家

玩家可能需要一些時間才能開始新的對齊序列。

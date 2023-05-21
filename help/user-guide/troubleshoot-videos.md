---
title: 視頻播放配置和故障排除
seo-title: Troubleshooting Videos
description: 按照本頁瞭解如何調試和排除頻道中視頻播放的故障。
seo-description: Follow this page to learn how to troubleshoot videos. When you upload a video to the DAM and add it your channel, you might encounter issues that video might not play in Screens player and this section describes how to debug and troubleshoot video playing in your channel.
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
feature: Channels, Interactive
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 0%

---

# 視頻播放配置和故障排除 {#video-playback-configuration-and-troubleshooting}

將視頻上載到DAM並添加頻道時，可能會遇到視頻在螢幕播放器中可能無法播放的問題。

以下各節介紹如何調試和排除頻道中播放視頻的故障。

## DAM格式副本 {#dam-renditions}

將視頻上載到頻道後，應AEM開始為其建立一些格式副本。 您可以在「資產」下查看視頻。

要查看視頻：

1. 例如，導航到視頻 `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`。
1. 按一下視頻並展開左上角的菜單，然後按一下 **格式副本**。

應有不同的格式副本（MP4或M4V）。

如果沒有格式副本，請確保已在運行的OS上安裝AEM了ffmpeg。

>[!CAUTION]
>
>如果沒有格式副本，請確保已在運行的OS上安裝AEM了ffmpeg。
>
>按一下 [這裡](https://www.ffmpeg.org/download.html) 安裝ffmpeg。

## 視頻資產 {#video-assets}

如果在視頻下沒有看到源屬性，則可能是該視頻未得到轉碼。 如果視頻被正確轉碼，它將顯示在儀表板中，如下圖所示。

檢查已安裝ffmpeg和視頻配置檔案。

![chlimage_1-2](assets/chlimage_1-2.png)

### 檢查視頻配置檔案 {#checking-video-profile}

1. 導航到 **視頻配置檔案**&#x200B;就是， `http://localhost:4502/etc/dam/video.html` 按一下 **上載Test視頻**。

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. 上載test視頻，然後按一下 **確定** 開始轉碼。

   如果轉碼失敗，請展開ffmpeg輸出，以瞭解ffmpeg的控制台輸出中的任何錯誤。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   此外，如果視頻轉碼成功，則可以下載轉碼檔案。

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >在將標籤添加到任何頻道之前，請確保為視頻提供足夠的時間進行轉碼（它應顯示新標籤，而不是處理標籤）。

### 使用視頻元件檢查配置檔案 {#checking-profile-with-a-video-component}

如果視頻元件配置不正確，請檢查頁面設計中的配置檔案清單。

1. 導航到您的頻道，然後選擇 **設計** 的子菜單。

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. 選擇視頻並開啟 **編輯** 對話框。 開啟 **配置檔案** 頁籤。

   >[!NOTE]
   >選擇不同的配置檔案（至少「High Quality H.264」配置檔案應該存在）。

### 在Web播放器中檢查視頻 {#checking-the-video-in-the-web-player}

使用 **Web播放器** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` 在瀏覽器（Chrome和Safari）中驗證回放。 Chrome在Android設備上使用，而Safari是OSX和iOS瀏覽器。

如果視頻在Safari上不運行，OSX和iOS播放器將不運行。 這可能是編碼問題，必須重新編碼視頻。

按照以下步驟使用DAM工作流建立FullHD格式副本：

1. 導航到 *工作流模型管理員*，即 `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`。
1. 選擇 **螢幕更新資產** 模型。
1. 按一下 **啟動工作流** 開啟 **運行工作流** 對話框。

1. 在 **負載**。
1. 按一下 **運行**。

>[!NOTE]
>
>允許一些時間建立格式副本，但幾秒/分鐘後（取決於視頻大小），在Safari上重新載入Web播放器。

#### 自動播放策略標誌疑難解答 {#troubleshooting-autoplay-policy-flag}

如果AEM Screens播放器拿起視頻但未顯示，則需要排除「自動播放策略」標誌的故障。

按照以下步驟排除google的自動播放策略標誌問題：

1. 導航到 ***chrome://flags/#autoplay-policy***
1. 更改 **自動播放策略** 從 **預設** 至 **不需要用戶手勢**

1. 重新啟動Web瀏覽器並更新播放器

>[!NOTE]
>
>要瞭解有關Chrome中新自動播放策略的最佳用戶體驗的更多資訊，請參閱文檔， *自動播放策略更改*&#x200B;就是， `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`。

### 在多個播放器之間同步視頻 {#syncing-video-across-multiple-players}

要在多個設備之間同步播放視頻，應使用視頻所屬序列的絕對策略。

#### 要求 {#requirements}

* 相同的2+位
* 理想的相似硬體
* 相同的網路拓撲（播放器連接到NTP伺服器，該伺服器將其內部系統時鐘對齊）

#### 設定絕對策略 {#setting-up-the-absolute-strategy}

絕對策略：

* 計算錨點時間（當天的午夜）
* 計算序列的持續時間（其所有項的持續時間之和）
* 在任何時間點，它通過解析sequence_remaining_time =(current_time - anchor_time)% sequence_duration來計算當前應播放的項和下一個項。

按照以下步驟設定絕對策略：

1. 導航到您的渠道作者並選擇序列元件，如下圖所示。
1. 開啟其配置對話框。
1. 編輯 **策略** 並添加絕對。

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >玩家的作業系統必須有相同的時鐘。

**在OS X上對齊時鐘** 按照以下步驟對齊OSX上的時鐘：

1. 開啟 **日期和時間** 每個OSX框上的首選項
1. 檢查 **自動設定日期和時間**
1. 將值0.pool.ntp.org、1.pool.ntp.org、2.pool.ntp.org、3.pool.ntp.org、time.apple.com貼上到下拉清單中或只運行 *sudo ntpdate -u -v 0.pool.ntp.org*
1. 啟動2+玩家

玩家可能需要一段時間才能開始新的排列順序。

---
title: 使用Chrome播放器作為擴充功能
description: 瞭解如何將Chrome播放器安裝為AEM Screens的瀏覽器擴充功能。
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# 使用Chrome播放器作為擴充功能 {#using-chrome-player}

ChromeOS播放器可在開發人員模式中安裝為Chrome瀏覽器外掛程式，而不需要實際的Chrome播放器裝置。

>[!CAUTION]
>
> 建議使用Chrome播放器作為疑難排解的擴充功能，以進行快速示範、偵錯並疑難排解客戶問題。 請勿將此機制用於需要資訊站模式和中央管理的生產部署。

請依照本頁面瞭解安裝Chrome播放器做為瀏覽器擴充功能的相關資訊。

1. 按一下 [此處](https://download.macromedia.com/screens/) 以下載最新的Chrome播放器。

1. 解壓縮並儲存在磁碟上。

1. 開啟Chrome瀏覽器，然後按一下3點選單並點選 **更多工具** 從 **擴充功能** 或直接導覽至「 」 `chrome://extensions`.

1. 切換至 **開發人員** 模式從右上角。

1. 按一下 **載入已解壓縮** 從左上角，並載入解壓縮的Chrome Player。

1. 如果擴充功能清單中有AEM Screens Chrome Player外掛程式，請勾選該外掛程式。

1. 開啟新標籤，然後從左上角按一下「應用程式」圖示，或直接導覽至 `chrome://apps`.

1. 按一下 **AEM Screens外掛程式** 以便啟動Chrome播放器。

   >[!NOTE]
   >
   > 依預設，播放器會以全熒幕模式啟動。 按下 **Esc** 以結束全熒幕模式。


## 進階偵錯提示 {#advanced-debugging-tips}

1. 當播放器在本機下載內容時，您可以前往「 」，瀏覽在本機下載的內容 `http://localhost:24502`.

   >[!NOTE]
   >
   > 如果上述URL無法運作，表示播放器未指派顯示區，或內容未成功下載。 檢查播放器設定JSON的網路索引標籤，檢視播放器是否取得正確的詳細資料，以及下載內容中是否有任何網路問題。

1. 按一下滑鼠右鍵並檢查Chrome播放器的三個圖層。
   **除錯內容**：以滑鼠右鍵按一下並檢查內容，針對執行中的內容進行偵錯(內容功能表中應會有名為「Inspect」的單一專案)

   **除錯韌體**：開啟管理員UI，然後按一下滑鼠右鍵並檢查以除錯韌體（播放器）程式碼。 （應該會有一個選項來檢查及檢查背景頁面，並模擬瀏覽器重新啟動。）

   **偵錯背景頁面**：開啟管理員UI，然後按一下滑鼠右鍵並檢查背景頁面（適用於http伺服器等背景服務）。

## 升級播放器擴充功能 {#upgrading-player}

如果發行新版本的播放器，請依照下列步驟升級播放器擴充功能。 您也可以依照下列指示，測試升級案例：

1. 關閉任何執行中的Chrome和播放器執行個體
1. 重新命名包含播放器檔案的舊資料夾
1. 在與舊資料夾相同的位置解壓縮新的zip
1. 啟動Chrome並瀏覽至 `chrome://extensions`
1. 核取播放器圖示，然後按一下重新整理或重新載入按鈕

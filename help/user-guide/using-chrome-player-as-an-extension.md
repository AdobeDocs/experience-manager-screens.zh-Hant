---
title: 使用Chrome Player做為擴充功能
seo-title: 使用Chrome Player做為擴充功能
description: 'null'
seo-description: 'null'
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 使用Chrome Player做為擴充功能 {#using-chrome-player}

ChromeOS Player可在開發人員模式下以Chrome Browser外掛程式安裝，而不需實際的Chrome Player裝置。

>[!CAUTION]
>
> 建議使用Chrome Player做為疑難排解的擴充功能，以進行快速示範、除錯，並疑難排解客戶問題。 此機制不應用於需要kiosk模式和集中管理的生產部署。

請依照本頁瞭解如何將chrome Player安裝為瀏覽器擴充功能。

1. 按一下這裡下載最新的Chrome Player。

1. 解壓縮並儲存在磁碟上。

1. 開啟Chrome瀏覽器，然後按一下3點功能表，然後選取位於右上角的「 **More** **Tools from** Extensions `chrome://extensions`」（從延伸功能中取得更多工具），或直接導覽至。

1. 從右上角 **切換** 「開發人員」模式。

1. 按一下左 **上角的「載入解壓縮** 」，然後載入解壓縮的Chrome Player。

1. 如果副檔名清單中有AEM Screens Chrome Player增效模組，請勾選。

1. 開啟新的標籤，然後按一下左上角的「應用程式」圖示，或直接導覽至 `chrome://apps`。

1. 按一下「 **AEM Screens Plugin** 」以啟動Chrome Player。
   >[!NOTE]
   >
   > 依預設，播放器會以全螢幕模式啟動。 按 **Esc** 退出全螢幕模式。


## 進階除錯提示 {#advanced-debugging-tips}

1. 當播放器已在本機下載內容後，您可前往瀏覽本機下載的內容 `http://localhost:24502`。

   >[!NOTE]
   >
   > 如果上述URL無法運作，表示播放器未指派顯示畫面或內容未成功下載。 檢查播放器設定JSON的網路標籤，以查看播放器是否取得正確的詳細資料，以及下載中的任何網路問題。

1. 您可以按一下滑鼠右鍵並檢查chrome播放器的三個圖層
   **除錯內容**:在內容上按一下滑鼠右鍵並加以檢查，以除錯執行中的內容（內容選單中應有一個名為「Inspect」的項目）

   **調試韌體**:啟動管理員UI，然後按一下滑鼠右鍵並進行檢查，以除錯韌體（播放器）程式碼（應該有選項來檢查和檢查背景頁面並模擬瀏覽器重新啟動）

   **除錯背景頁面**:開啟管理員UI，然後以滑鼠右鍵按一下並檢查背景頁面（針對背景服務，例如http伺服器）

## 升級播放器擴充功能 {#upgrading-player}

如果新版播放器已發行，請依照下列步驟升級播放器擴充功能。 您也可以依照下列指示來測試升級藍本：

1. 關閉任何執行中的chrome和播放器例項
1. 使用播放器檔案重新命名舊資料夾
1. 將新郵遞區號解壓縮至舊資料夾的相同位置
1. 啟動Chrome並導覽至 `chrome://extensions`
1. 勾選播放器圖示，然後按一下重新整理或重新載入按鈕
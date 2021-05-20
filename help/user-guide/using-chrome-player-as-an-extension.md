---
title: 使用Chrome Player作為擴充功能
seo-title: 使用Chrome Player作為擴充功能
description: 請詳閱本頁，了解如何將Chrome播放器安裝為瀏覽器擴充功能。
seo-description: 'null'
feature: 管理畫面
role: Administrator
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# 使用Chrome播放器作為擴充功能{#using-chrome-player}

ChromeOS播放器可在開發人員模式下，安裝為Chrome瀏覽器外掛程式，而不需要實際的Chrome播放器裝置。

>[!CAUTION]
>
> 若要快速示範、除錯以及疑難排解客戶問題，建議使用Chrome Player作為疑難排解的擴充功能。 此機制不應用於需要資訊站模式和集中管理的生產部署。

請詳閱本頁，了解如何將Chrome播放器安裝為瀏覽器擴充功能。

1. 按一下[這裡](https://download.macromedia.com/screens/)以下載最新的Chrome播放器。

1. 解壓縮並儲存在磁碟上。

1. 開啟Chrome瀏覽器，按一下3個點的功能表，然後從右上角的&#x200B;**延伸模組**&#x200B;選取&#x200B;**更多工具**，或直接導覽至`chrome://extensions`。

1. 從右上角切換&#x200B;**開發人員**&#x200B;模式。

1. 按一下左上角的「載入未封裝&#x200B;**」 ，然後載入未壓縮的Chrome播放器。**

1. 如果擴充功能清單中有AEM Screens Chrome Player外掛程式，請查看。

1. 開啟新標籤，然後按一下左上角的「應用程式」圖示，或直接導覽至`chrome://apps`。

1. 按一下&#x200B;**AEM Screens外掛程式**&#x200B;以啟動Chrome Player。
   >[!NOTE]
   >
   > 依預設，播放器會以全螢幕模式啟動。 按&#x200B;**esc**&#x200B;退出全螢幕模式。


## 進階偵錯提示{#advanced-debugging-tips}

1. 播放器在本機下載內容後，您可以前往`http://localhost:24502`瀏覽本機下載的內容。

   >[!NOTE]
   >
   > 如果上述URL無法運作，表示播放器未獲指派顯示畫面或內容未成功下載。 檢查播放器設定JSON的網路標籤，查看播放器是否取得正確的詳細資料，以及下載中的任何網路問題。

1. 您可以按一下滑鼠右鍵並檢查Chrome播放器的三個層
   **除錯內容**:以滑鼠右鍵按一下並檢查內容，以偵錯執行中的內容(內容功能表中應該有一個名為「Inspect」的單一項目)

   **調試韌體**:開啟管理員UI，然後按一下滑鼠右鍵並檢查以偵錯韌體（播放器）程式碼（應該有選項可檢查和檢查背景頁面並模擬瀏覽器重新啟動）

   **除錯背景頁面**:開啟管理員UI，然後按一下滑鼠右鍵並檢查背景頁面（適用於背景服務，例如http伺服器）

## 升級播放器擴充功能{#upgrading-player}

若已發行新版播放器，請依照下列步驟升級播放器擴充功能。 您也可以依照下列指示測試升級案例：

1. 關閉任何執行中的chrome和播放器例項
1. 使用播放器檔案重新命名舊資料夾
1. 將新郵遞區號解壓縮至與舊資料夾相同的位置
1. 啟動Chrome並導覽至`chrome://extensions`
1. 檢查播放器圖示，然後按一下重新整理或重新載入按鈕

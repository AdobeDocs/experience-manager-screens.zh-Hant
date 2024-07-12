---
title: 使用Chrome Player作為擴充功能
description: 瞭解如何將Chrome播放器安裝為AEM Screens的瀏覽器擴充功能。
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# 使用Chrome播放器作為擴充功能 {#using-chrome-player}

ChromeOS播放器可在開發人員模式中安裝為Chrome瀏覽器外掛程式，而不需要實際的Chrome播放器裝置。

>[!CAUTION]
>
> 建議使用Chrome播放器作為疑難排解的擴充功能，以進行快速示範、偵錯並疑難排解客戶問題。 請勿將此機制用於需要資訊站模式和中央管理的生產部署。

請依照本頁所述安裝Chrome播放器作為瀏覽器擴充功能的相關資訊。

1. 按一下[這裡](https://download.macromedia.com/screens/)以下載最新的Chrome播放器。

1. 解壓縮並儲存在磁碟上。

1. 開啟Chrome瀏覽器，然後按一下3點選單，再按一下右上角的&#x200B;**擴充功能**&#x200B;中的&#x200B;**更多工具**，或直接導覽至`chrome://extensions`。

1. 從右上角開啟&#x200B;**開發人員**&#x200B;模式。

1. 從左上角按一下「**載入解壓縮**」，然後載入解壓縮的Chrome播放程式。

1. 如果擴充功能清單中有AEM Screens Chrome播放器外掛程式，請加以檢視。

1. 開啟新標籤，然後從左上角按一下Apps圖示，或直接導覽至`chrome://apps`。

1. 按一下&#x200B;**AEM Screens外掛程式**，即可啟動Chrome播放程式。

   >[!NOTE]
   >
   > 依預設，播放器會以全熒幕模式啟動。 按&#x200B;**Esc**&#x200B;結束全熒幕模式。


## 進階偵錯提示 {#advanced-debugging-tips}

1. 當播放器已在本機下載內容時，您可以移至`http://localhost:24502`來瀏覽本機下載的內容。

   >[!NOTE]
   >
   > 如果上述URL無法運作，表示播放器未指派顯示區，或內容未成功下載。 檢查網路索引標籤，瞭解播放器設定JSON，瞭解播放器是否取得正確的詳細資料，以及下載內容中是否有任何網路問題。

1. 以滑鼠右鍵按一下並檢查Chrome播放器的三層。
   **偵錯內容**：在內容上按一下滑鼠右鍵並檢查，以偵錯執行中的內容(內容功能表中應有一個名為「Inspect」的專案)

   **偵錯韌體**：開啟管理UI，然後按一下滑鼠右鍵並檢查以偵錯韌體（播放器）代碼。 （應該會有一個選項來檢查及檢查背景頁面，並模擬瀏覽器重新啟動。）

   **偵錯背景頁面**：開啟管理員UI，然後按一下滑鼠右鍵並檢查背景頁面（針對http伺服器等背景服務）。

## 升級播放器擴充功能 {#upgrading-player}

如果發行新版本的播放器，請依照下列步驟升級播放器擴充功能。 您也可以依照下列指示，測試升級案例：

1. 關閉任何執行中的Chrome和播放器執行個體
1. 重新命名包含播放器檔案的舊資料夾
1. 在與舊資料夾相同的位置解壓縮新的zip
1. 啟動Chrome並導覽至`chrome://extensions`
1. 核取播放器圖示，然後按一下重新整理或重新載入按鈕

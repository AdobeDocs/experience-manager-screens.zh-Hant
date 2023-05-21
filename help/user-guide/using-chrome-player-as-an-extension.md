---
title: 使用Chrome播放器作為擴展
seo-title: Using Chrome Player as an Extension
description: 按照此頁瞭解如何將chrome播放器安裝為瀏覽器擴展。
seo-description: null
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# 使用Chrome播放器作為擴展 {#using-chrome-player}

ChromeOS播放器可以在開發人員模式下作為Chrome瀏覽器插件安裝，而不需要實際的Chrome播放器設備。

>[!CAUTION]
>
> 建議使用Chrome Player作為故障排除的擴展，以便快速演示、調試和解決客戶問題。 此機制不應用於需要自助服務亭模式和中央管理的生產部署。

按照此頁瞭解如何將chrome播放器安裝為瀏覽器擴展。

1. 按一下 [這裡](https://download.macromedia.com/screens/) 下載最新的Chrome播放器。

1. 解壓縮並將其保存到磁碟上。

1. 開啟Chrome瀏覽器，按一下「3點」菜單，然後選擇 **更多工具** 從 **擴展** 位於右上角，或直接導航到 `chrome://extensions`。

1. 開啟 **開發人員** 的下界。

1. 按一下 **載入已解壓縮** 從左上角裝載已解壓的Chrome播放器。

1. 如果擴展清單中提供，請檢查AEM ScreensChrome Player插件。

1. 開啟新頁籤，然後按一下左上角的「應用」表徵圖，或直接導航到 `chrome://apps`。

1. 按一下 **AEM Screens插件** 啟動Chrome播放器。
   >[!NOTE]
   >
   > 預設情況下，播放器以全屏模式啟動。 按 **esc** 退出全屏模式。


## 高級調試提示 {#advanced-debugging-tips}

1. 播放器在本地下載內容後，您可以通過轉到 `http://localhost:24502`。

   >[!NOTE]
   >
   > 如果上述URL不起作用，則表示未為播放器分配顯示或內容未成功下載。 檢查播放器配置JSON的網路頁籤，查看播放器是否獲得了正確的詳細資訊以及下載中的任何網路問題。

1. 可以按一下右鍵並檢查鉻合金播放器的三層
   **調試內容**:按一下右鍵並檢查內容以調試正在運行的內容(上下文菜單中應有一個名為「Inspect」的項目)

   **調試韌體**:開啟管理員UI，然後按一下右鍵並檢查以調試韌體（播放器）代碼（應有一個選項來檢查和檢查後台頁面並模擬瀏覽器重啟）

   **調試後台頁**:開啟管理員UI，然後按一下右鍵並檢查後台頁面（對於後台服務，如http伺服器）

## 升級播放器擴展 {#upgrading-player}

如果已發佈播放器的新版本，請按照以下步驟升級播放器擴展。 您還可以按照以下說明test升級方案：

1. 關閉所有運行的chrome和player實例
1. 使用播放器檔案更名舊資料夾
1. 將新ZIP解壓到與舊資料夾相同的位置
1. 啟動Chrome並導航至 `chrome://extensions`
1. 選中播放器表徵圖，然後按一下「刷新」或「重新載入」按鈕

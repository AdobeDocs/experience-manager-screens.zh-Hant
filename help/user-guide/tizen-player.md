---
title: Tizen Player
description: 本頁說明Tizen Player的安裝與運作。
translation-type: tm+mt
source-git-commit: b439cfab068dcbbfab602ad8d31aaa2781bde805
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# 實作Tizen Player {#tizen-player}

## 安裝Tizen Player {#installing-tizen-player}

請依照下列步驟，為AEM畫面實作Tizen Player:

1. 導覽至 [**AEM 6.5 Player下載頁面**](https://download.macromedia.com/screens/) ，以下載Tizen Player。

1. 從本機電腦安裝Tizen播放器(.zip)檔案。

1. 取得本機電腦的IP位址。

   >[!NOTE]
   >對於 **終端機** 中的Mac和 **Windows** `ifconfig` type命令。

1. 從「終端機介面」，導覽至解壓縮安裝程式資料夾的相同目錄，並驗證localhost是否正常運作。

   >[!NOTE]
   >對於 **Mac**，鍵入 `http://localhost` 並驗證伺服器是否 `http` 正在運行。

1. Tizen播放器會從本機伺服器下載安裝程式。

1. 將兩個解壓縮的文 `AEMScreensPlayer.wgt` 件復 `sssp_config.xml` 制到 `/Library/WebServer/Documents`。

### SamSung裝置的組態更新 {#config-updates}

請依照Samsung裝置上的下列步驟，在裝置上完成AEM Screens播放器的安裝：

1. 按一下Samsung Remote **中的** 「Home」（首頁）按鈕。
1. 從「設 **定」中選取** 「URL啟動 **器」**。
1. 從「開 **發人員模式** 」中選擇「遠端」。
1. 安裝Web應用程式並輸入您電腦的IP位址。
AEM Screens Player應會自動安裝在Samsung裝置上。



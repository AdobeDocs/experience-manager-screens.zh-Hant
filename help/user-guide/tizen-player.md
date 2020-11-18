---
title: Tizen Player
description: 本頁說明Tizen Player的安裝與運作。
translation-type: tm+mt
source-git-commit: 835da341fcee8e4abb3375c43a0a130d3f79d859
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---


# 實作Tizen Player {#tizen-player}

## 安裝Tizen Player {#installing-tizen-player}

請依照下列步驟，為AEM畫面實作Tizen Player:

1. 導覽至 [**AEM 6.5 Player下載頁面**](https://download.macromedia.com/screens/) ，以下載Tizen Player。

1. 從本機電腦安裝Tizen播放器(.zip)檔案。

## 設定本地伺服器並解壓Zip檔案 {#setting-local-server}

請依照下列步驟來設定本機伺服器並複製解壓縮的檔案：

1. 取得本機電腦的IP位址。

   >[!NOTE]
   >您可以使用下列命令從您電腦的終端機取得IP位址：
   >* **Mac**: `ifconfig`
   >* **Windows**: `ipconfig`


1. 從「終端機介面」，導覽至解壓縮安裝程式資料夾的相同目錄，並驗證localhost是否正常運作。

   >[!NOTE]
   >對於 **Mac**，鍵入 `http://localhost` 並驗證伺服器是否 `http` 正在運行。

1. Tizen播放器會從本機伺服器下載安裝程式。

1. 將兩個解壓縮的文 `AEMScreensPlayer.wgt` 件復 `sssp_config.xml` 制到 `/Library/WebServer/Documents`。

### 在Samsung裝置上設定更新 {#config-updates}

請依照Samsung裝置上的下列步驟，在裝置上完成AEM Screens播放器的安裝：

1. 前往您的Samsung裝置，並指向您的localhost伺服器。
1. 從「 **設定」中選取** 「URL啟動器設 **** 定」，然後輸入localhost伺服器的IP位址。
1. 安裝Web應用程式。
1. 從「開 **發人員** 」模式 **中選擇「遠端」**。
1. AEM Screens Player現在應會自動安裝在您的Samsung裝置上。



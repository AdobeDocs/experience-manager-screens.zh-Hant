---
title: Tizen Player
description: 本頁說明Tizen Player的安裝與運作。
translation-type: tm+mt
source-git-commit: b3209d1dcce6defff347f288c704a1e7ea075ecf
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# 實作Tizen Player {#tizen-player}

## 安裝Tizen Player {#installing-tizen-player}

請依照下列步驟，為AEM畫面實作Tizen Player:

1. 導覽至&#x200B;[**AEM 6.5 Player下載**](https://download.macromedia.com/screens/)頁面以下載Tizen Player。

1. 從本機電腦安裝Tizen播放器(.zip)檔案。

## 設定本地伺服器並解壓Zip檔案{#setting-local-server}

請依照下列步驟來設定本機伺服器並複製解壓縮的檔案：

1. 取得本機電腦的IP位址。
   >[!NOTE]
   >請參閱官方檔案，瞭解如何在您的平台上啟用本機伺服器。

1. 從「終端機介面」，導覽至解壓縮安裝程式資料夾的相同目錄，並驗證localhost是否正常運作。

1. Tizen播放器會從本機伺服器下載安裝程式。

1. 將兩個提取的檔案（如`AEMScreensPlayer.wgt`和`sssp_config.xml`）複製到本地伺服器的根目錄。

### 在Samsung設備上配置更新{#config-updates}

請依照Samsung裝置上的下列步驟，在裝置上完成AEM Screens播放器的安裝：

1. 請至您的Samsung裝置。

1. 使用設備的遠程設備按一下&#x200B;**Home**&#x200B;按鈕，然後選擇&#x200B;**URL Launcher Settings**。

1. 輸入localhost伺服器的IP地址。

1. 從&#x200B;**開發人員模式**&#x200B;中選擇&#x200B;**Remote**。

1. 按一下設備遠程中的&#x200B;**Home**&#x200B;按鈕，然後選擇&#x200B;**URL Launcher**。

1. AEM Screens Player現在應會自動在您的Samsung裝置上安裝和啟動。




---
title: Tizen Player
description: 本頁說明Tizen Player的安裝與運作。
translation-type: tm+mt
source-git-commit: 1ec3e3541755550f719dbe53e83326d9796de14f
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---


# 實作Tizen Player {#tizen-player}

## 安裝Tizen Player {#installing-tizen-player}

請依照下列步驟，為AEM畫面實作Tizen Player:

1. 導覽至[AEM 6.5 Player下載](https://download.macromedia.com/screens/)頁面以下載Tizen Player。

1. 從本機電腦安裝Tizen Player *(.zip)*&#x200B;檔案。

## 設定本地伺服器並解壓Zip檔案{#setting-local-server}

請依照下列步驟來設定本機伺服器並複製解壓縮的檔案：

1. 取得本機電腦的IP位址。
   >[!NOTE]
   >請參閱官方檔案，瞭解如何在您的平台上啟用本機伺服器。

1. 從「終端機介面」，導覽至解壓縮安裝程式資料夾的相同目錄，並驗證localhost是否正常運作。

1. Tizen播放器會從本機伺服器下載安裝程式。

1. 將`AEMScreensPlayer.wgt`和`sssp_config.xml`這兩個提取的檔案複製到本地Apache Web伺服器的根目錄。

   >[!NOTE]
   >`AEMScreensPlayer.wgt`是實際的Tizen播放器應用程式，`sssp_config.xml`包含此地圖的相關資訊，可協助您將它安裝在Tizen裝置上。

### 在Samsung設備上配置更新{#config-updates}

請依照Samsung裝置上的下列步驟，在裝置上完成AEM Screens播放器的安裝：

1. 導覽至您的Samsung裝置並開啟。

1. 按一下設備遠程中的&#x200B;**MENU**&#x200B;按鈕，並從左側導航欄向下滾動到&#x200B;**System**。

1. 向下捲動並選取「透過URL啟動器播放&#x200B;**」選項。**
   ![影像](/help/user-guide/assets/tizen/url-launcher.png)

1. 按遙控器上的&#x200B;**Home**&#x200B;按鈕。

1. 輸入localhost伺服器的IP地址。

1. 從&#x200B;**開發人員模式**&#x200B;中選擇&#x200B;**Remote**。

1. 按一下設備遠程中的&#x200B;**Home**&#x200B;按鈕，然後選擇&#x200B;**URL Launcher**。

1. AEM Screens Player現在應會自動在您的Samsung裝置上安裝和啟動。

## Tizen Player的批量布建{#bulk-provisioning-tizen-player}

>[!NOTE]
>在大量裝置的每個裝置的管理員UI中手動輸入AEM伺服器位址，可能會很麻煩。 建議使用Samsung遠端管理(RMS)解決方案來部署和管理解決方案。 如需詳細資訊，請參閱[將Tizen Device註冊至Samsung遠端管理服務(RMS)](#enroll-tizen-device-rm)。

請依照下列步驟，在啟動應用程式時大量布建應用程式，以指向您的AEM作者實例：

1. 下載並安裝[Tizen Studio](https://developer.tizen.org/development/tizen-studio/download)。
1. 使用Tizen Studio開啟`wgt`檔案。
1. 開啟檔案`firmware-platform.js`並搜尋`DEFAULT_PREFERENCES`，並將伺服器URL變更為AEM作者URL並儲存。
1. 建立新的`wgt`檔案。

   >[!NOTE]
   >您可能需要建立或設定簽署憑證。

1. 部署此新的`wgt`檔案RMS，當播放器啟動時，它應會自動指向您的伺服器，因此您不需要為每個裝置手動輸入它。

### 將Tizen Device註冊到Samsung Remote Management Service(RMS){#enroll-tizen-device-rms}

請依照下列步驟，將Tizen Device註冊至Samsung Remote Management Service(RMS)並遠端設定URL啟動程式：

>[!NOTE]
>驗證網路設定和顯示器。

1. 按遙控器上的「Menu（菜單）」 ，然後轉到「System（系統）」 ，然後按「Play Via（播放途徑）」上的Enter。

   >[!NOTE]
   >確認畫面已設定為透過URL啟動器播放
1. 導航到&#x200B;**菜單** -> **網路** -> **伺服器網路設定** ，然後按&#x200B;**Enter**。

1. 導覽至「伺服器位址」並輸入MagicInfo URL存取權，然後按「完成」。

1. 登錄到MIS後，導航到「設備」頁籤
1. 查看IP位址和／或其Mac位址，以尋找您剛配置的裝置。
1. 在找到裝置後，按一下核取方塊並選取「核准」
1. 請確認畫面已設定為透過URL啟動器播放
1. 按遙控器上的「Menu（菜單）」 ，然後轉到「System（系統）」 ，然後按Enter鍵以播放方式
1. 導航至菜單->網路->伺服器網路設定，然後按Enter鍵
1. 前往「伺服器位址」並輸入MagicInfo URL存取權，然後按「完成」
1. 設定使用或不使用TLS（視情況而定）
1. 轉到埠並從伺服器中選擇埠號。
1. 選項準備就緒後，按一下「儲存」。




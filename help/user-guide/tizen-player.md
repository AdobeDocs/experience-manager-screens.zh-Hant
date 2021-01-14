---
title: Tizen Player
description: 本頁說明Tizen Player的安裝與運作。
translation-type: tm+mt
source-git-commit: c1e7187ad3841cde08377d6daf700885d17706ba
workflow-type: tm+mt
source-wordcount: '691'
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

請依照下列步驟，將Tizen裝置註冊至Samsung Remote Management Service(RMS)，並遠端設定URL啟動程式：

>[!NOTE]
>驗證網路設定和顯示器。

1. 導航到&#x200B;**菜單** -> **網路** -> **伺服器網路設定** ，然後按&#x200B;**Enter**。

   >[!NOTE]
   >確認畫面已設定為「透過URL啟動器播放」。

1. 導覽至「伺服器位址」並輸入MagicInfo URL存取權，然後按「完成」。

1. 設定使用或不使用TLS（視情況而定）
   1. 轉到埠並從伺服器中選擇埠號。
   1. 選項準備就緒後，按一下「儲存」。

1. 登錄到MIS後，導航到「設備」頁籤
   1. 查看IP位址和／或其Mac位址，以尋找您剛配置的裝置。
   1. 在找到裝置後，按一下核取方塊並選取「核准」。

1. 按一下「核准」按鈕後，將會出現下列快顯視窗
   1. 填寫所需資訊
   1. 選擇設備組
   1. 按一下「確定按鈕」以完成核准程式。

1. 在「裝置」核准後，它應會如下顯示在「裝置清單」中。
   1. 按一下裝置方塊&quot;i&quot;上的「資訊」按鈕

1. 「Device Information（設備資訊）」彈出窗口將如下所示，然後按一下「Edit Button（編輯按鈕）」。

1. 編輯設備選項並選擇&#x200B;**設定**&#x200B;頁籤。

1. 導覽至「**URL啟動器**」區段，然後輸入托管wgt的URL和`SSSP config file`以安裝`SSSP`應用程式，如下圖所示。

   ![影像](/help/user-guide/assets/tizen/rms-9.png)

1. 按一下&#x200B;**保存**&#x200B;以使更改在顯示螢幕上生效。





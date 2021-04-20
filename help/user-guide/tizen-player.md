---
title: Tizen Player
description: 本頁說明Tizen Player的安裝與運作。
feature: Administering Screens, Players
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 1%

---


# 實作Tizen Player {#tizen-player}

## 安裝Tizen Player {#installing-tizen-player}

請依照下列步驟，為AEM Screens實作Tizen Player:

1. 導覽至[AEM Screens播放器下載](https://download.macromedia.com/screens/)頁面以下載Tizen播放器。

1. 從本機電腦安裝Tizen Player *(.zip)*&#x200B;檔案。

## 設定本地伺服器並解壓Zip檔案{#setting-local-server}

>[!NOTE]
> 解壓縮zip檔案，並透過`http server`提供Tizen播放器。 （`http server`不必是本機或Apache伺服器）。

請遵循下列步驟：

1. 將`AEMScreensPlayer.wgt`和`sssp_config.xml`這兩個提取的檔案複製到本地Apache Web伺服器的根目錄。

   >[!NOTE]
   >`AEMScreensPlayer.wgt`是實際的Tizen播放器應用程式，`sssp_config.xml`包含此地圖的相關資訊，可協助您將它安裝在Tizen裝置上。

1. 取得本機HTTP伺服器的IP或URL(以及在步驟2中包含解壓縮檔案的檔案夾路徑（如果解壓縮至子檔案夾，而非根檔案夾）

1. Tizen播放器會從本機伺服器下載安裝程式。

### 在Samsung設備上配置更新{#config-updates}

請依照Samsung裝置上的下列步驟，在裝置上完成AEM Screens播放器的安裝：

1. 導覽至您的Samsung裝置並開啟。

1. 按一下設備遠程中的&#x200B;**MENU**&#x200B;按鈕，並從左側導航欄向下滾動到&#x200B;**System**。

1. 向下捲動並選取「透過&#x200B;**播放」選項，並將其變更為「URL啟動器」**&#x200B;選項。****
   ![影像](/help/user-guide/assets/tizen/rms-2.png)

1. 設定URL啟動器後，按遠端的&#x200B;**Home**&#x200B;按鈕。

1. 導覽至「**URL啟動器設定**」，然後輸入localhost伺服器的IP位址，然後按一下「完成」。****
   >[!NOTE]
   >Tizen播放器應能連線至http伺服器。

1. 現在，AEM Screens播放器應會自動在您的Samsung裝置上安裝和啟動。

   >[!NOTE]
   >Tizen設備和`http`伺服器應能夠相互連接，即伺服器應可以連接到Tizen播放器。


## 使用SameSite Cookie問題免除使用者代理程式{#exempting-user-agents}

>[!IMPORTANT]
>**本節適用於Adobe Experience Manager(AEM)6.5.5至AEM6.5.7**
>有些瀏覽器引擎與6.5到6.7所發佈之登入Token中使用的&#x200B;*SameSite=None*&#x200B;屬性不相容AEM。在大多數情況下，可將瀏覽器升級至最新的可用版本即可解決此問題。 在某些情況下，例如智慧型顯示器、機上盒或具有內嵌瀏覽引擎的其他裝置可能無法進行此類升級。

使用&#x200B;*SameSite=None*&#x200B;時，請依照下列步驟免除這些不相容的用戶端：

1. 升級至Adobe Experience ManagerAEM()Service Pack 6.5.7。

1. 重新啟AEM動後，請前往`/system/console/configMgr`並搜尋&#x200B;**Adobe花崗岩Token驗證處理常式**。 將&#x200B;**SameSite**&#x200B;值的值設定為&#x200B;**None**。

1. 您應看到一個新選項&#x200B;*User agents，可免除與samesite屬性*&#x200B;相同的屬性。 用與&#x200B;*SameSite=None*&#x200B;屬性不相容的使用者代理對應的規則運算式來填入此變數。
   >[!NOTE]
   >請參閱[SameSite=None:已知不相容的用戶端](https://www.chromium.org/updates/same-site/incompatible-clients)以取得詳細資訊。 對於Tizen播放器，請使用regex:`(.*)Tizen(.*)`。

1. 針對您的6.5.5及以上AEM版本例項註冊Tizen播放器，它應正常註冊並顯示內容。

## Tizen Player的批量布建{#bulk-provisioning-tizen-player}

>[!NOTE]
>在大量裝置的每個裝置的管理UI中手動輸入AEM您的伺服器位址，可能會很麻煩。 建議使用Samsung Remote Management(RMS)解決方案來部署和管理大型解決方案。 如需詳細資訊，請參閱[將Tizen Device註冊至Samsung遠端管理服務(RMS)](#enroll-tizen-device-rm)。

請依照下列步驟，大量布建應用程式，以在啟動時指AEM向您的作者例項：

1. 下載並安裝[Tizen Studio](https://developer.tizen.org/development/tizen-studio/download)。
1. 使用Tizen Studio開啟`wgt`檔案。
1. 開啟檔案`firmware-platform.js`並搜尋`DEFAULT_PREFERENCES`，並將伺服器URL變更為作AEM者URL並儲存。
1. 建立新的`wgt`檔案。

   >[!NOTE]
   >您可能需要建立或設定簽署憑證。

1. 使用RMS或URL啟動器部署此新的`wgt`檔案，當播放器啟動時，它應會自動指向您的伺服器，因此您不需要為每個裝置手動輸入它。

### 將Tizen Device註冊到Samsung Remote Management Service(RMS){#enroll-tizen-device-rms}

請依照下列步驟，將Tizen裝置註冊至Samsung Remote Management Service(RMS)，並遠端設定URL啟動程式：

>[!NOTE]
>驗證網路設定和顯示器。

1. 導航到&#x200B;**菜單** -> **網路** -> **伺服器網路設定** ，然後按&#x200B;**Enter**。

1. 導覽至伺服器位址並輸入MagicInfo URL存取權，然後按&#x200B;**Done**。

1. 視需要設定TLS。 導航到埠並從伺服器中選擇埠號，然後按一下&#x200B;**保存**。

1. 導覽至&#x200B;**Device**&#x200B;標籤，並檢查您剛配置的裝置。 找到設備後，按一下該複選框並選擇&#x200B;**批准**。

   >![影像](/help/user-guide/assets/tizen/rms-3.png)

1. 填寫所需資訊並選取裝置群組。 按一下&#x200B;**OK**&#x200B;以完成核准程式。

   >![影像](/help/user-guide/assets/tizen/rms-7.png)

1. 一旦設備獲得批准，它應該會出現在設備清單中。 按一下裝置方塊上的&#x200B;*資訊*&#x200B;按鈕，即&#x200B;**i**，如下圖所示。

   >![影像](/help/user-guide/assets/tizen/rms-6.png)

1. 將顯示設備資訊對話框。 選擇&#x200B;**設備資訊**&#x200B;頁籤，然後按一下&#x200B;**編輯**。

   >![影像](/help/user-guide/assets/tizen/rms-5.png)

1. 編輯設備選項並選擇&#x200B;**Setup**&#x200B;頁籤。 導覽至「**URL啟動器**」區段，然後輸入托管wgt的URL和`SSSP config file`以安裝`SSSP`應用程式，如下圖所示。

   ![影像](/help/user-guide/assets/tizen/rms-9.png)

1. 按一下&#x200B;**Save**&#x200B;以查看顯示屏上顯示的更改。


---
title: 蒂森播放器
description: 本頁面說明Tizen Player的安裝與運作方式。
feature: 管理螢幕、播放器
role: Administrator
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 1%

---


# 實作Tizen播放器{#tizen-player}

## 安裝Tizen Player {#installing-tizen-player}

請依照下列步驟，為AEM Screens實作Tizen Player:

1. 導覽至[AEM Screens Player下載](https://download.macromedia.com/screens/)頁面以下載Tizen Player。

1. 從本機電腦安裝Tizen播放器&#x200B;*(.zip)*&#x200B;檔案。

## 設定本地伺服器並解壓縮Zip檔案{#setting-local-server}

>[!NOTE]
> 解壓縮zip檔案，並透過`http server`使Tizen播放器可用。 （`http server`不是本地或Apache伺服器的必需項）。

請遵循下列步驟：

1. 將兩個擷取的檔案（例如`AEMScreensPlayer.wgt`和`sssp_config.xml`）複製到本機Apache Web伺服器的根目錄。

   >[!NOTE]
   >`AEMScreensPlayer.wgt`是實際的Tizen播放器應用程式，`sssp_config.xml`包含有關此映射的資訊，可幫助您在Tizen設備上安裝該映射。

1. 取得本機HTTP伺服器的IP或URL（若擷取至子資料夾，而非根資料夾，則取得步驟2中包含擷取檔案的資料夾路徑）

1. Tizen播放器會從本機伺服器下載安裝程式。

### 在Samsung設備{#config-updates}上配置更新

請依照下列Samsung裝置上的步驟，在裝置上完成AEM Screens播放器的安裝：

1. 導覽至您的Samsung裝置並開啟。

1. 從設備的遠程按一下&#x200B;**MENU**&#x200B;按鈕，然後從左側導航欄向下滾動到&#x200B;**System**。

1. 向下捲動並選取&#x200B;**透過**&#x200B;播放選項，並將其變更為&#x200B;**URL啟動器**選項。
   ![影像](/help/user-guide/assets/tizen/rms-2.png)

1. 設定URL啟動器後，從遠程按&#x200B;**Home**&#x200B;按鈕。

1. 導航到&#x200B;**URL啟動器設定**，然後輸入本地主機伺服器的IP地址，然後按一下&#x200B;**Done**。
   >[!NOTE]
   >Tizen播放器應能連線至http伺服器。

1. 現在，AEM Screens Player應會自動在您的Samsung裝置上安裝和啟動。

   >[!NOTE]
   >Tizen設備和`http`伺服器應能夠相互連接，即伺服器應可以到達Tizen播放器。


## 使用SameSite Cookie問題免除使用者代理{#exempting-user-agents}

>[!IMPORTANT]
>**本節適用於Adobe Experience Manager(AEM)6.5.5至AEM 6.5.7**
>有些瀏覽器引擎與AEM 6.5發出到AEM 6.7的登入Token中使用的&#x200B;*SameSite=None*&#x200B;屬性不相容。在大多數情況下，可將瀏覽器升級至最新可用版本，以解決此問題。 在某些情況下，例如使用智慧顯示器、機頂盒或具有嵌入式瀏覽引擎的其他設備可能無法進行此類升級。

使用&#x200B;*SameSite=None*&#x200B;時，請依照下列步驟免除這些不相容的用戶端：

1. 升級至Adobe Experience Manager(AEM)Service Pack 6.5.7。

1. AEM重新啟動後，前往`/system/console/configMgr`並搜尋&#x200B;**AdobeGranite代號驗證處理常式**。 將&#x200B;**SameSite**&#x200B;值的值設定為&#x200B;**None**。

1. 您應該會看到新選項&#x200B;*要免除samesite屬性*&#x200B;的使用者代理。 使用與&#x200B;*SameSite=None*&#x200B;屬性不相容的使用者代理對應的規則運算式填入此項目。
   >[!NOTE]
   >請參閱[SameSite=None:已知不相容客戶端](https://www.chromium.org/updates/same-site/incompatible-clients)以了解詳細資訊。 對於Tizen播放器，請使用規則運算式：`(.*)Tizen(.*)`。

1. 針對您的AEM 6.5.5及以上執行個體註冊Tizen播放器，且應正常註冊並顯示內容。

## Tizen Player的批量配置{#bulk-provisioning-tizen-player}

>[!NOTE]
>若要針對大量裝置，在每個裝置的管理員UI中手動輸入AEM伺服器位址，可能會是件枯燥乏味的工作。 建議使用Samsung遠程管理(RMS)解決方案來部署和管理大型解決方案。 有關詳細資訊，請參閱[將Tizen設備註冊到Samsung遠程管理服務(RMS)](#enroll-tizen-device-rm)。

請依照下列步驟，大量布建應用程式，以在啟動時指向您的AEM製作例項：

1. 下載並安裝[Tizen Studio](https://developer.tizen.org/development/tizen-studio/download)。
1. 使用Tizen studio開啟`wgt`檔案。
1. 開啟檔案`firmware-platform.js`並搜尋`DEFAULT_PREFERENCES`，並將伺服器URL變更為AEM製作URL並儲存。
1. 建立新的`wgt`檔案。

   >[!NOTE]
   >您可能需要建立或設定簽名證書。

1. 使用RMS或URL啟動器部署此新的`wgt`檔案，當播放器啟動時，應該自動指向伺服器，因此您不需要為每個設備手動輸入該檔案。

### 將Tizen設備註冊到Samsung遠程管理服務(RMS){#enroll-tizen-device-rms}

請按照以下步驟將Tizen設備註冊到Samsung遠程管理服務(RMS)，並遠程配置URL啟動器：

>[!NOTE]
>驗證網路設定和監視器。

1. 導航到&#x200B;**Menu** -> **Network** -> **Server Network Settings**，然後按&#x200B;**Enter**。

1. 導覽至伺服器位址，並輸入MagicInfo URL存取權，然後按&#x200B;**Done**。

1. 視需要設定TLS。 導航到埠並從伺服器中選擇埠號，然後按一下&#x200B;**Save**。

1. 導覽至&#x200B;**Device**&#x200B;標籤，並檢查您剛配置的裝置。 找到裝置後，按一下核取方塊並選取&#x200B;**核准**。

   >![影像](/help/user-guide/assets/tizen/rms-3.png)

1. 填寫所需資訊並選擇設備組。 按一下&#x200B;**OK**&#x200B;以完成核准程式。

   >![影像](/help/user-guide/assets/tizen/rms-7.png)

1. 設備獲得批准後，應會顯示在設備清單中。 按一下位於設備盒上的&#x200B;*資訊*&#x200B;按鈕，即&#x200B;**i**，如下圖所示。

   >![影像](/help/user-guide/assets/tizen/rms-6.png)

1. 設備資訊對話框隨即顯示。 選擇&#x200B;**Device Info**&#x200B;頁簽，然後按一下&#x200B;**Edit**。

   >![影像](/help/user-guide/assets/tizen/rms-5.png)

1. 編輯設備選項並選擇&#x200B;**Setup**&#x200B;頁簽。 導覽至「**URL啟動器**」區段，並輸入托管wgt和`SSSP config file`的URL以安裝`SSSP`應用程式，如下圖所示。

   ![影像](/help/user-guide/assets/tizen/rms-9.png)

1. 按一下&#x200B;**儲存**，變更才會顯示在顯示畫面上。


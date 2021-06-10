---
title: 蒂森播放器
description: 本頁面說明Tizen Player的安裝與運作方式。
feature: 管理螢幕、播放器
role: Administrator
level: Intermediate
source-git-commit: e955838d33cbe74719b237e568fb0bfd1a6844a2
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 0%

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

### 命名Tizen播放器{#name-tizen}

您可以指派好記的裝置名稱給您的Tizen播放器，借此將指派的裝置名稱傳送至Adobe Experience Manager(AEM)。 此功能不僅可讓您為Tizen播放器命名，也可讓您輕鬆指派適當內容。

請依照下列步驟，在Tizen播放器中設定名稱：

1. 按一下遠端上的功能表按鈕。
1. 導覽至&#x200B;**network** —> **裝置名稱** ，為播放器指派名稱。

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

## 遠程配置Tizen Player {#remote-provisioning}

遠程配置Tizen Player可讓您部署數以百計的Samsung Tizen顯示器，無需費神。 若要使用伺服器URL和大量註冊程式碼或其他參數來設定每個播放器，以及以Screens作為設定雲端模式和雲端代號的Cloud Service，這可避免繁瑣的手動操作。

此功能可讓您遠端配置Tizen播放器，並在必要時集中更新這些配置。 您只需要`HTTP`伺服器來托管Tizen應用程式`(wgt and xml file)`，並需要文本編輯器來使用適當的參數保存`config.json`。

請確定您已在Tizen Device（即「Home Button —> URL Launcher」設定）上配置URL啟動器地址。
在承載Tizen應用程式的`HTTP`伺服器上，將檔案`config.json`放置在與`wgt`檔案相同的位置。 檔案名必須為`config.json`。
Tizen播放器將安裝，在啟動時（每次重新啟動）將檢查並套用`config.json`檔案中的設定。

### JSON策略示例{#example-json}

```java
{
  "server":  "http://your-aem-instance.com:4502",
  "registrationKey": "AdobeRocks!!",
  "enableAdminUI": true,
  "enableOSD": true,
  "enableActivityUI": true
}
```

### 策略屬性和用途{#policy-attributes}

下表概括了策略及其功能。

>[!NOTE]
>原則設定會強制執行，且不會在播放器的管理員UI中手動覆寫。 要允許為特定策略進行手動播放器配置，請勿在策略配置中指定策略，例如，如果要允許為重新啟動計畫進行手動配置，則不要在策略配置中指定鍵`rebootSchedule`。 每次播放器重新載入時，都會讀取原則設定。

| **策略名稱** | **用途** |
|---|---|
| 伺服器 | Adobe Experience Manager(AEM)伺服器的URL。 |
| registrationKey | 用於使用預共用密鑰對設備進行批量註冊。 |
| 解析度 | 裝置的解析度。 |
| rebootSchedule | 重新啟動播放器的排程。 |
| enableAdminUI | 啟用管理員UI以在網站上設定裝置。 在完全設定後並在生產環境中設為false。 |
| enableOSD | 啟用通道切換器UI，讓使用者在裝置上切換通道。 在完全設定並在生產環境中設定為false時，請考慮將其設為false。 |
| enableActivityUI | 啟用以顯示活動的進度，例如下載和同步。 完全設定後在生產環境中啟用疑難排解功能並加以停用。 |
| cloudMode | 如果您希望Tizen播放器連線至screens as a cloud service，請設為true。 false以連線至AMS或onPrem AEM。 |
| cloudToken | 註冊Token，以根據Screens註冊為Cloud Service。 |


## 將Tizen設備註冊到Samsung遠程管理服務(RMS){#enroll-tizen-device-rms}

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


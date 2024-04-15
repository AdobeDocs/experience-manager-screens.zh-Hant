---
title: Tizen Player
description: 本頁說明Tizen Player的安裝和運作。
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '1208'
ht-degree: 1%

---

# 實作Tizen播放器 {#tizen-player}

## 安裝Tizen Player {#installing-tizen-player}

請依照下列步驟實作AEM Screens的Tizen Player：

1. 導覽至 [AEM Screens播放器下載](https://download.macromedia.com/screens/) 頁面，方便您下載Tizen Player。

1. 安裝Tizen播放器 *(.zip)* 來自本機電腦的檔案。

## 設定http伺服器 {#setting-local-server}

>[!NOTE]
> 解壓縮zip檔案，並透過 `http server`. (此 `http server` 不須為本機或Apache伺服器)。

請遵循下列步驟：

1. 複製兩個擷取的檔案，例如 `AEMScreensPlayer.wgt` 和 `sssp_config.xml` 至本機Apache Web Server的根目錄。

   >[!NOTE]
   >此 `AEMScreensPlayer.wgt`是實際的Tizen播放器應用程式和 `sssp_config.xml` 包含關於此對應的資訊，可協助您在Tizen裝置上安裝。

1. 取得本機HTTP伺服器的IP或URL （以及步驟2中包含已擷取檔案之資料夾的路徑，前提是已擷取至子資料夾，而非根資料夾）。

1. Tizen播放器會從本機伺服器下載安裝程式。

### 命名Tizen播放器 {#name-tizen}

您可以指派好記的裝置名稱給您的Tizen播放器，然後將指派的裝置名稱傳送給Adobe Experience Manager (AEM)。 此功能不僅可讓您為Tizen播放器命名，也可讓您輕鬆指派適當的內容。

>[!NOTE]
>您只能在註冊之前選擇播放器名稱。 播放器註冊後，播放器名稱就無法再變更。

請依照下列步驟，在Tizen播放器中設定名稱：

1. 按一下遠端上的功能表按鈕。
1. 瀏覽至 **網路** > **裝置名稱** 以便您指派名稱給播放器。

### 在Samsung裝置上設定更新 {#config-updates}

在Samsung裝置上依照下列步驟操作，就能在裝置上完成AEM Screens播放器的安裝：

1. 導覽至您的Samsung裝置並開啟。
1. 按一下 **選單** 按鈕從裝置的遠端向下捲動至 **系統** 從左側導覽列。
1. 向下捲動並選取 **透過播放** 選項並變更為 **URL啟動器** 選項。
   ![影像](/help/user-guide/assets/tizen/rms-2.png)
1. 設定URL啟動器時，按下 **首頁** 遙控器上的按鈕。
1. 導覽至 **URL啟動器設定** 並輸入localhost伺服器的IP位址，然後按一下 **完成**.

   >[!NOTE]
   >Tizen播放器應能連線至http伺服器。

1. AEM Screens Player會自動在您的Samsung裝置上安裝及啟動。

   >[!NOTE]
   >Tizen裝置和 `http` 伺服器應該能夠相互連線，也就是說，伺服器應該可以連線到Tizen播放器。


## 免除具有SameSite Cookie問題的使用者代理 {#exempting-user-agents}

>[!IMPORTANT]
>**本節適用於Adobe Experience Manager (AEM) 6.5.5至AEM 6.5.7**
>
>有些瀏覽器引擎與 *`SameSite=None`* 用於AEM 6.5.5核發至AEM 6.5.7的登入權杖中的屬性。通常，將瀏覽器升級至最新可用版本即可解決此問題。 有時可能無法進行這類升級，例如使用智慧型顯示器、機上盒或其他內嵌瀏覽引擎的裝置。

請依照下列步驟，在使用時，免除這些不相容的使用者端 *SameSite=None*：

1. 升級至Adobe Experience Manager (AEM) Service Pack 6.5.7。

1. AEM重新啟動後，前往 `/system/console/configMgr` 並搜尋 **AdobeGranite權杖驗證處理常式**. 設定值 **SameSite** 值至 **無**.

1. 您應該會看到新選項 *`User agents to be exempted from samesite attribute`*. 將對應至使用者代理程式（與）不相容的規則運算式填入此運算式 *SameSite=None* 屬性。

   >[!NOTE]
   >
   >另請參閱 [SameSite=None：已知的不相容使用者端](https://www.chromium.org/updates/same-site/incompatible-clients) 以取得更多詳細資料。 對於Tizen播放器，請使用規則運算式： `(.*)Tizen(.*)`.

1. 針對您的AEM 6.5.5及更高版本例項註冊Tizen播放器，它應該會正常註冊並顯示內容。

## 遠端布建Tizen播放器 {#remote-provisioning}

從遠端布建Tizen Player，讓您輕鬆部署成百上千的Samsung Tizen顯示器。 這樣可以避免手動使用伺服器URL和大量註冊代碼或其他引數來設定每個播放器。 此外，如果有AEM Screensas a Cloud Service，請設定雲端模式和雲端代號。

此功能可讓您在遠端設定Tizen播放器，並視需要集中更新這些設定。 您只需要使用 `HTTP` 用來裝載Tizen應用程式的伺服器 `(wgt and xml file)` 以及文字編輯器，以儲存 `config.json` 搭配適當的引數。

請確定您已在Tizen裝置上設定URL啟動器位址，也就是「首頁」按鈕> URL啟動器設定。
在 `HTTP` 裝載Tizen應用程式的伺服器，放置檔案 `config.json` 與位於相同位置 `wgt` 檔案。 檔案名稱必須是 `config.json`.
Tizen播放器會在啟動時（以及每次重新開機）安裝並套用設定， `config.json` 檔案。

### JSON原則範例 {#example-json}

```java
{
  "server":  "http://your-aem-instance.com:4502",
  "registrationKey": "AdobeRocks!!",
  "enableAdminUI": true,
  "enableOSD": true,
  "enableActivityUI": true
}
```

### 原則屬性和用途 {#policy-attributes}

下表摘要列出這些原則及其功能。

>[!NOTE]
>原則設定會嚴格執行，且不會在播放器的管理員UI中手動覆寫。 若要允許特定原則的手動播放器設定，請勿在原則設定中指定原則。
>例如，如果您要允許手動設定重新開機排程，請勿指定索引鍵 `rebootSchedule` 在原則設定中。 每次播放器重新載入時都會讀取原則設定。

| **原則名稱** | **用途** |
|---|---|
| 伺服器 | Adobe Experience Manager (AEM)伺服器的URL。 |
| 註冊金鑰 | 用於使用預先共用金鑰的大量裝置註冊。 |
| 解析度 | 裝置的解析度。 |
| rebootSchedule | 重新啟動播放器的排程。 |
| enableAdminUI | 啟用管理員UI來設定站台上的裝置。 在完全設定並投入生產後，設為false。 |
| enableOSD | 啟用頻道切換器UI，讓使用者在裝置上切換頻道。 在完全設定並投入生產後，請考慮將設為false 。 |
| enableactivityui | 啟用，以便顯示下載和同步等活動的進度。 啟用以進行疑難排解，並在完全設定後停用。 |
| cloudMode | 如果您希望Tizen播放器as a Cloud Service連線至Screens，請設為true。 設為false可連線至AMS或內部部署AEM。 |
| cloudToken | 註冊Token以針對Screensas a Cloud Service註冊。 |


## 正在將Tizen裝置註冊到Samsung遠端管理服務(RMS) {#enroll-tizen-device-rms}

請依照下列步驟，將Tizen裝置註冊到Samsung遠端管理服務(RMS)，並從遠端設定URL啟動器：

>[!NOTE]
>驗證網路設定和監視器。

1. 瀏覽至 **選單** -> **網路** -> **伺服器網路設定** 然後按下 **輸入**.

1. 導覽至「伺服器位址」，並輸入MagicInfo URL存取權，然後按下 **完成**.

1. 設定TLS （如有必要）。 瀏覽至連線埠，並從伺服器選取連線埠號碼，然後選取 **儲存**.

1. 導覽至 **裝置** 標籤並檢查您設定的裝置。 找到裝置時，選取核取方塊，然後選取 **核准**.

   >![影像](/help/user-guide/assets/tizen/rms-3.png)

1. 填寫所需資訊，然後選取裝置群組。 選取 **確定**.

   >![影像](/help/user-guide/assets/tizen/rms-7.png)

1. 裝置獲得核准後，就會出現在「裝置清單」上。 選取 *資訊* （位於裝置方塊上），如下所示。

   >![影像](/help/user-guide/assets/tizen/rms-6.png)

1. 裝置資訊對話方塊隨即顯示。 選取 **裝置資訊** 標籤並選取 **編輯**.

   >![影像](/help/user-guide/assets/tizen/rms-5.png)

1. 編輯裝置選項並選取 **設定** 標籤。 瀏覽至 **URL啟動器** 區段，並輸入託管wgt的URL和 `SSSP config file` 以便您安裝 `SSSP` 應用程式，如下圖所示。

   ![影像](/help/user-guide/assets/tizen/rms-9.png)

1. 選取「**儲存**」。

### 使用Screens遙控器 {#using-remote-control}

AEM Screens提供遠端控制功能。 若要進一步瞭解此功能，請前往這裡： [熒幕遙控器](implementing-remote-control.md)

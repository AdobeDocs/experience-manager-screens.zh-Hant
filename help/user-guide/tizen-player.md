---
title: Tizen播放器
description: 瞭解Tizen播放器的安裝和運作方式。
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 1%

---

# 實作Tizen播放器 {#tizen-player}

## 安裝Tizen播放器 {#installing-tizen-player}

請依照下列步驟，實作AEM Screens的Tizen播放器：

1. 瀏覽至[AEM Screens播放器下載](https://download.macromedia.com/screens/)頁面，以便下載Tizen播放器。

1. 從您的本機電腦安裝Tizen播放器&#x200B;*(.zip)*&#x200B;檔案。

## 設定http伺服器 {#setting-local-server}

>[!NOTE]
> 解壓縮zip檔案，並透過`http server`提供Tizen播放器。 （`http server`不需要是本機或Apache伺服器）。

請遵循下列步驟：

1. 將兩個擷取的檔案（例如`AEMScreensPlayer.wgt`和`sssp_config.xml`）複製到本機Apache Web伺服器的根目錄。

   >[!NOTE]
   >`AEMScreensPlayer.wgt`是實際的Tizen播放器應用程式，`sssp_config.xml`包含此對應的相關資訊，可協助您將其安裝在Tizen裝置上。

1. 取得本機HTTP伺服器的IP或URL （以及步驟2中包含已擷取檔案之資料夾的路徑，前提是已擷取至子資料夾，而非根資料夾）。

1. Tizen播放器會從本機伺服器下載安裝程式。

### 命名Tizen播放器 {#name-tizen}

您可以為您的Tizen播放器指派好記的裝置名稱，然後將指派的裝置名稱傳送至Adobe Experience Manager (AEM)。 此功能不僅可讓您為Tizen播放器命名，也可讓您輕鬆指派適當的內容。

>[!NOTE]
>您只能在註冊之前選擇播放器名稱。 播放器註冊後，播放器名稱就無法再變更。

請依照下列步驟，在Tizen播放器中設定名稱：

1. 按一下遠端上的功能表按鈕。
1. 導覽至&#x200B;**網路** > **裝置名稱**，讓您可以將名稱指派給播放器。

### 在Samsung裝置上設定更新 {#config-updates}

在Samsung裝置上依照下列步驟操作，就能在裝置上完成AEM Screens Player的安裝：

1. 導覽至您的Samsung裝置並開啟。
1. 從裝置的遠端按一下&#x200B;**功能表**&#x200B;按鈕，然後從左側導覽列向下捲動至&#x200B;**系統**。
1. 向下捲動，然後按一下&#x200B;**透過**&#x200B;播放選項，並將其變更為&#x200B;**URL啟動器**選項。
   ![影像](/help/user-guide/assets/tizen/rms-2.png)
1. 設定URL啟動器時，從遠端按下&#x200B;**Home**&#x200B;按鈕。
1. 導覽至&#x200B;**URL啟動器設定**，並輸入您的本機主機伺服器的IP位址，然後按一下&#x200B;**完成**。

   >[!NOTE]
   >Tizen播放器應能連線至HTTP伺服器。

1. AEM Screens Player會自動在您的Samsung裝置上安裝及啟動。

   >[!NOTE]
   >Tizen裝置和`http`伺服器都應該能夠相互連線，也就是說，伺服器應該可以連線到Tizen播放器。


## 免除具有SameSite Cookie問題的使用者代理 {#exempting-user-agents}

>[!IMPORTANT]
>**本節適用於Adobe Experience Manager (AEM) 6.5.5至AEM 6.5.7**
>
>有些瀏覽器引擎與AEM 6.5.5核發至AEM 6.5.7的登入權杖中使用的&#x200B;*`SameSite=None`*&#x200B;屬性不相容。通常，將瀏覽器升級至最新可用版本即可解決此問題。 有時可能無法進行這類升級，例如使用智慧型顯示器、機上盒或其他內嵌瀏覽引擎的裝置。

請依照下列步驟，在使用&#x200B;*SameSite=None*&#x200B;時免除這些不相容的使用者端：

1. 升級至Adobe Experience Manager (AEM) Service Pack 6.5.7。

1. AEM重新啟動後，移至`/system/console/configMgr`並搜尋&#x200B;**Adobe Granite權杖驗證處理常式**。 將&#x200B;**SameSite**&#x200B;的值設定為&#x200B;**無**。

1. 您應該會看到新選項&#x200B;*`User agents to be exempted from samesite attribute`*。 將對應至使用者代理程式（不相容於&#x200B;*SameSite=None*&#x200B;屬性）的規則運算式填入此選項。

   >[!NOTE]
   >
   >如需詳細資訊，請參閱[SameSite=None：已知不相容的使用者端](https://www.chromium.org/updates/same-site/incompatible-clients)。 對於Tizen播放器，請使用規則運算式： `(.*)Tizen(.*)`。

1. 針對您的AEM 6.5.5及更高版本例項註冊Tizen播放器，它應該會正常註冊並顯示內容。

## 從遠端布建Tizen播放器 {#remote-provisioning}

從遠端布建Tizen播放器，讓您輕鬆部署成百上千的Samsung Tizen顯示器。 這樣可以避免手動使用伺服器URL和大量註冊代碼或其他引數來設定每個播放器。 如果有AEM Screens as a Cloud Service，則設定雲端模式和雲端代號。

此功能可讓您在遠端設定Tizen播放器，並視需要集中更新這些設定。 您只需要用來裝載Tizen應用程式`(wgt and xml file)`的`HTTP`伺服器，以及用來以適當的引數儲存`config.json`的文字編輯器。

請確定您已在Tizen裝置上設定URL啟動器位址。 按一下「首頁」按鈕> URL啟動器設定。
在裝載Tizen應用程式的`HTTP`伺服器上，將檔案`config.json`放在與`wgt`檔案相同的位置。 檔案名稱必須是`config.json`。
Tizen播放器會在啟動時（以及每次重新開機）安裝並套用`config.json`檔案中的設定。

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
>播放器的管理員UI原則設定會嚴格強制執行，且不會手動覆寫。 若要允許特定原則的手動播放器設定，請勿在原則設定中指定原則。
>>例如，如果您要允許手動設定重新開機排程，請勿在原則設定中指定索引鍵`rebootSchedule`。 每次播放器重新載入時都會讀取原則設定。

| **原則名稱** | **用途** |
|---|---|
| 伺服器 | Adobe Experience Manager (AEM)伺服器的URL。 |
| 註冊金鑰 | 用於使用預先共用金鑰的大量裝置註冊。 |
| 解析度 | 裝置的解析度。 |
| rebootSchedule | 重新啟動播放器的排程。 |
| enableAdminUI | 啟用管理員UI來設定站台上的裝置。 在完全設定並投入生產後，設為false。 |
| enableOSD | 啟用頻道切換器UI，讓使用者在裝置上切換頻道。 在完全設定並在生產環境中後，請考慮將其設為false 。 |
| enableactivityui | 啟用，以便顯示活動的進度，例如下載和同步。 啟用以進行疑難排解，並在完全設定後停用。 |
| cloudMode | 如果您希望Tizen播放器連線至Screens as a Cloud Service，請設為true。 設為false可連線至AMS或內部部署AEM。 |
| cloudToken | 註冊Token以註冊Screens as a Cloud Service。 |


## 正在將Tizen裝置註冊到Samsung遠端管理服務(RMS) {#enroll-tizen-device-rms}

請依照下列步驟，將Tizen裝置註冊到Samsung遠端管理服務(RMS)，並從遠端設定URL啟動器：

>[!NOTE]
>驗證網路設定和監視器。

1. 瀏覽至&#x200B;**功能表** -> **網路** -> **伺服器網路設定**，然後按&#x200B;**Enter**。

1. 導覽至伺服器位址，並輸入MagicInfo URL存取，然後按&#x200B;**完成**。

1. 設定TLS （如有必要）。 瀏覽至連線埠，然後按一下伺服器的連線埠號碼，再按一下[儲存]。****

1. 導覽至&#x200B;**裝置**&#x200B;標籤，然後檢查您設定的裝置。 找到裝置時，按一下核取方塊，然後按一下[核准]。****

   >![影像](/help/user-guide/assets/tizen/rms-3.png)

1. 填寫必要資訊，然後按一下裝置群組。 按一下&#x200B;**「確定」**。

   >![影像](/help/user-guide/assets/tizen/rms-7.png)

1. 裝置獲得核准後，就會出現在「裝置清單」上。 按一下裝置方塊上的&#x200B;*資訊*，如下所示。

   >![影像](/help/user-guide/assets/tizen/rms-6.png)

1. 裝置資訊對話方塊隨即顯示。 按一下&#x200B;**裝置資訊**&#x200B;索引標籤，然後按一下&#x200B;**編輯**。

   >![影像](/help/user-guide/assets/tizen/rms-5.png)

1. 編輯裝置選項，然後按一下&#x200B;**設定**&#x200B;標籤。 導覽至&#x200B;**URL啟動器**&#x200B;區段，然後輸入主控wgt的URL和`SSSP config file`，以便您可以安裝`SSSP`應用程式，如下圖所示。

   ![影像](/help/user-guide/assets/tizen/rms-9.png)

1. 按一下「**儲存**」。

### 使用Screens遠端控制 {#using-remote-control}

AEM Screens提供遠端控制功能。 若要深入瞭解此功能，請前往下列位置： [Screens遙控器](implementing-remote-control.md)

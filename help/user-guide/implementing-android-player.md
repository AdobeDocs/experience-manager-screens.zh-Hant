---
title: 實作Android&amp；trade；播放器
description: 瞭解Android&amp；trade； Watchdog的實作，此解決方案可讓您從當機狀態復原Android&amp；trade；播放器。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: 06082edf3dadbaea1cea142ff624e83bc6045dfd
workflow-type: tm+mt
source-wordcount: '1471'
ht-degree: 0%

---

# 實作Android™ Player {#implementing-android-player}

本節說明如何設定Android™播放器。 它提供設定檔和可用選項的資訊，以及開發和測試使用哪些設定的建議。

此外，**Watchdog**&#x200B;是讓播放器從當機復原的解決方案。 應用程式必須向看門狗服務註冊自己，然後定期傳送訊息給處於使用狀態的服務。 如果監視程式服務未在規定的時間內收到保持連線訊息，則服務會嘗試重新啟動裝置。 如此可完全復原（如果它有足夠的許可權）或重新啟動應用程式。

## 安裝Android™ Player {#installing-android-player}

若要實作適用於AEM Screens的Android™ Player，請安裝適用於AEM Screens的Android™ Player。

造訪&#x200B;[**AEM 6.5播放器下載**](https://download.macromedia.com/screens/)頁面。

### 為AEM Screens 6.5.5 Service Pack設定環境 {#fp-environment-setup}

>[!NOTE]
>如果您使用Android 6.5.5 Service Pack，請為AEM Screens™播放器設定環境。

在所有AEM作者和發佈執行個體上，將登入權杖Cookie **的** SameSite屬性從&#x200B;**Lax**&#x200B;設定為&#x200B;**None** (從&#x200B;**Adobe Experience Manager Web主控台設定**)。

請遵循下列步驟：

1. 使用`http://localhost:4502/system/console/configMgr`導覽至&#x200B;**Adobe Experience Manager Web主控台組態**。

1. 搜尋&#x200B;*AdobeGranite權杖驗證處理常式*。

1. 將登入權杖Cookie **的** SameSite屬性從&#x200B;**Lax**&#x200B;設定為&#x200B;**None**。
   ![影像](/help/user-guide/assets/granite-updates.png)

1. 按一下「**儲存**」。


### 臨機方法 {#ad-hoc-method}

Ad-Hoc方法可讓您安裝最新的Android™ Player (*.exe*)。 造訪&#x200B;[**AEM 6.5播放器下載**](https://download.macromedia.com/screens/)頁面。

下載應用程式後，請依照播放器上的步驟完成隨選安裝：

1. 長按左上角以開啟「管理」面板。
1. 從左側動作功能表瀏覽至&#x200B;**組態**，並輸入您要連線的AEM執行個體的位置（位址），然後按一下&#x200B;**儲存**。

1. 從左側動作功能表瀏覽至&#x200B;**裝置** **註冊**&#x200B;連結，以便檢查裝置註冊程式的狀態。

>[!NOTE]
>
>如果&#x200B;**狀態**&#x200B;是&#x200B;**已註冊**，您會看到已填入&#x200B;**裝置識別碼**&#x200B;欄位。
>
>如果&#x200B;**狀態**&#x200B;是&#x200B;**未註冊**，您可以使用&#x200B;**權杖**&#x200B;來註冊裝置。

## 實作Android™ Watchdog {#implementing-android-watchdog}

由於Android™的架構，重新啟動裝置需要應用程式具有系統許可權。 使用製造商的簽署金鑰簽署應用程式，否則監視程式可以重新啟動播放器應用程式，而不會重新啟動裝置。

### Android的招牌™ `apks`使用製造商金鑰 {#signage-of-android-apks-using-manufacturer-keys}

若要存取Android的某些授權API™例如&#x200B;*PowerManager*&#x200B;或&#x200B;*HDMIControlServices*，請使用製造商的金鑰簽署Android™ `apk`。

>[!CAUTION]
>
>先決條件：
>
>您應先安裝Android™ SDK，再執行下列步驟。

請依照下列步驟，使用製造商的金鑰簽署Android™ apk：

1. 從Google Play或[AEM Screens播放器下載](https://download.macromedia.com/screens/)頁面下載App
1. 向製造商取得平台金鑰，以便取得&#x200B;*pk8*&#x200B;和&#x200B;*pem*&#x200B;檔案

1. 使用尋找`~/Library/Android/sdk/build-tools -name "apksigner"`在Android™ SDK中尋找`apksigner`工具
1. `<pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk`
1. 尋找Android™ SDK中zip對齊工具的路徑
1. `<pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk`
1. 使用adb安裝將&#x200B;***aemscreensaligned.apk***&#x200B;安裝到裝置

## 瞭解Android™監視程式服務 {#android-watchdog-services}

跨Android™監視程式服務是使用&#x200B;*AlarmManager*&#x200B;實作為Cordova外掛程式。

下圖顯示監視程式服務的實作：

![chlimage_1-31](assets/chlimage_1-31.png)

**1. 初始化** — 在初始化Cordova外掛程式時，會檢查許可權以檢視您是否擁有系統許可權，以及重新開機許可權。 如果符合這兩個條件，就會建立擱置的重新開機目的，否則就會建立擱置的重新開機目的（根據應用程式的啟動活動）。

**2. 保持連線計時器** — 保持連線計時器是用來每15秒觸發一次事件。 在該事件中，請取消現有的擱置意圖（重新開機或重新啟動應用程式），並在未來的60秒內，登入新的擱置意圖（基本上會延遲重新開機）。

>[!NOTE]
>
>在Android™中，*AlarmManager*&#x200B;是用來登入即使應用程式當機且其警報傳送與API 19 (Kitkat)不精確也能執行的&#x200B;*pendingIntents*。 在計時器的間隔與&#x200B;*AlarmManager的* *pendingIntent的*&#x200B;警報之間保留一些間距。

**3。 應用程式當機** — 如果當機，將不再重設向AlarmManager登入的pendingIntent for Reboot。 因此，它會執行重新開機或重新啟動應用程式（取決於Cordova外掛程式初始化時可用的許可權）。

## 大量布建Android™ Player {#bulk-provision-android-player}

大量推出Android™播放器時，需要布建播放器以指向AEM執行個體，並設定其他屬性，而不需在管理員UI中手動輸入。

>[!NOTE]
>Android™播放器42.0.372提供此功能。

請依照下列步驟，在Android™播放器中允許大量布建：

1. 建立名稱為`player-config.default.json`的組態JSON檔案。
請參閱[範例JSON原則](#example-json)和說明各種[原則屬性](#policy-attributes)之使用的表格。

1. 使用MDM、ADB或Android™ Studio檔案總管將此原則JSON檔案拖放到Android™裝置上的&#x200B;*sdcard*&#x200B;資料夾。

1. 部署檔案時，請使用MDM安裝播放器應用程式。

1. 播放器應用程式啟動時，會讀取此設定檔，並指向適用的AEM伺服器（在其中註冊並接著控制）。

   >[!NOTE]
   >第一次啟動應用程式時，這個檔案是&#x200B;*唯讀*，無法用於後續設定。 如果在卸除設定檔之前啟動播放器，只需在裝置上解除安裝並重新安裝應用程式即可。

### 原則屬性 {#policy-attributes}

下表摘要列出原則JSON範例作為參考的原則：

| **原則名稱** | **用途** |
|---|---|
| *server* | Adobe Experience Manager伺服器的URL。 |
| *解析度* | 裝置的解析度。 |
| *rebootSchedule* | 重新開機的排程適用於所有平台。 |
| *enableAdminUI* | 啟用管理員UI來設定站台上的裝置。 設定為&#x200B;*false*，前提是它已完全設定並投入生產。 |
| *啟用OSD* | 啟用頻道切換器UI，讓使用者在裝置上切換頻道。 請考慮在完全設定後和生產中將其設定為&#x200B;*false*。 |
| *enableActivityUI* | 如果想要顯示下載和同步等活動的進度，請啟用此選項。 啟用以進行疑難排解，並在完全設定後停用。 |
| *enableNativeVideo* | 如果您想要使用原生硬體加速來播放視訊(僅限Android™)，請啟用此選項。 |

### JSON原則範例 {#example-json}

```java
{
  "server": "https://author-screensdemo.adobecqms.net",
"device": "",
"user": "",
"password": "",
"resolution": "auto",
"rebootSchedule": "at 4:00 am",
"maxNumberOfLogFilesToKeep": 10,
"logLevel": 3,
"enableAdminUI": true,
"enableOSD": true,
"enableActivityUI": false,
"enableNativeVideo": false,
"enableAutoScreenshot": false,
"cloudMode": false,
"cloudUrl": "https://screens.adobeioruntime.net",
"cloudToken": "",
"enableDeveloperMode": true
}
```

>[!NOTE]
>不論是否插入實際的`*sdcard*`，所有Android™裝置都有`*sdcard*`資料夾。 部署時，此檔案會與「下載」資料夾位於相同層級。 某些MDM （例如Samsung Knox）可能會看到此&#x200B;*sdcard*&#x200B;資料夾位置為&#x200B;*內部儲存空間*。

## 使用企業行動管理大量布建Android™ Player {#bulk-provisioning}

大量部署Android™播放器時，手動向AEM註冊每個播放器會變得繁瑣起來。 使用EMM （企業行動管理）解決方案，例如[`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、MobileIron或Samsung Knox，以便從遠端布建和管理您的部署。 AEM Screens Android™播放器支援業界標準的EMM AppConfig，以允許遠端布建。

## 命名Android™ Player {#name-android}

您可以指派好記的裝置名稱給您的Android™播放器，然後將指派的裝置名稱傳送給AEM (Adobe Experience Manager)。 此功能不僅可讓您為Android™播放器命名，也可讓您輕鬆指派適當內容。

>[!NOTE]
>您只能在註冊之前選擇播放器名稱。 播放器註冊後，播放器名稱就無法再變更。

請依照下列步驟，在Android™播放器中設定名稱：

1. 瀏覽至&#x200B;**設定** > **關於裝置**
1. 編輯並設定您的裝置名稱，以命名您的Android™播放器

### 使用Enterprise Mobility Management實作Android™ Player的大量布建 {#implementation}

請依照下列步驟，在Android™ Player中允許大量布建：

1. 確認您的Android™裝置支援Google Play服務。
1. 使用您最愛的支援AppConfig的EMM解決方案註冊您的Android™播放器裝置。
1. 登入您的EMM主控台，並從Google Play提取AEM Screens Player應用程式。
1. 按一下Managed組態或相關選項。
1. 您現在應該會看到可設定的播放器選項清單，例如伺服器和大量註冊代碼。
1. 設定這些引數、儲存原則，並將其部署至裝置。

   >[!NOTE]
   >裝置應該會同時接收應用程式和設定。 它應該以選取的設定指向正確的AEM伺服器。 如果您選擇設定大量註冊程式碼，並使其與AEM中的設定相同，則播放器應能自動註冊自身。 如果您設定了預設顯示，它也可以下載並顯示某些預設內容（稍後可視您的便利性進行變更）。

此外，您也應該向EMM供應商洽詢AppConfig支援。 最受歡迎的[`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、[`Mobile Iron`](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)、[`SOTI`](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)、[`BlackBerry&reg; UEM`](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)、[`IBM&reg; Maas360`](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)和[`Samsung Knox`](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)等支援此產業標準。

### 使用Screens遠端控制 {#using-remote-control}

AEM Screens提供遠端控制功能。 若要深入瞭解此功能，請前往下列位置： [Screens遙控器](implementing-remote-control.md)

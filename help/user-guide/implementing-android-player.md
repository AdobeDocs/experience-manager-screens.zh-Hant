---
title: 實作Android&trade；播放器
description: 瞭解Android&trade； Watchdog的實作，此解決方案可讓您將Android&trade；播放器從當機中復原。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '1462'
ht-degree: 0%

---

# 實作Android™ Player {#implementing-android-player}

本節說明如何設定Android™播放器。 它提供設定檔和可用選項的資訊，以及開發和測試使用哪些設定的建議。

另外， **看門狗** 是讓播放器從當機復原的解決方案。 應用程式必須向看門狗服務註冊自己，然後定期傳送訊息給處於使用狀態的服務。 如果watchdog服務未在規定的時間內收到保持連線訊息，服務會嘗試重新啟動裝置以進行乾淨的復原（如果它有足夠的許可權）或重新啟動應用程式。

## 安裝Android™ Player {#installing-android-player}

若要實作適用於AEM Screens的Android™ Player，請安裝適用於AEM Screens的Android™ Player。

造訪 [**AEM 6.5播放器下載**](https://download.macromedia.com/screens/) 頁面。

### 為AEM Screens 6.5.5 Service Pack設定環境 {#fp-environment-setup}

>[!NOTE]
>如果您使用AEM Screens 6.5.5 Service Pack，請為Android™播放器設定環境。

設定 **登入權杖Cookie的SameSite屬性** 從 **鬆散** 至 **無** 從 **Adobe Experience Manager Web主控台設定** 在所有AEM作者和發佈執行個體上。

請遵循下列步驟：

1. 瀏覽至 **Adobe Experience Manager Web主控台設定** 使用 `http://localhost:4502/system/console/configMgr`.

1. 搜尋 *AdobeGranite權杖驗證處理常式*.

1. 設定 **登入權杖Cookie的SameSite屬性** 從 **鬆散** 至 **無**.
   ![影像](/help/user-guide/assets/granite-updates.png)

1. 按一下「**儲存**」。


### 臨機方法 {#ad-hoc-method}

臨機操作方法可讓您安裝最新的Android™播放器(*.exe*)。 造訪 [**AEM 6.5播放器下載**](https://download.macromedia.com/screens/) 頁面。

下載應用程式後，請依照播放器上的步驟完成隨選安裝：

1. 長按左上角以開啟「管理」面板。
1. 瀏覽至 **設定** 從左側動作選單中輸入您要連線的AEM執行個體的位置（位址），然後按一下 **儲存**.

1. 導覽至 **裝置** **註冊** 從左側動作功能表連結，以便您檢視裝置註冊程式的狀態。

>[!NOTE]
>
>如果 **狀態** 是 **已註冊**，您會看到 **裝置ID** 欄位會填入。
>
>如果 **狀態** 是 **未註冊**，您可以使用 **Token** 以註冊裝置。

## 實作Android™ Watchdog {#implementing-android-watchdog}

由於Android™的架構，重新啟動裝置需要應用程式具有系統許可權。 要執行此操作，請使用製造商的簽署金鑰簽署應用程式，否則監視器會重新啟動播放器應用程式，而不會重新啟動裝置。

### Android™的招牌 `apks` 使用製造商金鑰 {#signage-of-android-apks-using-manufacturer-keys}

若要存取Android的某些特殊許可權API™例如 *PowerManager* 或 *Hdmicontrolservices*，簽署Android™ `apk` 使用製造商的金鑰。

>[!CAUTION]
>
>先決條件：
>
>您應先安裝Android™ SDK，再執行下列步驟。

請依照下列步驟，使用製造商的金鑰簽署Android™應用程式：

1. 從Google Play或下載應用程式 [AEM Screens播放器下載](https://download.macromedia.com/screens/) 頁面
1. 向製造商取得平台金鑰，以便您取得 *pk8* 和 *pem* 檔案

1. 找到 `apksigner` Android™ sdk中的工具（使用尋找） `~/Library/Android/sdk/build-tools -name "apksigner"`
1. `<pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk`
1. 尋找Android™ sdk中zip對齊工具的路徑
1. `<pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk`
1. 安裝 ***aemscreensaligned.apk*** 在裝置上使用adb安裝

## 瞭解Android™ Watchdog服務 {#android-watchdog-services}

跨Android看門狗服務是使用實作為Cordova外掛程式 *AlarmManager*.

下圖顯示監視程式服務的實作：

![chlimage_1-31](assets/chlimage_1-31.png)

**1. 初始化**  — 初始化Cordova外掛程式時，系統會檢查許可權以檢視您是否擁有系統許可權，進而檢查是否擁有重新開機許可權。 如果符合這兩個條件，就會建立擱置的重新開機目的，否則就會建立擱置的重新開機目的（根據應用程式的啟動活動）。

**2. 保持作用中計時器**  — 保持連線計時器可用來每15秒觸發一次事件。 在該事件中，請取消現有的擱置意圖（重新開機或重新啟動應用程式），並在未來的60秒內，登入新的擱置意圖（基本上會延遲重新開機）。

>[!NOTE]
>
>在Android™中， *AlarmManager* 用於註冊 *pendingIntents* 即使應用程式當機且其警報傳送與API 19 (Kitkat)不準確，仍可執行。 在計時器的間隔與 *警報管理員的* *pendingIntent的* 警報。

**3. 應用程式當機**  — 如果發生當機，將不再重設向AlarmManager註冊的pendingIntent for Reboot。 因此，它會執行重新開機或重新啟動應用程式（取決於Cordova外掛程式初始化時可用的許可權）。

## 大量布建Android™ Player {#bulk-provision-android-player}

大量推出Android™播放器時，需要布建播放器以指向AEM執行個體並設定其他屬性，而不需在管理員UI中手動輸入那些屬性。

>[!NOTE]
>Android™播放器42.0.372提供此功能。

請依照下列步驟，在Android™播放器中允許大量布建：

1. 以名稱建立設定JSON檔案 `player-config.default.json`.
檢視 [JSON原則範例](#example-json) 以及說明各種 [原則屬性](#policy-attributes).

1. 使用MDM、ADB或Android™ Studio檔案總管將此原則JSON檔案拖放至 *sdcard* Android™裝置上的資料夾。

1. 部署檔案時，請使用MDM安裝播放器應用程式。

1. 播放器應用程式啟動時，會讀取此設定檔，並指向適用的AEM伺服器（在其中註冊並接著控制）。

   >[!NOTE]
   >此檔案為 *唯讀* 首次啟動應用程式，且無法用於後續設定時。 如果在卸除設定檔之前啟動播放器，只需在裝置上解除安裝並重新安裝應用程式即可。

### 原則屬性 {#policy-attributes}

下表摘要列出原則JSON範例作為參考的原則：

| **原則名稱** | **用途** |
|---|---|
| *server* | Adobe Experience Manager伺服器的URL。 |
| *解析度* | 裝置的解析度。 |
| *rebootSchedule* | 重新開機的排程適用於所有平台。 |
| *enableAdminUI* | 啟用管理員UI來設定站台上的裝置。 將設為 *false* 完成設定並投入生產後。 |
| *enableOSD* | 啟用頻道切換器UI，讓使用者在裝置上切換頻道。 考慮將設為 *false* 完成設定並投入生產後。 |
| *enableactivityui* | 如果想要顯示下載和同步等活動的進度，請啟用此選項。 啟用以進行疑難排解，並在完全設定後停用。 |
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
>所有Android™裝置都有 `*sdcard*` 資料夾(無論是 `*sdcard*` 是否插入。 部署時，此檔案會與「下載」資料夾位於相同層級。 有些MDM （例如Samsung Knox）可能會看到這種情況 *sdcard* 資料夾位置為 *內部儲存*.

## 使用企業行動性管理大量布建Android™ Player {#bulk-provisioning}

大量部署Android™播放器時，手動向AEM註冊每個播放器會變得繁瑣起來。 強烈建議使用EMM （企業行動管理）解決方案，例如 [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、 MobileIron或Samsung Knox可從遠端布建及管理您的部署。 AEM Screens Android™播放器支援業界標準的EMM AppConfig，以便允許遠端布建。

## 命名Android™ Player {#name-android}

您可以指派好記的裝置名稱給您的Android™播放器，然後將指派的裝置名稱傳送給AEM (Adobe Experience Manager)。 此功能不僅可讓您為Android™播放器命名，也可讓您輕鬆指派適當的內容。

>[!NOTE]
>您只能在註冊之前選擇播放器名稱。 播放器註冊後，播放器名稱就無法再變更。

請依照下列步驟，在Android™播放器中設定名稱：

1. 瀏覽至 **設定** > **關於裝置**
1. 編輯並設定您的裝置名稱，以命名您的Android™播放器

### 使用Enterprise Mobility Management實作Android™ Player的大量布建 {#implementation}

請依照下列步驟，在Android™ Player中允許大量布建：

1. 確認您的Android™裝置支援Google Play服務。
1. 使用您最愛的支援AppConfig的EMM解決方案註冊您的Android™播放器裝置。
1. 登入您的EMM主控台，並從Google Play提取AEM Screens Player應用程式。
1. 選取Managed組態或相關選項。
1. 您現在應該會看到可設定的播放器選項清單，例如伺服器和大量註冊代碼。
1. 設定這些引數、儲存原則，並將其部署至裝置。

   >[!NOTE]
   >裝置應該會連同設定一起接收應用程式，並以選取的設定指向正確的AEM伺服器。 如果您選擇設定大量註冊程式碼，並使其與AEM中的設定相同，播放器應該能夠自動註冊自身。 如果您設定了預設顯示，它也可以下載並顯示某些預設內容（稍後可視您的便利性進行變更）。

此外，您也應該向EMM供應商洽詢AppConfig支援。 最受歡迎的內容，例如 [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)， [`Mobile Iron`](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)， [`SOTI`](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)， [`BlackBerry&reg; UEM`](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)， [`IBM&reg; Maas360`](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)、和 [`Samsung Knox`](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) 其他支援此產業標準。

### 使用Screens遙控器 {#using-remote-control}

AEM Screens提供遠端控制功能。 若要進一步瞭解此功能，請前往這裡： [熒幕遙控器](implementing-remote-control.md)

---
title: 實作Android Player
seo-title: Android Player的實作
description: 請依照本頁瞭解Android Watchdog的實作，此解決方案可從當機中復原播放器。
seo-description: 請依照本頁瞭解Android Watchdog的實作，此解決方案可從當機中復原播放器。
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: Administering Screens, Android Player
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 6978d9d13f2b7f723812561554fdb0a606ddb4fc
workflow-type: tm+mt
source-wordcount: '1441'
ht-degree: 0%

---


# 實作Android Player {#implementing-android-player}

本節說明如何設定Android播放器。 它提供設定檔、可用選項和建議的資訊，說明要用於開發和測試的設定。

此外，**Watchdog**&#x200B;是從當機中恢復播放器的解決方案。 應用程式需要向監視程式服務註冊，然後定期向其處於活動狀態的服務發送消息。 如果監視程式服務未在規定時間內收到保持活動消息，則服務會嘗試重新啟動設備以進行乾淨的恢復（如果它具有足夠的權限）或重新啟動應用程式。

## 安裝Android Player {#installing-android-player}

若要實作適用於AEM Screens的Android Player，請安裝適用於AEM Screens的Android Player。

請造訪&#x200B;[**AEM 6.5播放器下載**](https://download.macromedia.com/screens/)頁面。

### 設定AEM Screens6.5.5 Service Pack {#fp-environment-setup}的環境

>[!NOTE]
>如果您使用AEM Screens6.5.5 Service Pack，則必須為Android Player設定環境。

在所有作者和發佈例項上，將登入Token Cookie **的** SameSite屬性從&#x200B;**Lax**&#x200B;設為&#x200B;**None**&#x200B;從&#x200B;**Adobe Experience Manager網頁主控台設定**&#x200B;設AEM定至。

請遵循下列步驟：

1. 使用`http://localhost:4502/system/console/configMgr`導覽至&#x200B;**Adobe Experience ManagerWeb控制台配置**。

1. 搜尋&#x200B;*Adobe花崗岩Token驗證處理常式*。

1. 將login-token Cookies的&#x200B;**SameSite屬性從** Lax **設為** None **。**
   ![影像](/help/user-guide/assets/granite-updates.png)

1. 按一下「**儲存**」。


### 臨機方法{#ad-hoc-method}

臨機方法可讓您安裝最新的Android Player(*.exe*)。 請造訪&#x200B;[**AEM 6.5播放器下載**](https://download.macromedia.com/screens/)頁面。

下載應用程式後，請依照播放器上的步驟完成臨機安裝：

1. 長按左上角以開啟管理面板。
1. 從左側操作菜單導航至&#x200B;**Configuration**，然後輸入要連接到的實例的位置（地址），然後按一下AEM **Save**。

1. 從左側操作菜單導航到&#x200B;**設備****註冊**&#x200B;連結，以檢查設備註冊過程的狀態。

>[!NOTE]
>
>如果&#x200B;**State**&#x200B;是&#x200B;**REGISTERED**，您會注意到&#x200B;**Device id**&#x200B;欄位將會填入。
>
>如果&#x200B;**State**&#x200B;是&#x200B;**UNECROVERED**，則可使用&#x200B;**Token**&#x200B;註冊裝置。

## 實作Android Watchdog {#implementing-android-watchdog}

由於Android的架構，重新啟動裝置需要應用程式具備系統權限。 為此，您需要使用製造商的簽名密鑰來簽署應用程式，否則看門狗會重新啟動播放器應用程式，而不會重新啟動裝置。

### 使用製造商金鑰{#signage-of-android-apks-using-manufacturer-keys}的Android標誌

若要存取部分Android的特權API，例如&#x200B;*PowerManager*&#x200B;或&#x200B;*HDMIControlServices*，您必須使用製造商的金鑰簽署android apk。

>[!CAUTION]
>
>先決條件：
>
>您應先安裝Android SDK，然後再執行下列步驟。

請依照下列步驟，使用製造商的金鑰簽署Android應用程式：

1. 從Google Play或[AEM Screens播放器下載](https://download.macromedia.com/screens/)頁面下載應用程式
1. 從製造商獲取平台密鑰，以獲取&#x200B;*pk8*&#x200B;和&#x200B;*pem*&#x200B;檔案

1. 使用尋找~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;，在android sdk中找到apksigner工具
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. 在Android sdk中尋找郵遞區號對齊工具的路徑
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaldified.apk
1. 使用adb安裝安裝至裝置，安裝&#x200B;***aemscreensalpid.apk***

## 瞭解Android Watchdog服務{#android-watchdog-services}

跨Android監視程式服務是使用&#x200B;*AlarmManager*&#x200B;以cordova增效模組實作。

下圖顯示了監視程式服務的實現：

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Initialization**&#x200B;在初始化cordova增效模組時，會檢查權限，以查看我們是否擁有系統權限，進而查看重新啟動權限。 如果滿足這兩個條件，則會建立「待重新啟動的意圖」，否則會建立「待重新啟動的意圖」（基於其「啟動活動」）。

**2.保持活動計時器**&#x200B;使用保持活動計時器每15秒觸發一個事件。 在此情況下，您必須取消現有的待定意圖（以重新啟動或重新啟動應用程式），並在相同的60秒內註冊新的待定意圖（實際上是延遲重新啟動）。

>[!NOTE]
>
>在Android中，*AlarmManager*&#x200B;用於註冊&#x200B;*pendingIntents*，即使應用程式當機且其警報傳送與API 19(Kitkat)不精確，AlarmManager仍可執行。 在計時器的間隔和&#x200B;*AlarmManager的* *pendingIntent的*&#x200B;報警之間保持一定的間隔。

**3.應用程式當機**&#x200B;在當機時，向AlarmManager註冊的待重新引導方式不再重設，因此它會執行應用程式的重新引導或重新啟動（視cordova增效模組初始化時的可用權限而定）。

## Android Player的大量布建{#bulk-provision-android-player}

大量推出Android播放器時，需要布建播放器以指向例項，AEM並設定其他屬性，而不需手動輸入管理UI中的屬性。

>[!NOTE]
>此功能可從Android player 42.0.372取得。

請依照下列步驟，在Android播放器中允許大量布建：

1. 建立名稱為`player-config.default.json`的設定JSON檔案。
請參閱[範例JSON原則](#example-json)以及說明各種[原則屬性](#policy-attributes)使用情形的表格。

1. 使用MDM或ADB或Android Studio檔案總管，將此原則JSON檔案拖放至Android裝置上的&#x200B;*sdcard*&#x200B;檔案夾。

1. 在部署檔案後，使用MDM安裝播放器應用程式。

1. 當播放器應用程式啟動時，它會讀取此設定檔，並指向適用的伺服器，AEM供其註冊並隨後加以控制。

   >[!NOTE]
   >首次啟動應用程式時此檔案為&#x200B;*只讀*，不能用於後續配置。 如果播放器在刪除設定檔之前啟動，只需解除安裝並在裝置上重新安裝應用程式即可。

### 策略屬性{#policy-attributes}

下表匯總了策略屬性，其中包含範例策略JSON以供參考：

| **原則名稱** | **目的** |
|---|---|
| *伺服器* | 指向Adobe Experience Manager伺服器的URL。 |
| *解析度* | 裝置的解析度。 |
| *rebootSchedule* | 重新啟動的計畫適用於所有平台。 |
| *enableAdminUI* | 啟用管理員UI以在網站上設定裝置。 在完全配置並投入生產後，設為&#x200B;*false*。 |
| *enableOSD* | 啟用頻道切換器UI，讓使用者在裝置上切換頻道。 在完全配置並投入生產後，請考慮設定為&#x200B;*false*。 |
| *enableActivityUI* | 啟用以顯示活動的進度，例如下載和同步。 啟用疑難排解功能，並在完全設定後在生產中停用。 |
| *enableNativeVideo* | 啟用以使用原生硬體加速來播放視訊（僅限Android）。 |

### 範例JSON原則{#example-json}

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
>無論是否插入實際的&#x200B;*sdcard*，所有Android裝置都有&#x200B;*sdcard*&#x200B;資料夾。 此檔案在部署時會與「下載」檔案夾處於相同層級。 某些MDM（如Samsung Knox）可將此&#x200B;*sdcard*&#x200B;資料夾位置稱為&#x200B;*內部儲存*。

## 使用企業行動管理{#bulk-provisioning}大量布建Android Player

當大量部署Android播放器時，手動註冊每個播放器將變得很麻煩AEM。 強烈建議您使用EMM（企業行動力管理）解決方案，例如VMWare Airwatch、MobileIron或Samsung Knox，以遠端布建及管理您的部署。 AEM ScreensAndroid播放器支援業界標準EMM AppConfig，允許遠端布建。

### 使用企業行動管理{#implementation}實作Android Player的大量布建

請依照下列步驟，在Android Player中允許大量布建：

1. 請確定您的Android裝置支援Google Play服務。
1. 使用您最愛支援AppConfig的EMM解決方案註冊您的Android播放器裝置。
1. 登入您的EMM主控台，從Google Play拉出AEM Screens播放器應用程式。
1. 選擇受管理的配置或相關選項。
1. 您現在應該會看到可設定的播放器選項清單，例如伺服器和大量註冊代碼。
1. 配置這些參數、保存策略並將其部署到設備。

   >[!NOTE]
   >設備應接收應用程式以及配置，並指向具有選定配置AEM的正確伺服器。 如果您選擇設定大量註冊代碼，並維持其與中設定的相同AEM，則播放器應能自動註冊自己。 如果您已設定預設顯示，它也可以下載並顯示某些預設內容（稍後可視您的方便而變更）。

此外，您應洽詢您的EMM廠商有關AppConfig支援的資訊。 最常用的例如[VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、[Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)、[SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)、[Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)、[IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)和[Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)等支援此業界標準。

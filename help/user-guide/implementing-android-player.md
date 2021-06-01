---
title: 實作Android播放器
seo-title: Android Player實作
description: 請詳閱本頁，了解Android Watchdog的實作，這是一種從當機中復原播放器的解決方案。
seo-description: 請詳閱本頁，了解Android Watchdog的實作，這是一種從當機中復原播放器的解決方案。
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: 管理螢幕，Android Player
role: Administrator
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1439'
ht-degree: 0%

---


# 實作Android Player {#implementing-android-player}

本節說明如何設定Android播放器。 它提供設定檔案的資訊，以及可用選項和建議，說明要用於開發和測試的設定。

此外，**Watchdog**&#x200B;是從崩潰中恢復播放器的解決方案。 應用程式需要向監視程式服務註冊，然後定期向其處於活動狀態的服務發送消息。 如果監視程式服務未在規定的時間內收到保持活動消息，則服務將嘗試重新啟動設備以進行乾淨恢復（如果它具有足夠的權限）或重新啟動應用程式。

## 安裝Android Player {#installing-android-player}

若要實作適用於AEM Screens的Android Player，請安裝適用於AEM Screens的Android Player。

請造訪&#x200B;[**AEM 6.5播放器下載**](https://download.macromedia.com/screens/)頁面。

### 設定AEM Screens 6.5.5 Service Pack {#fp-environment-setup}的環境

>[!NOTE]
>如果您使用AEM Screens 6.5.5 Service Pack，則必須為Android播放器設定環境。

在所有AEM製作和發佈執行個體上，將登入代號Cookie **的** Lax **的** None **從** Adobe Experience Manager Web Console Configuration **設定** SameSite屬性。

請遵循下列步驟：

1. 使用`http://localhost:4502/system/console/configMgr`導覽至&#x200B;**Adobe Experience Manager Web主控台設定**。

1. 搜尋&#x200B;*AdobeGranite代號驗證處理常式*。

1. 將登入代號Cookie **的** SameSite屬性從&#x200B;**Lax**&#x200B;設定為&#x200B;**None**。
   ![影像](/help/user-guide/assets/granite-updates.png)

1. 按一下「**儲存**」。


### 臨機方法{#ad-hoc-method}

臨機方法可讓您安裝最新的Android播放器(*.exe*)。 請造訪&#x200B;[**AEM 6.5播放器下載**](https://download.macromedia.com/screens/)頁面。

下載應用程式後，請依照播放器上的步驟完成臨機安裝：

1. 長按左上角以開啟「管理面板」。
1. 從左側操作菜單導航到&#x200B;**配置**，並輸入要連接的AEM實例的位置（地址），然後按一下&#x200B;**保存**。

1. 從左側操作菜單導航到&#x200B;**Device** **Registration**&#x200B;連結，以檢查設備註冊過程的狀態。

>[!NOTE]
>
>如果&#x200B;**State**&#x200B;為&#x200B;**REGISTERED**，您會注意到將填入&#x200B;**Device id**&#x200B;欄位。
>
>如果&#x200B;**State**&#x200B;為&#x200B;**UNECROSTERD**，則可以使用&#x200B;**Token**&#x200B;註冊設備。

## 實作Android監視程式{#implementing-android-watchdog}

由於Android的架構，重新啟動設備要求應用程式具有系統權限。 要執行此操作，您需要使用製造商的簽名密鑰來簽名apk，否則，監視程式將重新啟動播放器應用程式，而不會重新啟動設備。

### 使用製造商索引鍵{#signage-of-android-apks-using-manufacturer-keys}的Android App招牌

若要存取Android的某些特權API，例如&#x200B;*PowerManager*&#x200B;或&#x200B;*HDMIControlServices*，您需要使用製造商的金鑰簽署android apk。

>[!CAUTION]
>
>先決條件：
>
>您應先安裝android SDK，再執行下列步驟。

請依照下列步驟，使用製造商的金鑰簽署android apk:

1. 從Google Play或從[AEM Screens Player下載](https://download.macromedia.com/screens/)頁面下載頁面
1. 從製造商獲取平台密鑰，以獲取&#x200B;*pk8*&#x200B;和&#x200B;*pem*&#x200B;檔案

1. 在android sdk中，使用尋找~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;來找到apksigner工具
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreenplayer.apk
1. 在android sdk中尋找zip對齊工具的路徑
1. &lt;pathto> /zipalign -fv 4 aemscreenplayer.apk aemscreensalid.apk
1. 使用adb install安裝至裝置，安裝&#x200B;***aemscreensalid.apk***

## 了解Android監視程式服務{#android-watchdog-services}

使用&#x200B;*AlarmManager*&#x200B;將跨Android看門狗服務實作為cordova外掛程式。

下圖顯示了監視程式服務的實現：

![chlimage_1-31](assets/chlimage_1-31.png)

**1. 初始化**&#x200B;在初始化cordova插件時，將檢查權限，以查看我們是否具有系統權限，從而獲得重新啟動權限。 如果滿足這兩個條件，則會建立「待重新引導的目的」，否則會建立「待重新啟動應用程式的目的」（基於其啟動活動）。

**2.保持活動計時器**&#x200B;保持活動計時器用於每15秒觸發一次事件。 在該事件中，您需要取消現有的待定意圖（重新啟動或重新啟動應用程式），並在將來相同的60秒內註冊新的待定意圖（實際上是延遲重新啟動）。

>[!NOTE]
>
>在Android中，*AlarmManager*&#x200B;用於註冊&#x200B;*pendingIntents*，即使應用程式當機且其警報傳送與API 19(Kitkat)不完全，仍可執行。 在計時器的間隔和&#x200B;*AlarmManager的* *pendingIntent的*&#x200B;警報之間保留一些間隔。

**3.應用程式崩潰**&#x200B;如果發生崩潰，向AlarmManager註冊的PendingIntent for Reboot將不再重置，因此它會執行應用程式的重新啟動或重新啟動（取決於cordova插件初始化時的可用權限）。

## Android Player {#bulk-provision-android-player}的大量布建

大量推出Android播放器時，需要布建播放器以指向AEM例項，並設定其他屬性，而不需要在管理員UI中手動輸入這些屬性。

>[!NOTE]
>此功能可從Android播放器42.0.372取得。

請依照下列步驟，允許在Android播放器中大量布建：

1. 建立名為`player-config.default.json`的配置JSON檔案。
請參閱[範例JSON原則](#example-json)，以及說明各種[原則屬性](#policy-attributes)之使用情形的表格。

1. 使用MDM、ADB或Android Studio檔案資源管理器將此策略JSON檔案拖放到Android設備上的&#x200B;*sdcard*&#x200B;資料夾中。

1. 部署檔案後，使用MDM安裝播放器應用程式。

1. 播放器應用程式啟動時，會讀取此設定檔案，並指向適用的AEM伺服器，供其註冊並隨後控制。

   >[!NOTE]
   >此檔案在首次啟動應用程式時為&#x200B;*只讀*，不能用於後續配置。 如果播放器是在放置配置檔案之前啟動的，只需在設備上卸載並重新安裝應用程式即可。

### 策略屬性{#policy-attributes}

下表匯總了具有示例策略JSON的策略屬性以供參考：

| **策略名稱** | **用途** |
|---|---|
| *伺服器* | Adobe Experience Manager伺服器的URL。 |
| *解析度* | 裝置的解析度。 |
| *rebootSchedule* | 要重新啟動的計畫適用於所有平台。 |
| *enableAdminUI* | 啟用管理員UI以在網站上設定裝置。 在完全設定並在生產環境中後，設為&#x200B;*false*。 |
| *enableOSD* | 啟用通道切換器UI，讓使用者在裝置上切換通道。 在完全設定並投入生產後，請考慮將設為&#x200B;*false*。 |
| *enableActivityUI* | 啟用以顯示活動的進度，例如下載和同步。 完全設定後在生產環境中啟用疑難排解功能並加以停用。 |
| *enableNativeVideo* | 啟用以將原生硬體加速用於視訊播放（僅限Android）。 |

### JSON策略示例{#example-json}

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
>無論是否插入實際&#x200B;*sdcard*，所有Android裝置都有&#x200B;*sdcard*&#x200B;資料夾。 部署後，此檔案將與「下載」資料夾處於同一級別。 某些MDM（如Samsung Knox）可能將此&#x200B;*sdcard*&#x200B;資料夾位置稱為&#x200B;*內部儲存*。

## 使用企業移動管理的Android Player批量配置{#bulk-provisioning}

大量部署Android播放器時，使用AEM手動註冊每個播放器將變得很麻煩。 強烈建議使用EMM（企業移動管理）解決方案（如VMWare Airwatch、MobileIron或Samsung Knox）來遠程調配和管理您的部署。 AEM Screens Android player支援業界標準的EMM AppConfig，以允許遠端布建。

### 使用企業移動管理實作Android Player的大量布建 {#implementation}

請依照下列步驟，允許在Android Player中大量布建：

1. 確定您的Android裝置支援Google Play服務。
1. 使用您最喜愛的支援AppConfig的EMM解決方案註冊Android播放器裝置。
1. 登入您的EMM主控台，然後從Google Play提取AEM Screens Player應用程式。
1. 選擇受管配置或相關選項。
1. 您現在應該會看到可設定的播放器選項清單，例如伺服器和大量註冊代碼。
1. 配置這些參數、保存策略並將策略部署到設備。

   >[!NOTE]
   >裝置應會接收應用程式以及設定，並指向使用所選設定的正確AEM伺服器。 如果您選擇設定大量註冊程式碼，並將其保持與AEM中設定的相同，播放器應可自動註冊自己。 如果您已設定預設顯示，它也可以下載並顯示一些預設內容（稍後可視您的方便而變更）。

此外，您應洽詢EMM廠商AppConfig支援。 最受歡迎的產品，例如[VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、[Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)、[SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)、[Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)、[IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)和[Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)等支援此行業標準。

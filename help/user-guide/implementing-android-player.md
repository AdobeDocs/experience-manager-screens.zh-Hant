---
title: 實現Android Player
seo-title: Implementation of Android Player
description: 請按照本頁瞭解Android Watchdog的實現，該解決方案用於從崩潰中恢復播放器。
seo-description: Follow this page to learn implementation of Android Watchdog, a solution to recover the player from crashes.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: 8d4a7b2bc436d822c673a00437ee895c8ef5cb6f
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---

# 實現Android Player {#implementing-android-player}

本節介紹配置Android播放器。 它提供了配置檔案的資訊以及可用選項以及用於開發和測試的設定的建議。

此外， **監視程式** 是從崩潰中恢復玩家的解決方案。 應用程式需要向監視程式服務註冊自身，然後定期向該服務發送其處於活動狀態的消息。 如果監視程式服務在規定時間內未收到保持活動狀態消息，則服務會嘗試重新啟動設備以進行乾淨恢復（如果它具有足夠的權限）或重新啟動應用程式。

## 安裝Android Player {#installing-android-player}

要為AEM Screens實現Android Player，請為AEM Screens安裝Android Player。

訪問 [**6AEM.5播放器下載**](https://download.macromedia.com/screens/) 的子菜單。

### 設定AEM Screens6.5.5 Service Pack環境 {#fp-environment-setup}

>[!NOTE]
>如果使用AEM Screens6.5.5 Service Pack，則必須為Android播放器設定環境。

設定 **登錄令牌Cookie的SameSite屬性** 從 **松** 至 **無** 從 **Adobe Experience ManagerWeb控制台配置** 和發佈AEM實例。

請遵循下列步驟：

1. 導航到 **Adobe Experience ManagerWeb控制台配置** 使用 `http://localhost:4502/system/console/configMgr`。

1. 搜索 *Adobe花崗岩令牌驗證處理程式*。

1. 設定 **登錄令牌Cookie的SameSite屬性** 從 **松** 至 **無**。
   ![影像](/help/user-guide/assets/granite-updates.png)

1. 按一下「**儲存**」。


### Ad-Hoc方法 {#ad-hoc-method}

Ad-Hoc方法允許您安裝最新的Android Player(*.exe*)。 訪問 [**6AEM.5播放器下載**](https://download.macromedia.com/screens/) 的子菜單。

下載應用程式後，請按照播放器上的步驟完成即席安裝：

1. 長按左上角以開啟管理面板。
1. 導航到 **配置** 從左側操作菜單中，輸入要連接到的實AEM例的位置（地址），然後按一下 **保存**。

1. 導航到 **設備** **註冊** 連結以檢查設備註冊過程的狀態。

>[!NOTE]
>
>如果 **州** 是 **已註冊**，您會注意到 **設備ID** 將填充。
>
>如果 **州** 是 **未註冊**，可以使用 **令牌** 註冊設備。

## 實現Android Watchdog {#implementing-android-watchdog}

由於Android的體系結構，重新啟動設備需要應用程式具有系統權限。 為此，您需要使用製造商的簽名密鑰對apk進行簽名，否則監視程式將重新啟動播放器應用程式而不重新啟動設備。

### 使用製造商密鑰的Android Apk的標牌 {#signage-of-android-apks-using-manufacturer-keys}

訪問Android的某些特權API，如 *PowerManager* 或 *HDMIControlServices*&#x200B;您需要使用製造商的密鑰簽署android apk。

>[!CAUTION]
>
>先決條件：
>
>在執行以下步驟之前，應先安裝android SDK。

按照以下步驟使用製造商的密鑰對androidapk進行簽名：

1. 從Google Play或 [AEM Screens播放器下載](https://download.macromedia.com/screens/) 頁
1. 從製造商處獲取平台密鑰以獲取 *pk8* 和 *質* 檔案

1. 使用查找~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;在android sdk中查找apksigner工具
1. &lt;pathto> /apksigner符號 — key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. 在android sdk中查找zip對齊工具的路徑
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensalignd.apk
1. 安裝 ***Aemscreensaling.apk*** 使用adb安裝到設備

## 瞭解Android Watchdog服務 {#android-watchdog-services}

跨Android監視程式服務是使用 *報警管理器*。

下圖顯示了監視程式服務的實現：

![chlimage_1-31](assets/chlimage_1-31.png)

**1. 初始化** 在初始化cordova插件時，會檢查權限，以查看我們是否具有系統權限，從而是否具有「重新啟動」權限。 如果滿足這兩個條件，則會建立掛起的重新啟動意圖，否則會建立掛起的重新啟動應用程式意圖（基於其啟動活動）。

**2. 保持活動計時器** 使用「保持活動」計時器每15秒觸發一次事件。 在該事件中，您需要取消現有的掛起意圖（重新啟動或重新啟動應用），並在將來60秒內註冊新的掛起意圖（實際上是推遲重新啟動）。

>[!NOTE]
>
>在Android中， *報警管理器* 用於註冊 *待處理* 即使應用崩潰，且其警報傳遞與API 19(Kitkat)不準確，也能執行。 在計時器的間隔和 *AlarmManager的* *pendingIntent的* 警報。

**3. 應用程式崩潰** 在發生崩潰時，註冊到AlarmManager的待重新啟動意圖不再重置，因此它執行應用的重新啟動或重新啟動（具體取決於cordova插件初始化時可用的權限）。

## Android Player批量配置 {#bulk-provision-android-player}

批量推出Android播放器時，需要設定播放器以指向實例AEM，並配置其他屬性，而無需手動輸入管理員UI中的屬性。

>[!NOTE]
>Android播放器42.0.372提供此功能。

按照以下步驟允許在Android播放器中批量設定：

1. 建立名為的配置JSON檔案 `player-config.default.json`。
請參閱 [JSON策略示例](#example-json) 以及一個表，它描述了 [策略屬性](#policy-attributes)。

1. 使用MDM或ADB或Android Studio檔案資源管理器將此策略JSON檔案放到 *sd卡* 資料夾。

1. 部署檔案後，使用MDM安裝播放器應用程式。

1. 播放器應用程式啟動時，它將讀取此配置檔案並指向可註冊AEM並隨後控制的適用伺服器。

   >[!NOTE]
   >此檔案為 *只讀* 首次啟動應用程式時，無法用於後續配置。 如果在刪除配置檔案之前啟動了播放器，只需卸載並重新安裝設備上的應用程式即可。

### 策略屬性 {#policy-attributes}

下表匯總了策略屬性，其中包含供參考的示例策略JSON:

| **策略名稱** | **用途** |
|---|---|
| *伺服器* | 到Adobe Experience Manager伺服器的URL。 |
| *解析度* | 設備的解析度。 |
| *重新引導計畫* | 要重新啟動的計畫適用於所有平台。 |
| *enableAdminUI* | 啟用Admin UI以在現場配置設備。 設定為 *假* 完全配置並投入生產。 |
| *啟用OSD* | 啟用通道切換器UI，以便用戶在設備上切換通道。 考慮將設定為 *假* 完全配置並投入生產。 |
| *enableActivityUI* | 啟用以顯示下載和同步等活動的進度。 在完全配置並投入生產後啟用故障排除和禁用。 |
| *enableNativeVideo* | 啟用本機硬體加速以用於視頻播放（僅限Android）。 |

### JSON策略示例 {#example-json}

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
>所有Android設備都 *sd卡* 資料夾是否 *sd卡* 是否。 此檔案在部署時將與「下載」資料夾處於同一級別。 某些MDM（如Samsung Knox）可能指此 *sd卡* 資料夾位置 *內部儲存*。

## 使用企業移動管理的Android Player批量配置 {#bulk-provisioning}

當批量部署Android播放器時，手動註冊每個播放器就變得非常繁瑣AEM。 強烈建議使用EMM（企業移動管理）解決方案（如VMWare Airwatch、MobileIron或Samsung Knox）來遠程配置和管理您的部署。 AEM ScreensAndroid播放器支援行業標準EMM AppConfig，允許遠程配置。

## 命名Android Player {#name-android}

您可以為Android播放器指定用戶友好的設備名稱，從而將指定的設備名稱發送給Adobe Experience Manager(AEM)。 此功能不僅允許您命名Android播放器，還允許您輕鬆分配適當的內容。

>[!NOTE]
>您只能在註冊前選擇播放器名稱。 註冊玩家後，玩家名稱將不能再更改。

按照以下步驟在Android播放器中配置名稱：

1. 導航到 **設定** —> **關於設備**
1. 編輯並設定設備名稱以命名Android播放器

### 利用企業移動管理實現Android Player批量配置 {#implementation}

按照以下步驟允許在Android Player中批量設定：

1. 確保您的Android設備支援Google Play服務。
1. 使用您最喜愛的支援AppConfig的EMM解決方案註冊Android播放器設備。
1. 登錄到EMM控制台，從Google Play拉出AEM Screens播放器應用程式。
1. 選擇托管配置或相關選項。
1. 現在，您應看到可以配置的播放器選項清單，如伺服器和批量註冊代碼。
1. 配置這些參數，保存策略並將其部署到設備。

   >[!NOTE]
   >設備應接收應用程式以及配置，並指向具有選定配AEM置的正確伺服器。 如果您選擇配置批量註冊代碼，並將其與中配置的代碼保AEM持相同，則播放器應能自動註冊自己。 如果您已配置了預設顯示，則還可以下載和顯示一些預設內容（稍後可根據您的方便程度更改這些內容）。

此外，您應與EMM供應商覈實AppConfig支援。 最受歡迎的，例如 [VMWare航空監視](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)。 [移動鐵](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)。 [索蒂](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)。 [黑莓UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)。 [IBMMaas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) 和 [三星諾克斯](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) 其中包括支援這一行業標準。

### 使用螢幕遙控器 {#using-remote-control}

AEM Screens提供遠程控制功能。 在此處瞭解有關此功能的詳細資訊： [螢幕遙控](implementing-remote-control.md)

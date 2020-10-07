---
title: AEM Screens常見問答集
seo-title: AEM Screens常見問答集
description: 請依照本頁取得與AEM Screens專案相關的常見問答集。
seo-description: 請依照本頁取得與AEM Screens專案相關的常見問答集。
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: b4f9acb68aca05ed3f6b040910742c245923dace
workflow-type: tm+mt
source-wordcount: '1483'
ht-degree: 0%

---


# AEM Screens常見問答集 {#aem-screens-faqs}

以下章節提供與AEM Screens專案相關之常見常見問答集的解答。

## 渠道管理 {#channel-management}

### 1.線上和線下通道之間有何差異？ {#what-is-the-difference-between-an-online-and-an-offline-channel}

線 ***上頻道***(Online Channel ***)會在即時環境中顯示更新內容，而離線頻道(*** Offline Channel)則會顯示快取內容。

### 2.如何建立線上通路？ {#how-do-i-make-a-channel-online}

選取渠道並從動作列導覽至渠道屬性。 在「 **Channel」（頻道）標籤下，選** 取「開發人員模式」（強制頻道連線） **,** 讓頻道連線。

### 3.「渠道角色」欄位的用途為何？ {#what-is-the-use-of-the-channel-role-field}

渠道角色是實際執行渠道的抽象化，因此作者可以直接關注一般體驗。 您可以將其視為一種標籤，可在其內容（顯示或排程）中唯一識別渠道。

### 4.實際的通道解析度如何發生？ {#how-does-actual-channel-resolution-happen}

對於 *靜態參照*，解析度僅遵循指定的路徑。

對於 *動態參照*，解析度會在頻道指派給顯示器（而非排程）後發生。 顯示路徑會變成頻道的內容，解析度會如下（最高到最低優先順序）:

1. 顯示器具有與引用的頻道名稱匹配的子節點
1. 顯示具有與引用的通道名稱匹配的同級節點
1. 顯示的父位置具有與引用的頻道名稱匹配的子節點
1. 顯示的grand-parent位置有一個子節點，該子節點與引用的頻道名稱匹配

等等，直到您到達位置資料夾並停在此處（因此，您無法參考位於頻道資料夾中的頻道，例如僅參考位置子樹狀結構中的頻道）。

## 裝置註冊 {#device-registration}

### 1.如果我發現端點，例如裝置上線和註冊的要求，我可以編寫大量裝置的指令碼並註冊這些裝置。 除了將此項鎖定到分支Wi-Fi外，是否還能確保這些請求的安全？ {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

目前只有作者實例才能進行註冊。 雖然註冊服務未經過驗證，但它只會在AEM中建立待審裝置，而不會實際註冊裝置或指派任何顯示。

若要註冊裝置（這表示在AEM中為裝置建立使用者），您仍需要向AEM驗證，而且目前必須手動遵循註冊精靈來完成註冊。 理論上，惡意使用者可能會建立數個擱置中的裝置，但若未登入AEM，就無法註冊任何裝置。

### 2.是否有方法將HTTP GET請求轉換為HTTP POST，並使用某種形式的驗證？ {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

註冊請求是POST請求。

建議您從工作階段取得裝置ID，而非以參數形式傳遞。 這會清除伺服器記錄檔、瀏覽器快取等。 目前並非安全問題。 請注意，當伺服器上沒有狀態更改時，語義上會使用GET，當狀態更改時，會使用POST。

### 3.是否有方法拒絕裝置註冊請求？ {#is-there-a-way-to-decline-a-device-registration-request}

您無法拒絕註冊請求。 註冊請求應在 [Adobe Experience Manager Web Console中設定的逾時後過期](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl)。 預設情況下，此值設定為一天，並儲存在記憶體快取中。

## 設備監視和運行狀況報告 {#device-monitoring-and-health-reports}

### 1.如果我的AEM Screens播放器顯示空白畫面，我要如何進行疑難排解？ {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

請檢查以下可能性以排除空白螢幕問題：

* AEM無法推送離線內容
* 頻道沒有任何內容
* 目前不會排程顯示任何資產

### 2.如果AEM Screens播放器無法註冊且其狀態顯示為「失敗」，該怎麼辦？ {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

您必須啟用Apache Sling Referrer Filter Allow Empty。 這是AEM Screens Player和AEM Screens伺服器之間最佳化控制通訊協定所需的。

1. 導覽至 **Adobe Experience Manager Web Console設定**
1. 選中 **allow.empty選項** 。
1. 按一下&#x200B;**「儲存」**。

### 3.如果在註冊AEM Screens播放器時，裝置顯示FAILURE，而主控台記錄顯示ENAME_NOT_FOUND錯誤，如何進行疑難排解？ {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

如果播放器找不到AEM Screens Server DNS，就可能會發生這個問題。 您可以嘗試使用IP位址進行連線。 要獲取伺服器的IP，請使用： *arp &lt;server_dns_name>*。

### 4.AMS是否建議在所有裝置上實作Android Watchdog? Watchdog(Cordova)外掛程式是否包含在APK中？ {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

使用純Android API的跨平台Android監視程式已包含在應用程式中。 您不需要額外的軟體，但視您使用的裝置而定，您可能需要退出apk才能取得完整電源週期的系統權限(Powermanager api)。 如果它沒有使用製造商密鑰辭職，它將退出並重新啟動應用程式，但不會重新啟動電源。

如需如何實作Android Player的詳細資訊，請參閱實 [**作Android Player**](implementing-android-player.md)。

### 5.Adobe/AMS建議使用哪些協力廠商遠端監視和警報工具（軟體）來監視每個裝置？  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

根據您所需的監控和警報，AEM Screens Notifications新功能會通知您裝置是否有一段時間未ping通。 協力廠商工具將視您的作業系統(OS)、其功能及客戶的特定需求而定。

如需您可在何處監視裝置活動的詳細資訊，請參閱 [**AEM Screens Notifications Service**](screens-notifications-service.md)。

## AEM Screens 播放器 {#aem-screens-player}

### 1.如何將ChromeOS播放器安裝為Chrome Browser外掛程式？ {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS Player可在開發人員模式下以Chrome Browser外掛程式安裝，而不需實際的Chrome Player裝置。 如需安裝，請遵循下列步驟：

1. 按一 [下這裡](https://download.macromedia.com/screens/) ，下載最新的Chrome Player。
1. 解壓縮並儲存在磁碟上。
1. 開啟Chrome瀏覽器，然後從選 **單選取** 「延伸模組」，或直接導覽至 ***chrome://extensions***。
1. 從右上角 **切換** 「開發人員」模式。
1. 按一下左 **上角的「載入解壓縮** 」，然後載入解壓縮的Chrome Player。
1. 如果 **副檔名清單中有AEM Screens Chrome Player** plugin，請勾選。
1. 開啟新的標籤，然後從左上角按 **一下「應用程式** 」圖示，或直接導覽至 ***chrome://apps***。
1. 按一下「 **AEM Screens** Plugin」以啟動Chrome Player。 依預設，播放器會以全螢幕模式啟動。 按 **Esc** 退出全螢幕模式。

### 2.如何疑難排解Screens播放器是否無法透過具有自訂錯誤處理常式的發佈例項進行驗證？ {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

當AEM Screens播放器啟動時，當播放器收到 ***404錯誤時，會向/content/screens/svc.ping.json***&#x200B;提出要求。 播放器會啟動驗證要求以針對發佈例項進行驗證。 如果發佈例項中有自訂錯誤處理常式，請確定您在 ***/content/screens/svc.ping.json上傳回匿名使用者的404狀態代碼***。

### 3.如何在Android Player中設定裝置畫面保持開啟？ {#how-to-set-the-device-screen-stay-on-in-an-android-player}

請依照下列步驟，在任何Android播放器上開啟「保持清醒」:

1. 導覽至Android播放器設定—>關 **於**
1. 點選7次組建編號，以啟用「設定」中 **的「開發人員選項** 」 **功能**
1. 導覽至開發 **人員選項**
1. 啟用 **保持清醒**

### 4.如何啟用Windows播放器的視窗模式？{#enable-player}

Windows Player中沒有窗口模式。 一律為全螢幕模式。

### 5.如何疑難排解AEM Screens播放器是否持續傳送登入要求？{#requests-login}

請依照下列步驟，疑難排解持續傳送要求至和 `/content/screens/svc.json` 下列 `/libs/granite/core/content/login.validate/j_security_check`:

1. 當AEM Screens播放器啟動時，會提出要求 `/content/screens/svc.json`，當播放器收到回應中的404狀態代碼時，播放器會啟動驗證要求，以針對發佈例項 `/libs/granite/core/content/login.validate/j_security_check` 進行驗證。 如果發佈例項中有自訂錯誤處理常式，請務必在或上傳回匿名使用者的404狀態 `/content/screens/svc.json` 代碼 `/content/screens/svc.ping.json`。

1. 檢查您的調度器配置是否允許在部分中使用這些 `/filters` 請求。 如需詳 [細資訊，請參閱設定畫面篩選](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters) 。

1. 檢查您的調度程式重寫規則是否將任何螢幕路徑重寫到其他路徑。

1. 檢查您的作者 `/etc/map` 或發佈例 *項和畫面路徑是否符合***`sling:match` 規則，並在內部重新導向至不同路徑。 解析／中的確切URL`system/console/jcrresolver` ，有助於識別 *publish* 實例是否將這些URL重寫到任何其他路徑。

1. 檢查您是否有造成內部重寫的任何Apache Sling Resource Resolver Factory組態。

## 一般疑難排解提示 {#general-troubleshooting-tips}

### 1.如何停用Livefyre以避免A/P畫面錯誤？ {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

若要停用Livefyre以避免記錄錯誤：

1. ***停用Livefyre搭售：***

   * 導航到 `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * 搜尋AEM Livefyre搭售： `com.adobe.cq.social.cq-social-livefyre`
   * 按一下 **停止**

1. ***停用Livefyre poller:***

   * 在CRXDE Lite中，導覽至 `/etc/importers/polling/livefyre-poller/jcr:content`
   * 新增啟用屬性的 *類型* 布林 *值*
   * 將 **enabled屬性設** 為 **false**


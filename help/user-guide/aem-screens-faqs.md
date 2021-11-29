---
title: AEM Screens常見問題集
seo-title: AEM Screens FAQs
description: 請詳閱本頁，了解與AEM Screens專案相關的常見問題解答。
seo-description: Follow this page to get answers to FAQs related to an AEM Screens project.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: fc120c02e01d0159ca0294a9b5326b53a0fa48f0
workflow-type: tm+mt
source-wordcount: '2120'
ht-degree: 0%

---

# AEM Screens常見問題集 {#aem-screens-faqs}

以下章節提供與AEM Screens專案相關的幾個常見問題集的解答。

## 空白螢幕問題 {#blank-screen}

>[!NOTE]
>列出的強制檢查，應在引發問題之前由主要支援或客戶端支援嘗試。

### 1.對於面對黑屏或非播放內容的客戶，哪些是急救故障排除步驟？ {#troubleshooting-blank-screen}

* 檢查通道預覽是否正常運作。
* 檢查顯示預覽是否正在工作
* 嘗試將播放器註冊為同一顯示器的系統瀏覽器擴充功能，並檢查這是否有效。
* 當播放器在您的系統上執行時，請導覽至 `http://localhost:24502`. 檢查所有內容是否都正確下載。
* 檢查資產是否已建立適當的轉譯，以及正在播放正確的轉譯。
* 檢查是否有任何排程內容，以及時間是否正確。 檢查播放器中設定的時間是否正確。
* Inspect播放器主控台記錄並檢查是否有任何錯誤。 以滑鼠右鍵按一下並檢查，即可查看主控台記錄。 如果使用windows player按下 `CTRL + ALT +I` 開啟dev console以檢視記錄檔。

### 2.如何透過建立預設管道或排程來解決AEM Screens中的灰色畫面問題？

為避免欄位中出現空白或灰色畫面，請建立預設的全域頻道或排程，並以最低優先順序1指派給每個顯示器。 萬一內容更新發生問題（因為網路、播放器、伺服器或復寫），因為播放器已快取磁碟上的此內容，因此應可正常播放並避免顯示灰色畫面。

所有其他內容（例如頻道或排程）的優先順序都會大於1，因此其他內容會優先，而全域頻道或排程內容（優先順序為1）只會以後退選項的形式播放。

## 管道管理 {#channel-management}

### 1.線上和離線頻道有何差異？ {#what-is-the-difference-between-an-online-and-an-offline-channel}

安 ***線上頻道***，會在即時環境中顯示更新的內容，而 ***離線頻道***，顯示快取內容。

### 2.如何線上建立管道？ {#how-do-i-make-a-channel-online}

選取通道並從動作列導覽至通道屬性。 檢查 **開發人員模式（強制通道聯機）** 在 **管道** 標籤，讓通道上線。

### 3. 「管道角色」欄位的用途為何？ {#what-is-the-use-of-the-channel-role-field}

管道角色是實際執行管道的抽象，讓作者能直接專注於一般體驗。 您可以將其視為可唯一識別其內容（顯示或排程）之管道的標籤。

### 4.實際通道解析度如何發生？ {#how-does-actual-channel-resolution-happen}

針對 *靜態參考*，則解析只會遵循指定的路徑。

針對 *動態參考*，則解析度會在通道指派給顯示器（而非排程）後發生。 顯示路徑會成為通道的內容，解析度會如下（最高至最低優先順序）:

1. 顯示器有一個子節點，該子節點與引用的通道名稱匹配
1. 顯示器有一個同級節點，該節點與引用的通道名稱匹配
1. 顯示的父節點具有匹配引用的通道名稱的子節點
1. 顯示的大父節點位置有一個匹配引用的通道名稱的子節點

等等，直到到達位置資料夾並立即停止為止（因此，不能引用通道資料夾中的通道，例如，只能引用位置子樹中的通道）。

### 5.如何在AEM Screens頻道中設定自訂clientlib離線設定？

使用內建的自訂用戶端代碼時 `clientlib` 在AEM Screens管道中，必須執行下列步驟，以確保 `clientlib` 已成功在通道中載入檔案(`manifest.json`)和將包含的路徑 `clientlib`.

請從管道編輯器遵循下列步驟：

1. 選取管道，然後按一下 **編輯** 從動作列開啟頻道編輯器。
1. 選取您要新增自訂的元件 `clientlib`.
1. 按一下「設定」按鈕（扳手圖示）。
1. 導覽至 **離線設定** 標籤，並將路徑新增至 **用戶端程式庫**.

## 裝置註冊 {#device-registration}

### 1.如果我發現端點，例如裝置上線和註冊請求，便可以編寫大量裝置的指令碼並註冊這些裝置。 除了將此鎖定到分支Wi-Fi外，還是可以保護這些請求嗎？ {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

目前只能在製作執行個體上註冊。 雖然註冊服務未通過驗證，但它只會在AEM中建立擱置的裝置，且不會實際註冊裝置或指派任何顯示。

要註冊設備(這意味著在AEM中為設備建立用戶)，您仍需要向AEM驗證，並且當前需要手動按照註冊嚮導完成註冊。 理論上，惡意用戶可能建立多個掛起的設備，但如果沒有AEM登錄，則無法註冊任何設備。

### 2.是否可透過某種驗證形式，將HTTPGET要求轉換為HTTPPOST? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

註冊請求是POST請求。

建議您從工作階段取得裝置ID，而非以參數形式傳遞。 這會清除伺服器記錄、瀏覽器快取等。 目前不是安全性問題。 請注意，當伺服器上沒有狀態更改時，會使用語義GET，當狀態更改時，會使用POST。

### 3.是否可以拒絕設備註冊請求？ {#is-there-a-way-to-decline-a-device-registration-request}

您無法拒絕註冊請求。 註冊請求應會在中設定的逾時後過期 `Adobe Experience Manager Web Console`. 預設情況下，此值將設定為一天，並儲存在記憶體快取中。

## 裝置監控與狀態報告 {#device-monitoring-and-health-reports}

### 1.如果我的AEM Screens播放器顯示空白畫面，如何進行疑難排解？ {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

請檢查下列可能性，以疑難排解空白畫面問題：

* AEM無法推送離線內容
* 管道沒有任何內容
* 目前不會排程顯示任何資產

### 2.如果AEM Screens播放器無法註冊且其狀態顯示為「失敗」，怎麼辦？ {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

您必須啟用Apache Sling Referrer Filter Allow Empty。 這是AEM Screens Player與AEM Screens伺服器之間控制通訊協定最佳運作所需的項目。

1. 導覽至 **Adobe Experience Manager Web主控台設定**
1. 檢查 **allow.empty** 選項。
1. 按一下「**儲存**」。

### 3.如果註冊AEM Screens播放器時，裝置顯示「失敗」，主控台記錄顯示「ENAME_NOT_FOUND」錯誤，如何進行疑難排解？ {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

如果播放器找不到AEM Screens伺服器DNS，就可能會發生此問題。 您可以嘗試使用IP位址來連線。 要獲取伺服器的IP，請使用： *arp &lt;server_dns_name>*.

### 4. AMS是否建議在所有裝置上實作Android監視程式？ Watchdog(Cordova)外掛程式是否包含在APK中？ {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

使用純Android API的跨平台Android監視程式已是Apk的一部分。 不需要其他軟體，但根據您使用的設備，您可能需要退出apk才能獲得完整電源週期(Powermanager api)的系統權限。 如果不使用製造商密鑰辭職，它將退出並重新啟動應用程式，但不會重啟。

如需如何實作Android Player的詳細資訊，請參閱 [**實作Android播放器**](implementing-android-player.md).

### 5.Adobe/AMS建議哪些第三方遠程監視和警報工具（軟體）來監視每台設備？  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

根據您在監控和警報中需要的項目，AEM Screens通知服務會在裝置一段時間內未ping通時通知您。 第三方工具取決於您的作業系統(OS)、其功能和客戶的特定需求。

有關可以監視設備活動的位置的詳細資訊，請參閱 [**AEM Screens通知服務**](screens-notifications-service.md).

## AEM Screens 播放器 {#aem-screens-player}

### 1.如何將ChromeOS播放器安裝為Chrome瀏覽器外掛程式？ {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS播放器可在開發人員模式下，安裝為Chrome瀏覽器外掛程式，而不需要實際的Chrome播放器裝置。 安裝時，請遵循下列步驟：

1. 按一下 [此處](https://download.macromedia.com/screens/) 下載最新的Chrome播放器。
1. 解壓縮並儲存在磁碟上。
1. 開啟Chrome瀏覽器並選取 **擴充功能** ，或直接導覽至 ***chrome://extensions***.
1. 開啟 **開發人員模式** 從右上角。
1. 按一下 **載入未打包** 從左上角載入已解壓縮的Chrome Player。
1. 檢查 **AEM Screens Chrome Player** 外掛程式（如果擴充功能清單中有）。
1. 開啟新標籤，然後按一下 **應用程式** 圖示，或直接導覽至 ***chrome://apps***.
1. 按一下 **AEM Screens** 啟動Chrome Player的外掛程式。 依預設，播放器會以全螢幕模式啟動。 Press **esc** 退出全螢幕模式。

### 2.如果Screens播放器無法透過具有自訂錯誤處理常式的發佈執行個體進行驗證，如何進行疑難排解？ {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

AEM Screens播放器啟動時，會向 ***/content/screens/svc.ping.json***，當播放器收到404錯誤時。 播放器會起始驗證要求，以針對發佈例項進行驗證。 如果發佈執行個體中有自訂錯誤處理常式，請務必傳回匿名使用者的404狀態代碼，位於 ***/content/screens/svc.ping.json***.

### 3.如何在Android播放器中設定裝置畫面持續開啟？ {#how-to-set-the-device-screen-stay-on-in-an-android-player}

請依照下列步驟，在任何Android播放器上開啟「保持清醒」：

1. 導覽至Android播放器設定 — > **關於**
1. 對組建編號點選7次以啟用 **開發人員選項** in **設定**
1. 導覽至 **開發人員選項**
1. 啟用 **保持清醒**

### 4.如何為Windows播放器啟用視窗模式？{#enable-player}

Windows播放器中沒有視窗模式。 一律為全螢幕模式。

### 5.如何疑難排解AEM Screens播放器是否持續傳送登入要求？{#requests-login}

請依照下列步驟，疑難排解持續傳送要求至的AEM Screens播放器 `/content/screens/svc.json` 和 `/libs/granite/core/content/login.validate/j_security_check`:

1. AEM Screens播放器啟動時，會要求 `/content/screens/svc.json`. 當播放器在回應中取得404狀態碼時，會使用 `/libs/granite/core/content/login.validate/j_security_check` 與 *發佈* 例項。 如果 *發佈* 例項，請務必傳回匿名使用者的404狀態代碼，位於 `/content/screens/svc.json` 或 `/content/screens/svc.ping.json`.

1. 檢查您的Dispatcher設定是否允許 `/filters`.

   請參閱 [設定螢幕篩選器](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters) 以取得更多詳細資訊。

1. 檢查調度程式重寫規則是否將任何螢幕路徑重寫到不同路徑。

1. 檢查是否 `/etc/map` 規則 *作者* 或 *發佈* 例項和螢幕路徑相符 `sling:match` 並內部重新導向至不同的路徑。 解析中的確切URL `/system/console/jcrresolver` 有助於識別 *發佈* 例項會將這些URL重新寫入任何其他路徑。

1. 檢查Apache Sling Resource Resolver Factory設定是否導致內部重新寫入。

### 6.如何從播放器API取得顯示器和裝置的詳細資訊？

您可以透過下列方式取得顯示器和裝置的詳細資訊：

* **內部JS API**
* **ContextHub存放區**:三個ContextHub存放區定義於 `/libs/screens/clientlibs/contexthub` 以公開通道、設備和顯示資訊。

   請依照下列步驟使用這些ContentHub儲存值：

   * 編輯管道屬性，並將個人化索引標籤中的ContextHub路徑設為值（如上所述）
   * 在管道JS中，您可以使用：

      ```shell
         ContextHub.getStore('screens-device');
         ContextHub.getStore('screens-display');
         ContextHub.getStore('screens-channels');
      ```

## 一般疑難排解提示 {#general-troubleshooting-tips}

### 1.如何停用Livefyre以避免A/P畫面錯誤？ {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

為了停用Livefyre以避免記錄錯誤：

1. ***停用Livefyre套件組合：***

   * 導航到 `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * 搜尋AEM Livefyre套件組合： `com.adobe.cq.social.cq-social-livefyre`
   * 按一下 **停止**

1. ***停用Livefyre poller:***

   * 在CRXDE Lite中，導覽至 `/etc/importers/polling/livefyre-poller/jcr:content`
   * 新增屬性 *已啟用* type *布林值*
   * 設定 **已啟用的屬性** to **false**

### 2.如何新增Oak索引資訊？ {#add-oak-index-info}

AEM Screens會為產品使用的查詢建立索引定義。
如果有 *查詢遍歷警告* 在 `error.log`，為查詢建立自訂索引。 請參閱 [配置索引](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#configuring-the-indexes) 以取得更多詳細資訊。

您也可以參考 [Oak檔案](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


### 3.配置v3艙單需要什麼？ {#configure-v3}

若要啟用v3資訊清單，您必須：

* 更新Dispatcher。
請參閱 [為資訊清單版本v3配置Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) 以取得更多詳細資訊。

* 更新自訂元件。
請參閱 [自訂處理常式的範本](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers) 以取得更多詳細資訊。

* 在中停用ContentSync `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

* 在中啟用SmartSync `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

* 編輯 `channel/experience fragment/page components`.

* 導覽至 **離線設定** 標籤。

* 輸入 `clientlibs `和需要新增至資訊清單之靜態檔案的資料夾。

### 4.如果在軟體包screens-cloud-ams-pkg-0.0.20、screens-cloud-ams-pkg-0.0.16和screens核心套件已安裝但未啟用，您應該做什麼？

您必須安裝最低版本的AEM 6.5 Feature Pack 8,AMS連接器才能運作。 請參閱 [可用性](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105.html?lang=en#availability) 以取得Screens功能套件的最低版本。
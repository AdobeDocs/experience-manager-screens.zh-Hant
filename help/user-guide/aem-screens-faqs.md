---
title: AEM Screens常見問題
seo-title: AEM Screens FAQs
description: 按照本頁獲取與AEM Screens項目相關的常見問題解答。
seo-description: Follow this page to get answers to FAQs related to an AEM Screens project.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: 089bf4eebe5234d77d6f02ae6fc3b8bb75ba6ea2
workflow-type: tm+mt
source-wordcount: '2185'
ht-degree: 0%

---

# AEM Screens常見問題 {#aem-screens-faqs}

以下部分提供了與AEM Screens項目相關的常見問題解答。

## 空白螢幕問題 {#blank-screen}

>[!NOTE]
>列出的強制性檢查，應在提出問題之前由主要支援或客戶端支援嘗試。

### 1。對於任何面向黑屏或非播放內容的客戶，急救故障排除步驟應該是什麼？ {#troubleshooting-blank-screen}

* 檢查頻道預覽是否正在工作。
* 檢查顯示預覽是否正在工作
* 嘗試將播放器註冊為系統上的瀏覽器擴展插件，並檢查此功能是否正常。
* 在您的系統上運行玩家後，導航至 `http://localhost:24502`。 檢查是否下載了所有內容。
* 檢查是否建立了相應的格式副本並且正在播放正確的格式副本。
* 檢查任何計畫內容以及時間是否正確。 檢查玩家中設定的時間是否正確。
* Inspect播放器控制台記錄並檢查是否有錯誤。 按一下右鍵並檢查以查看控制台日誌。 如果使用Windows播放器按 `CTRL + ALT +I` 開啟dev控制台查看日誌。

### 2.如何通過建立預設通道或時間表解決AEM Screens的灰屏問題？

要避免欄位中出現空白或灰色螢幕，請建立預設的全局通道或時間表，分配給優先順序最低為1的每個顯示。 在這種情況下，內容更新出現問題（由於網路、播放器、伺服器或複製），因為玩家已將此內容快取在磁碟上，因此應該可以正常播放並避免出現灰色螢幕。

所有其他內容（如頻道或時間表）的優先順序都大於1，因此其他內容將優先，而全局頻道或時間表內容（優先順序為1）將僅作為回退選項播放。

## 渠道管理 {#channel-management}

### 1。線上渠道和離線渠道之間有何區別？ {#what-is-the-difference-between-an-online-and-an-offline-channel}

安 ***線上渠道***，將在即時環境中顯示更新的內容，而 ***離線通道***，顯示快取的內容。

### 2.如何線上製作頻道？ {#how-do-i-make-a-channel-online}

選擇通道並從操作欄導航到通道屬性。 檢查 **開發模式（強制通道聯機）** 在 **頻道** 頁籤。

### 3.「渠道角色」欄位的用途是什麼？ {#what-is-the-use-of-the-channel-role-field}

Channel Role是實際運行的通道的抽象，以便作者可以直接關注一般體驗。 您可以將其視為一種標籤，在其上下文（顯示或計畫）中唯一標識通道。

### 4.實際的通道解析度如何發生？ {#how-does-actual-channel-resolution-happen}

對於 *靜態引用*，解析只遵循指定的路徑。

對於 *動態引用*，在將通道分配給顯示器（而非時間表）後，就會出現解析度。 顯示路徑成為通道的上下文，解析度將按如下方式（最高到最低優先順序）進行：

1. 顯示器具有與引用的通道名稱匹配的子節點
1. 顯示具有與引用的通道名稱匹配的同級節點
1. 顯示的父位置具有與引用的通道名稱匹配的子節點
1. 顯示的大父節點具有與引用的通道名稱匹配的子節點

等等，直到您到達位置資料夾並立即停止（因此，您不能引用將位於通道資料夾中的通道，例如，只引用位置子樹中的通道）。

### 5.如何在AEM Screens通道中設定自定義客戶端庫離線配置？

使用構建的自定義客戶端代碼時 `clientlib` 在AEM Screens頻道，需要執行以下步驟來確保 `clientlib` 檔案已成功載入到通道(`manifest.json`)並將包含 `clientlib`。

按照以下通道編輯器中的步驟操作：

1. 選擇一個頻道，然後按一下 **編輯** 的子菜單。
1. 選擇要添加自定義的元件 `clientlib`。
1. 按一下「configure（配置）」按鈕（扳手錶徵圖）。
1. 導航到 **離線配置** 頁籤，並將路徑添加到 **客戶端庫**。

## 裝置註冊 {#device-registration}

### 1。如果我發現終端節點，例如設備登錄和註冊請求，我可以編寫大量設備指令碼並註冊這些設備。 除了將此鎖定到分支Wi-Fi外，是否可以保護這些請求？ {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

當前僅在作者實例上可以進行註冊。 儘管註冊服務未經過身份驗證，但它只會在中建立掛起的設AEM備，並且實際上不會註冊設備或分配任何顯示。

要註冊設備(即為中的設備建立用戶AEM)，您仍然需要向註冊嚮導進行驗證，AEM並且當前需要手動遵循註冊嚮導來完成註冊。 理論上，惡意用戶可能會建立多個掛起的設備，但如果沒有登錄，則無法註冊AEM任何設備。

### 2.是否有一種方法將HTTPGET請求轉換為HTTPPOST，並使用某種形式的身份驗證？ {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

註冊請求是POST請求。

建議從會話獲取設備ID，而不是作為參數傳遞。 這將清除伺服器日誌、瀏覽器快取等。 當前不是安全問題。 請注意，當伺服器上沒有狀態更改時，將使用語義GET，當狀態更改時，將使用POST。

### 3.是否有方法拒絕設備註冊請求？ {#is-there-a-way-to-decline-a-device-registration-request}

您不能拒絕註冊請求。 註冊請求應在中配置的超時後過期 `Adobe Experience Manager Web Console`。 預設情況下，此值設定為一天，並儲存在記憶體快取中。

## 設備監視和運行狀況報告 {#device-monitoring-and-health-reports}

### 1。如果我的AEM Screens播放器顯示空白螢幕，如何排除故障？ {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

請檢查以下可能性以排除空白螢幕問題：

* 無AEM法推送離線內容
* 渠道沒有任何內容
* 沒有計畫在當前時間顯示任何資產

### 2.如果AEM Screens播放器無法註冊且其狀態顯示為失敗，我該怎麼辦？ {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

需要啟用Apache Sling引用過濾器允許空。 這是AEM Screens播放器和AEM Screens伺服器之間控制協定的最佳操作所必需的。

1. 導航到 **Adobe Experience ManagerWeb控制台配置**
1. 檢查 **allow.empty** 的雙曲餘切值。
1. 按一下「**儲存**」。

### 3.如果在註冊AEM Screens播放器時，設備顯示FAILURE，控制台日誌顯示ENAME_NOT_FOUND錯誤，則如何進行故障排除？ {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

如果播放器找不到AEM Screens伺服器DNS，則可能會出現此問題。 可以嘗試使用IP地址進行連接。 要獲取伺服器的IP，請使用： *arp &lt;server_dns_name>*。

### 4.AMS是否建議在所有設備上實施Android Watchdog? Watchdog(Cordova)插件是否包含在APK中？ {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

一個使用純Android API的跨平台Android監視程式已經是程式的一部分。 不需要其他軟體，但根據您使用的設備，您可能需要退出apk以獲得完整電源循環的系統權限(Powermanager api)。 如果沒有使用製造商密鑰辭職，它將退出並重新啟動應用程式，但不會重新啟動電源。

有關如何實施Android Player的詳細資訊，請參閱 [**實現Android Player**](implementing-android-player.md)。

### 5.Adobe/AMS建議使用哪些第三方遠程監視和警報工具（軟體）來監視每台設備？  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

根據您希望從監視和警報中獲得的資訊，如果某個設備在一段時間內未ping通，則新功能「AEM Screens通知」服務會通知您。 第三方工具將取決於您的作業系統(OS)、其功能和客戶的特定需求。

有關可以在何處監視設備活動的詳細資訊，請參閱 [**AEM Screens通知服務**](screens-notifications-service.md)。

## AEM Screens 播放器 {#aem-screens-player}

### 1。如何將ChromeOS播放器安裝為Chrome瀏覽器插件？ {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS播放器可以在開發人員模式下作為Chrome瀏覽器插件安裝，而不需要實際的Chrome播放器設備。 要安裝，請執行以下步驟：

1. 按一下 [這裡](https://download.macromedia.com/screens/) 下載最新的Chrome播放器。
1. 解壓縮並將其保存到磁碟上。
1. 開啟Chrome瀏覽器並選擇 **擴展** 或直接導航到 ***chrome://extensions***。
1. 開啟 **開發人員模式** 右上角。
1. 按一下 **載入已解壓縮** 從左上角裝載已解壓的Chrome播放器。
1. 檢查 **AEM Screens克羅姆球員** 插件（如果擴展清單中可用）。
1. 開啟新頁籤，然後按一下 **應用** 表徵圖，或直接導航到 ***chrome://apps***。
1. 按一下 **AEM Screens** 啟動Chrome Player的插件。 預設情況下，播放器以全屏模式啟動。 按 **esc** 退出全屏模式。

### 2.如果Screens播放器無法使用自定義錯誤處理程式通過發佈實例進行身份驗證，如何進行故障排除？ {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

當AEM Screens玩家開始時，它會請求 ***/content/screens/svc.ping.json***，當播放器出現404錯誤時。 播放器啟動驗證請求以針對發佈實例進行驗證。 如果發佈實例中存在自定義錯誤處理程式，請確保返回上匿名用戶的404狀態代碼 ***/content/screens/svc.ping.json***。

### 3.如何在Android播放器中設定設備螢幕保持開啟狀態？ {#how-to-set-the-device-screen-stay-on-in-an-android-player}

按照以下步驟在任何Android播放器上開啟「保持清醒」：

1. 導航到Android播放器設定 — > **關於**
1. 在內部版本號上點擊7次以啟用 **開發人員選項** 在 **設定**
1. 導航到 **開發人員選項**
1. 啟用 **保持清醒**

### 4.如何為Windows播放器啟用窗口模式？{#enable-player}

Windows播放器中沒有窗口模式。 它總是全屏模式。

### 5.如果AEM Screens播放器連續發送登錄請求，如何排除故障？{#requests-login}

按照以下步驟對連續向發送請求的AEM Screens播放器進行故障排除 `/content/screens/svc.json` 和 `/libs/granite/core/content/login.validate/j_security_check`:

1. 當AEM Screens玩家開始時，它請求 `/content/screens/svc.json`。 當播放器在響應中獲得404狀態代碼時，它使用 `/libs/granite/core/content/login.validate/j_security_check` 與 *發佈* 實例。 如果中有自定義錯誤處理程式 *發佈* 實例，確保返回匿名用戶的404狀態代碼 `/content/screens/svc.json` 或 `/content/screens/svc.ping.json`。

1. 檢查您的調度程式配置是否允許 `/filters`。

   請參閱 [配置螢幕篩選器](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters) 的子菜單。

1. 檢查您的調度程式重寫規則是否將任何螢幕路徑重寫到其他路徑。

1. 檢查是否 `/etc/map` 規則 *作者* 或 *發佈* 實例和螢幕路徑與 `sling:match` 並內部重定向到其他路徑。 正在解析中的確切URL `/system/console/jcrresolver` 有助於識別 *發佈* 實例正在將這些URL重寫到任何其他路徑。

1. 檢查Apache Sling資源解析器工廠配置是否導致內部重寫。

### 6。如何從播放器API獲取顯示和設備的詳細資訊？

您可以通過以下方式獲取顯示器和設備的詳細資訊：

* **內部JS API**
* **上下文中心儲存**:在中定義了三個ContextHub儲存 `/libs/screens/clientlibs/contexthub` 顯示頻道、設備和顯示資訊。

   按照以下步驟使用這些ContentHub儲存值：

   * 編輯通道屬性，並將個性化頁籤中的ContextHub路徑設定為值（如上所述）
   * 在通道JS中，您可以使用：

      ```shell
         ContextHub.getStore('screens-device');
         ContextHub.getStore('screens-display');
         ContextHub.getStore('screens-channels');
      ```

## 一般故障排除提示 {#general-troubleshooting-tips}

### 1。如何禁用Livefyre以避免A/P螢幕錯誤？ {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

為了禁用Livefyre以避免日誌錯誤：

1. ***禁用Livefyre捆綁包：***

   * 瀏覽到 `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * 搜索AEMLivefyre捆綁包： `com.adobe.cq.social.cq-social-livefyre`
   * 按一下 **停止**

1. ***禁用Livefyre poller:***

   * 在CRXDE Lite中，導航到 `/etc/importers/polling/livefyre-poller/jcr:content`
   * 添加新屬性 *啟用* 類型 *布爾型*
   * 設定 **已啟用屬性** 至 **假**

### 2.如何添加Oak索引資訊？ {#add-oak-index-info}

AEM Screens為產品使用的查詢建立索引定義。
如果有 *查詢遍歷WARN* 的 `error.log`，為查詢建立自定義索引。 請參閱 [配置索引](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#configuring-the-indexes) 的子菜單。

您還可以參考上的其他資源 [Oak文檔](https://jackrabbit.apache.org/oak/docs/query/lucene.html)。


### 3.配置v3清單需要什麼？ {#configure-v3}

要啟用v3清單，您必須：

* 更新調度程式。
請參閱 [為清單版本v3配置Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) 的子菜單。

* 更新自定義元件。
請參閱 [自定義處理程式模板](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers) 的子菜單。

* 在中禁用ContentSync `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`。

* 在中啟用SmartSync `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`。

* 編輯 `channel/experience fragment/page components`.

* 導航到 **離線配置** 頁籤。

* 輸入 `clientlibs `以及需要添加到清單的靜態檔案的資料夾。

### 4.如果軟體包螢幕 — cloud-ams-pkg-0.0.20、screens-cloud-ams-pkg-0.0.16和螢幕核心軟體包已安裝但未處於活動狀態，您應該怎麼辦？

必須安裝最低版本的6AEM.5功能包8才能使AMS連接器工作。 查看 [可用性](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105.html?lang=en#availability) 獲取螢幕功能包的最低版本。

### 5.如何在螢幕中配置CQ連結外部化程式服務？

該服務用於為作者和發佈實例定義公共主機名，然後這些值用於更新設備伺服器URL以及ContextHub目標。

可以通過以下方式配置螢幕中的CQ連結外部化程式服務：

1. 瀏覽到 `http://localhost:4502/system/console/configMgr`
1. 第CQ天連結外部化程式
1. 更改 `author/publish` 需要的條目
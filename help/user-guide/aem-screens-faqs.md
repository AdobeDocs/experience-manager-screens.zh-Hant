---
title: AEM Screens常見問題集
seo-title: AEM Screens常見問題集
description: 請詳閱本頁，了解與AEM Screens專案相關的常見問題解答。
seo-description: 請詳閱本頁，了解與AEM Screens專案相關的常見問題解答。
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
feature: 數位招牌，內容
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1903'
ht-degree: 0%

---


# AEM Screens常見問題集{#aem-screens-faqs}

以下章節提供與AEM Screens專案相關的幾個常見問題集的解答。

## 空白螢幕問題{#blank-screen}

>[!NOTE]
>列出的強制檢查，應在引發問題之前由主要支援或客戶端支援嘗試。

### 1.對於面對黑屏或非播放內容的客戶，哪些是急救故障排除步驟？{#troubleshooting-blank-screen}

* 檢查通道預覽是否正常運作。
* 檢查顯示預覽是否正在工作
* 嘗試將播放器註冊為同一顯示器的系統瀏覽器擴充功能，並檢查這是否有效。
* 當播放器在您的系統上執行時，導覽至`http://localhost:24502`。 檢查所有內容是否都正確下載。
* 檢查資產是否已建立適當的轉譯，以及正在播放正確的轉譯。
* 檢查是否有任何排程內容，以及時間是否正確。 檢查播放器中設定的時間是否正確。
* Inspect播放器主控台記錄並檢查是否有任何錯誤。 以滑鼠右鍵按一下並檢查，即可查看主控台記錄。 如果使用windows player，請按`CTRL + ALT +I`開啟開發主控台以檢視記錄。

### 2.如何透過建立預設管道或排程來解決AEM Screens中的灰色畫面問題？

為避免欄位中出現空白或灰色畫面，請建立預設的全域頻道或排程，並以最低優先順序1指派給每個顯示器。 萬一內容更新發生問題（因為網路、播放器、伺服器或復寫），因為播放器已快取磁碟上的此內容，因此應可正常播放並避免顯示灰色畫面。

所有其他內容（例如頻道或排程）的優先順序都會大於1，因此其他內容會優先，而全域頻道或排程內容（優先順序為1）只會以後退選項的形式播放。

## 通道管理{#channel-management}

### 1.線上和離線頻道有何差異？{#what-is-the-difference-between-an-online-and-an-offline-channel}

***線上頻道***&#x200B;將在即時環境中顯示更新的內容，而&#x200B;***離線頻道***&#x200B;顯示快取內容。

### 2.如何線上建立管道？{#how-do-i-make-a-channel-online}

選取通道並從動作列導覽至通道屬性。 在&#x200B;**Channel**&#x200B;標籤下檢查&#x200B;**開發者模式（強制通道聯機）**&#x200B;以使通道聯機。

### 3. 「管道角色」欄位的用途為何？{#what-is-the-use-of-the-channel-role-field}

管道角色是實際執行管道的抽象，讓作者能直接專注於一般體驗。 您可以將其視為可唯一識別其內容（顯示或排程）之管道的標籤。

### 4.實際通道解析度如何發生？{#how-does-actual-channel-resolution-happen}

對於&#x200B;*靜態引用*，解析度僅遵循指定的路徑。

對於&#x200B;*動態引用*，一旦將通道分配給顯示器（而非調度），就會發生解析。 顯示路徑會成為通道的內容，解析度會如下（最高至最低優先順序）:

1. 顯示器有一個子節點，該子節點與引用的通道名稱匹配
1. 顯示器有一個同級節點，該節點與引用的通道名稱匹配
1. 顯示的父節點具有匹配引用的通道名稱的子節點
1. 顯示的大父節點位置有一個匹配引用的通道名稱的子節點

等等，直到到達位置資料夾並立即停止為止（因此，不能引用通道資料夾中的通道，例如，只能引用位置子樹中的通道）。

## 裝置註冊 {#device-registration}

### 1.如果我發現端點，例如裝置上線和註冊請求，便可以編寫大量裝置的指令碼並註冊這些裝置。 除了將此鎖定到分支Wi-Fi外，還是可以保護這些請求嗎？{#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

目前只能在製作執行個體上註冊。 雖然註冊服務未通過驗證，但它只會在AEM中建立擱置的裝置，且不會實際註冊裝置或指派任何顯示。

要註冊設備(這意味著在AEM中為設備建立用戶)，您仍需要向AEM驗證，並且當前需要手動按照註冊嚮導完成註冊。 理論上，惡意用戶可能建立多個掛起的設備，但如果沒有AEM登錄，則無法註冊任何設備。

### 2.是否可透過某種驗證形式，將HTTPGET要求轉換為HTTPPOST?{#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

註冊請求是POST請求。

建議您從工作階段取得裝置ID，而非以參數形式傳遞。 這會清除伺服器記錄、瀏覽器快取等。 目前不是安全性問題。 請注意，當伺服器上沒有狀態更改時，會使用語義GET，當狀態更改時，會使用POST。

### 3.是否可以拒絕設備註冊請求？{#is-there-a-way-to-decline-a-device-registration-request}

您無法拒絕註冊請求。 註冊請求應會在[Adobe Experience Manager Web Console](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl)中設定的逾時後過期。 預設情況下，此值將設定為一天，並儲存在記憶體快取中。

## 設備監視和運行狀況報告{#device-monitoring-and-health-reports}

### 1.如果我的AEM Screens播放器顯示空白畫面，如何進行疑難排解？{#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

請檢查下列可能性，以疑難排解空白畫面問題：

* AEM無法推送離線內容
* 管道沒有任何內容
* 目前不會排程顯示任何資產

### 2.如果AEM Screens播放器無法註冊且其狀態顯示為「失敗」，怎麼辦？{#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

您必須啟用Apache Sling Referrer Filter Allow Empty。 這是AEM Screens Player與AEM Screens伺服器之間控制通訊協定最佳運作所需的項目。

1. 導覽至&#x200B;**Adobe Experience Manager Web主控台設定**
1. 檢查&#x200B;**allow.empty**&#x200B;選項。
1. 按一下「**儲存**」。

### 3.如果註冊AEM Screens播放器時，裝置顯示「失敗」，主控台記錄顯示「ENAME_NOT_FOUND」錯誤，如何進行疑難排解？{#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

如果播放器找不到AEM Screens伺服器DNS，就可能會發生此問題。 您可以嘗試使用IP位址來連線。 要獲取伺服器的IP，請使用：*arp &lt;server_dns_name>*。

### 4. AMS是否建議在所有裝置上實作Android監視程式？ Watchdog(Cordova)外掛程式是否包含在APK中？{#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

使用純Android API的跨平台Android監視程式已是Apk的一部分。 不需要其他軟體，但根據您使用的設備，您可能需要退出apk才能獲得完整電源週期(Powermanager api)的系統權限。 如果不使用製造商密鑰辭職，它將退出並重新啟動應用程式，但不會重啟。

如需如何實作Android Player的詳細資訊，請參閱&#x200B;[**實作Android Player**](implementing-android-player.md)。

### 5.Adobe/AMS建議哪些第三方遠程監視和警報工具（軟體）來監視每台設備？ {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

根據您在監控和警報中需要的項目，AEM Screens通知服務會在裝置一段時間內未ping通時通知您。 第三方工具取決於您的作業系統(OS)、其功能和客戶的特定需求。

有關可監控設備活動的位置的詳細資訊，請參閱&#x200B;[**AEM Screens通知服務**](screens-notifications-service.md)。

## AEM Screens 播放器 {#aem-screens-player}

### 1.如何將ChromeOS播放器安裝為Chrome瀏覽器外掛程式？{#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS播放器可在開發人員模式下，安裝為Chrome瀏覽器外掛程式，而不需要實際的Chrome播放器裝置。 安裝時，請遵循下列步驟：

1. 按一下[這裡](https://download.macromedia.com/screens/)以下載最新的Chrome播放器。
1. 解壓縮並儲存在磁碟上。
1. 開啟Chrome瀏覽器，從功能表選取&#x200B;**擴充功能**，或直接導覽至&#x200B;***chrome://extensions***。
1. 從右上角開啟&#x200B;**開發人員模式**。
1. 按一下左上角的「載入未封裝&#x200B;**」 ，然後載入未壓縮的Chrome播放器。**
1. 如果擴充功能清單中有，請檢查&#x200B;**AEM Screens Chrome Player**&#x200B;外掛程式。
1. 開啟新標籤，然後按一下左上角的&#x200B;**Apps**&#x200B;圖示，或直接導覽至&#x200B;***chrome://apps***。
1. 按一下「**AEM Screens**&#x200B;外掛程式」以啟動Chrome Player。 依預設，播放器會以全螢幕模式啟動。 按&#x200B;**esc**&#x200B;退出全螢幕模式。

### 2.如果Screens播放器無法透過具有自訂錯誤處理常式的發佈執行個體進行驗證，如何進行疑難排解？{#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

AEM Screens播放器啟動時，會向&#x200B;***/content/screens/svc.ping.json***&#x200B;發出要求，當播放器收到404錯誤。 播放器會起始驗證要求，以針對發佈例項進行驗證。 如果發佈例項中有自訂錯誤處理常式，請務必在&#x200B;***/content/screens/svc.ping.json***&#x200B;上傳回匿名使用者的404狀態代碼。

### 3.如何在Android播放器中設定裝置畫面持續開啟？{#how-to-set-the-device-screen-stay-on-in-an-android-player}

請依照下列步驟，在任何Android播放器上開啟「保持清醒」：

1. 導覽至Android播放器設定 — > **關於**
1. 對組建編號點選7次，以在&#x200B;**Settings**&#x200B;中啟用&#x200B;**開發人員選項**
1. 導覽至&#x200B;**開發人員選項**
1. 啟用&#x200B;**保持清醒**

### 4.如何為Windows播放器啟用窗口模式？{#enable-player}

Windows播放器中沒有視窗模式。 一律為全螢幕模式。

### 5.如何疑難排解AEM Screens播放器是否持續傳送登入請求？{#requests-login}

請依照下列步驟，疑難排解持續傳送要求至`/content/screens/svc.json`和`/libs/granite/core/content/login.validate/j_security_check`的AEM Screens播放器：

1. AEM Screens播放器啟動時，會向`/content/screens/svc.json`提出請求。 當播放器在回應中取得404狀態代碼時，會針對&#x200B;*publish*&#x200B;例項使用`/libs/granite/core/content/login.validate/j_security_check`起始驗證請求。 如果&#x200B;*publish*&#x200B;例項中有自訂錯誤處理常式，請務必在`/content/screens/svc.json`或`/content/screens/svc.ping.json`上傳回匿名使用者的404狀態代碼。

1. 檢查您的Dispatcher設定是否允許`/filters`中的這些請求。

   如需詳細資訊，請參閱[設定螢幕篩選器](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters) 。

1. 檢查調度程式重寫規則是否將任何螢幕路徑重寫到不同路徑。

1. 檢查您在&#x200B;*author*&#x200B;或&#x200B;*publish*&#x200B;執行個體上是否有`/etc/map`規則，且螢幕路徑符合`sling:match`，且內部重新導向至不同路徑。 解析`/system/console/jcrresolver`中的確切URL有助於識別&#x200B;*publish*&#x200B;例項是否將這些URL重新寫入任何其他路徑。

1. 檢查Apache Sling Resource Resolver Factory設定是否導致內部重新寫入。

### 6.如何從播放器API取得顯示器和裝置的詳細資訊？

您可以透過下列方式取得顯示器和裝置的詳細資訊：

* **內部JS API**
* **ContextHub存放區**:中定義了三個ContextHub存放區， `/libs/screens/clientlibs/contexthub` 以公開管道、裝置和顯示資訊。

   請依照下列步驟使用這些ContentHub儲存值：

   * 編輯管道屬性，並將個人化索引標籤中的ContextHub路徑設為值（如上所述）
   * 在管道JS中，您可以使用：

      ```shell
         ContextHub.getStore('screens-device');
         ContextHub.getStore('screens-display');
         ContextHub.getStore('screens-channels');
      ```

## 一般疑難排解提示{#general-troubleshooting-tips}

### 1.如何停用Livefyre以避免A/P畫面錯誤？{#how-to-disable-livefyre-to-avoid-a-p-screens-error}

為了停用Livefyre以避免記錄錯誤：

1. ***停用Livefyre套件組合：***

   * 導航到 `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * 搜尋AEM Livefyre套件組合：`com.adobe.cq.social.cq-social-livefyre`
   * 按一下&#x200B;**Stop**

1. ***停用Livefyre poller:***

   * 在CRXDE Lite中，導覽至`/etc/importers/polling/livefyre-poller/jcr:content`
   * 新增屬性&#x200B;*enabled*&#x200B;類型&#x200B;*Boolean*
   * 將&#x200B;**enabled屬性**&#x200B;設為&#x200B;**false**

### 2.如何新增Oak索引資訊？{#add-oak-index-info}

AEM Screens會為產品使用的查詢建立索引定義。
如果`error.log`中有任何&#x200B;*查詢遍歷WARNs*，請為查詢建立自定義索引。 有關詳細資訊，請參閱[配置索引](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#configuring-the-indexes)。

您也可以參閱[Oak Documentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html)上的其他資源。



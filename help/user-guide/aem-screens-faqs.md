---
title: AEM Screens常見問題集
description: 閱讀與AEM Screens專案相關的常見問題解答。
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: e82cfee5ecc6b639b7b2b65553d1635943b356ea
workflow-type: tm+mt
source-wordcount: '2135'
ht-degree: 0%

---

# AEM Screens常見問題集 {#aem-screens-faqs}

本主題提供與AEM Screens專案相關的常見問題解答。

## 空白畫面問題 {#blank-screen}

>[!NOTE]
>列出的強制檢查在提出問題之前應嘗試主要支援或客戶端支援。

### 1.任何面對黑熒幕或未播放內容的客戶，其急救疑難排解步驟應該是什麼？ {#troubleshooting-blank-screen}

* 檢查頻道預覽是否正常運作。
* 檢查顯示預覽是否正常運作
* 請嘗試將播放器註冊為系統上的瀏覽器延伸模組，以登入至相同顯示器，並檢查其是否正常運作。
* 在系統上執行播放器時，導覽至`http://localhost:24502`。 檢查是否已正確下載所有內容。
* 檢查資產，確保已建立適當的轉譯並播放正確的轉譯。
* 檢查是否有任何排程內容，以及時間是否正確。 檢查播放器中設定的時間是否正確。
* Inspect播放器主控台會記錄並檢查是否有任何錯誤。 按一下滑鼠右鍵並檢查以檢視主控台記錄檔。 如果您使用Windows Player，請按`CTRL + ALT +I`開啟開發主控台以檢視記錄檔。

### 2.如何透過建立預設頻道或排程來解決AEM Screens中的灰幕問題？

要避免欄位中的空白或灰色畫面，請建立預設全域頻道或排程，指派給具有最低優先順序1的每個顯示器。 萬一內容更新發生問題，因為播放器已在光碟上快取此內容。 應該會順利播放，避免出現灰色熒幕。

所有其他內容（例如頻道或排程）的優先順序大於1，因此其他內容會採用優先順序，而全域頻道或排程內容（具有優先順序1）只會作為遞補選項播放。

## 頻道管理 {#channel-management}

### 1.線上和離線管道之間有何差異？ {#what-is-the-difference-between-an-online-and-an-offline-channel}

***線上頻道***&#x200B;在即時環境中顯示更新的內容，而&#x200B;***離線頻道***&#x200B;則顯示快取的內容。

### 2.如何讓頻道上線？ {#how-do-i-make-a-channel-online}

按一下頻道，然後從動作列導覽至頻道屬性。 檢查&#x200B;**頻道**&#x200B;標籤下的&#x200B;**開發人員模式（強制頻道上線）**，讓頻道上線。

### 3. 「頻道角色」欄位有何用途？ {#what-is-the-use-of-the-channel-role-field}

管道角色是實際執行管道的抽象概念，可讓作者直接專注於一般體驗。 您可以將之視為可在頻道內容（顯示或排程）中唯一識別該頻道的標籤種類。

### 4.實際頻道解析如何發生？ {#how-does-actual-channel-resolution-happen}

對於&#x200B;*靜態參考*，解析度會遵循指定的路徑。

針對&#x200B;*動態參考*，解析度會在頻道指派給顯示區（而非排程）後發生。 顯示路徑會成為色版的前後關聯，而解析度如下（最高至最低優先順序）：

1. 顯示區有一個與參照的管道名稱相符的子節點
1. 顯示區有一個與參照的管道名稱相符的同層級節點
1. 顯示的父級位置有一個與參照的管道名稱相符的子節點
1. 顯示的父級位置有一個子節點，與參照的管道名稱相符

等等，直到您達到位置資料夾。 現在停在那裡（例如，您無法參照會位於色版資料夾中的色版，僅會參照位置子樹狀結構中的色版）。

### 5.如何在AEM Screens頻道中設定自訂clientlib離線設定？

在AEM Screens管道中使用內建的自訂使用者端代碼`clientlib`時，需要執行下列步驟。 步驟會確定`clientlib`檔案已在通道(`manifest.json`)中成功載入，並包含`clientlib`的路徑。

從通道編輯器執行以下步驟：

1. 按一下頻道，然後按一下動作列中的&#x200B;**編輯**。
1. 按一下您要新增自訂`clientlib`的元件。
1. 按一下設定按鈕（扳手圖示）。
1. 導覽至&#x200B;**離線設定**&#x200B;標籤，並在&#x200B;**使用者端資料庫**&#x200B;中新增路徑至您的自訂clientlib。

## 裝置註冊 {#device-registration}

### 1.如果發現端點（例如裝置上線和註冊請求），我就能編寫許多裝置的指令碼並註冊這些裝置。 除了鎖定至分支Wi-Fi，是否還能保護這些要求？ {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

目前僅可在作者執行個體上註冊。 雖然註冊服務未經過驗證，但它只會在AEM中建立擱置中的裝置，實際上並不會註冊裝置或指派任何顯示器。

若要註冊裝置(在AEM中建立裝置的使用者)，請向AEM驗證並手動遵循註冊精靈以完成註冊。 理論上，惡意使用者可能會建立多個擱置中的裝置，但如果沒有AEM登入，則無法註冊任何裝置。

### 2.是否有方法透過某種形式的驗證將HTTPGET請求轉換為HTTPPOST？ {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

註冊要求是POST要求。

建議您從工作階段取得裝置ID，而非以引數傳遞。 這麼做會清除伺服器記錄、瀏覽器快取等。 這不是安全問題。 語義。 當伺服器上沒有狀態變更時使用GET，而狀態變更時使用POST。

### 3.是否可以拒絕裝置註冊要求？ {#is-there-a-way-to-decline-a-device-registration-request}

您無法拒絕註冊要求。 相反地，註冊要求應在`Adobe Experience Manager Web Console`中設定的逾時後到期。 根據預設，此值會設定為一天，並儲存在記憶體快取中。

## 裝置監視和健康情況報告 {#device-monitoring-and-health-reports}

### 1.如果我的AEM Screens Player顯示空白熒幕，該如何進行疑難排解？

檢查下列是否可能疑難排解空白熒幕問題：

* AEM無法推送離線內容
* 此頻道沒有任何內容
* 沒有任何資產排程在目前時間顯示

### 2.如果AEM Screens Player無法註冊且其狀態顯示為「失敗」，我該怎麼做？

啟用Apache Sling查閱者篩選器允許空白。 在AEM Screens Player與AEM Screens伺服器之間最佳化操作控制通訊協定所需。

1. 瀏覽至&#x200B;**Adobe Experience Manager Web主控台組態**
1. 核取&#x200B;**allow.empty**&#x200B;選項。
1. 按一下「**儲存**」。

### 3.如果在註冊AEM Screens Player時，裝置顯示失敗且主控台記錄檔顯示ENAME_NOT_FOUND錯誤，如何進行疑難排解？

如果播放器找不到AEM Screens伺服器DNS，就可能會發生此問題。 您可以嘗試使用IP位址進行連線。 若要取得伺服器的IP，請使用： *arp &lt;server_dns_name>*。

### 4. AMS建議在所有裝置上實作Android™監視程式嗎？ APK是否包含Watchdog (Cordova)外掛程式？ {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

使用純Android™ API的跨平台Android™監視程式已經是apk的一部分。 不需要其他軟體。 不過，視您使用的裝置而定，您可以視需要放棄apk以取得完整電源週期(`Powermanager` api)的系統許可權。 如果它沒有使用製造商金鑰辭職，它會退出並重新啟動應用程式，但不會重新啟動電源。

如需如何實作Android™ Player的詳細資訊，請參閱&#x200B;[**實作Android™ Player**](implementing-android-player.md)。

### 5.Adobe/AMS建議使用哪些協力廠商遠端監控和警示工具（軟體）來監控每個裝置？ {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

根據您希望在監視和警報中移除的內容，如果裝置一段時間未發出偵測訊號，AEM Screens Notifications服務會通知您。 協力廠商工具取決於您的作業系統(OS)、其功能以及客戶的特定需求。

如需您可以在何處監視裝置活動的詳細資訊，請參閱&#x200B;[**AEM Screen Notifications Service**](screens-notifications-service.md)。

## AEM Screens 播放器

### 1.如何將ChromeOS播放器安裝為Chrome瀏覽器外掛程式？ {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS播放器可在開發人員模式中安裝為Chrome瀏覽器外掛程式，而不需要實際的Chrome播放器裝置。 請依照下列步驟進行安裝：

1. 按一下[這裡](https://download.macromedia.com/screens/)以下載最新的Chrome Player。
1. 解壓縮並儲存在磁碟上。
1. 開啟Chrome瀏覽器，然後在功能表按一下&#x200B;**擴充功能**，或直接導覽至&#x200B;***chrome://extensions***。
1. 從右上角開啟&#x200B;**開發人員模式**。
1. 從左上角按一下「**載入解壓縮**」，然後載入解壓縮的Chrome Player。
1. 如果擴充功能清單中有該專案，請檢查&#x200B;**AEM Screens Chrome Player**&#x200B;外掛程式。
1. 開啟新標籤，然後從左上角按一下&#x200B;**應用程式**&#x200B;圖示，或直接導覽至&#x200B;***chrome://apps***。
1. 按一下&#x200B;**AEM Screens**&#x200B;外掛程式。 依預設，播放器會以全熒幕模式啟動。 按&#x200B;**Esc**&#x200B;結束全熒幕模式。

### 2.如果Screens Player無法透過使用自訂錯誤處理常式的發佈執行個體進行驗證，該如何進行疑難排解？

AEM Screens Player啟動時，會在播放器收到404錯誤時向&#x200B;***/content/screens/svc.ping.json***&#x200B;提出要求。 播放器會起始驗證要求，以針對發佈執行個體進行驗證。 如果發佈執行個體中有自訂錯誤處理常式，請務必在&#x200B;***/content/screens/svc.ping.json***&#x200B;上傳回匿名使用者的404狀態碼。

### 3.如何在Android™ Player中設定裝置熒幕持續顯示？ {#how-to-set-the-device-screen-stay-on-in-an-android-player}

請依照下列步驟，在任何Android™播放器上開啟保持醒來功能：

1. 瀏覽至Android™播放器設定> **關於**。
1. 點選組建編號七次，以便在&#x200B;**設定**&#x200B;中啟用&#x200B;**開發人員選項**。
1. 瀏覽至&#x200B;**開發人員選項**。
1. 啟用&#x200B;**保持清醒**。

### 4.如何啟用Windows Player的視窗模式？{#enable-player}

Windows Player中沒有視窗模式。 永遠處於全熒幕模式。

### 5.如果AEM Screens Player持續傳送登入要求，該如何進行疑難排解？

請依照下列步驟，疑難排解持續傳送要求給`/content/screens/svc.json`和`/libs/granite/core/content/login.validate/j_security_check`的AEM Screens Player：

1. AEM Screens Player啟動時，會向`/content/screens/svc.json`要求。 當播放器在回應中取得404狀態碼時，它會對&#x200B;*發佈*&#x200B;執行個體使用`/libs/granite/core/content/login.validate/j_security_check`來起始驗證要求。 如果&#x200B;*發佈*&#x200B;執行個體中有自訂錯誤處理常式，請確定在`/content/screens/svc.json`或`/content/screens/svc.ping.json`上傳回匿名使用者的404狀態碼。

1. 檢查您的Dispatcher設定是否允許`/filters`中的這些要求。

   如需詳細資訊，請參閱[設定Screens篩選器](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#step-configure-screens-filters)。

1. 檢查您的Dispatcher重寫規則是否正在將任何熒幕路徑重寫為其他路徑。

1. 檢查您在&#x200B;*作者*&#x200B;或&#x200B;*發佈*&#x200B;執行個體上是否有`/etc/map`個規則，且Screens路徑符合`sling:match`，並在內部重新導向至不同的路徑。 解析`/system/console/jcrresolver`中的確切URL有助於識別&#x200B;*發佈*&#x200B;執行個體是否正在將這些URL重寫至任何其他路徑。

1. 檢查Apache Sling Resource Resolver Factory設定是否造成內部重寫。

### 6.如何從播放器API取得顯示器和裝置的詳細資料？

您可以透過以下方式取得顯示器和裝置的詳細資訊：

* **內部JS API**
* **ContextHub存放區**：三個ContextHub存放區定義於`/libs/screens/clientlibs/contexthub`，以公開頻道、裝置和顯示資訊。

  請依照下列步驟，使用這些ContentHub存放區值：

   * 編輯管道屬性，並將個人化標籤中的ContextHub路徑設定為值（如上所述）
   * 在管道JS中，您可以使用：

     ```shell
        ContextHub.getStore('screens-device');
        ContextHub.getStore('screens-display');
        ContextHub.getStore('screens-channels');
     ```

## 一般疑難排解提示 {#general-troubleshooting-tips}

### 1.如何停用Livefyre以避免A/P Screens錯誤？

停用Livefyre以避免記錄錯誤，方法是執行下列動作。

1. ***停用Livefyre套件：***

   * 導覽至 `https://<host>:<port>/system/console/bundles`。
   * 搜尋AEM Livefyre套件： `com.adobe.cq.social.cq-social-livefyre`。
   * 按一下&#x200B;**停止**。

1. ***停用Livefyre輪詢程式：***

   * 在CRXDE Lite中，導覽至`/etc/importers/polling/livefyre-poller/jcr:content`。
   * 新增屬性&#x200B;*已啟用*&#x200B;型別&#x200B;*布林值*。
   * 將&#x200B;**Enabled屬性**&#x200B;設為&#x200B;**false**。

### 2.如何新增Oak索引資訊？ {#add-oak-index-info}

AEM Screens會為產品使用的查詢建立索引定義。
如果`error.log`中有任何&#x200B;*查詢周遊WARN*，請為您的查詢建立自訂索引。 如需詳細資訊，請參閱[設定索引](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/implementing/deploying/deploying/queries-and-indexing#configuring-the-indexes)。

您也可以在[Oak檔案](https://jackrabbit.apache.org/oak/docs/query/lucene.html)上看到其他資源。


### 3.設定v3資訊清單需要哪些條件？ {#configure-v3}

若要啟用v3資訊清單，請執行下列動作：

* 更新Dispatcher。
如需詳細資訊，請參閱[為資訊清單版本v3](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3)設定Dispatcher。

* 更新自訂元件。
如需詳細資訊，請參閱[自訂處理常式的範本](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers)。

* 在`/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`中停用ContentSync。

* 在`/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`中啟用SmartSync。

* 編輯`channel/experience fragment/page components`。

* 瀏覽至&#x200B;**離線設定**&#x200B;標籤。

* 輸入必須加入資訊清單之靜態檔案的`clientlibs `和資料夾。

### 4.如果在套件screens-cloud-ams-pkg-0.0.20、screens-cloud-ams-pkg-0.0.16和screens核心套件已安裝但未啟用，您應該怎麼做？

安裝AEM 6.5 Feature Pack 8的最低版本，讓AMS聯結器正常運作。 請參閱[可用性](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105#availability)，以取得AEM Screens Feature Pack的最低版本。

### 5.如何在Screens中設定CQ Link Externalizer服務？

此服務可用來定義製作和發佈執行個體的公用主機名稱，而值接著可用來更新裝置伺服器URL及用於ContextHub鎖定目標。

Screens中的CQ Link Externalizer服務可透過以下方式設定：

1. 瀏覽至`http://localhost:4502/system/console/configMgr`
1. Day CQ連結外部化器
1. 視需要變更`author/publish`專案的主機名稱
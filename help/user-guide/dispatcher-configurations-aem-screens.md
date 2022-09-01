---
title: 適用於AEM Screens的Dispatcher設定
seo-title: Dispatcher Configurations for AEM Screens
description: 本頁面重點說明為AEM Screens專案設定Dispatcher的准則。
seo-description: This page highlights guidelines for configuring dispatcher for an AEM Screens project.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 2%

---

# 適用於AEM Screens的Dispatcher設定{#dispatcher-configurations-for-aem-screens}

Dispatcher 是 Adobe Experience manager 的快取和/或負載平衡工具。

以下頁面提供為AEM Screens專案設定Dispatcher的准則。

>[!NOTE]
>
>如果調度程式可用，則可以通過在調度程式規則中進行篩選來阻止與註冊servlet的連接。
>
>如果沒有Dispatcher，請停用OSGi元件清單中的註冊Servlet。

在為AEM Screens專案設定Dispatcher之前，您必須先具備Dispatcher的相關知識。
請參閱 [設定Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) 以取得更多詳細資訊。

## 為資訊清單v2配置Dispatcher {#configuring-dispatcher}

>[!IMPORTANT]
>下列Dispatcher設定僅適用於資訊清單v2。 請參閱 [資訊清單v3版的Dispatcher設定](#configuring-dispatcherv3) 資訊清單v3版。

AEM Screens播放器或裝置也會使用已驗證的工作階段來存取發佈執行個體中的資源。 因此，當您有多個發佈例項時，請求應一律前往相同的發佈例項，使已驗證的工作階段對來自AEM Screens播放器/裝置的所有請求有效。

請依照下列步驟，為AEM Screens專案設定Dispatcher。

### 啟用嚴格工作階段 {#enable-sticky-session}

如果您想使用由單一Dispatcher前端的多個發佈例項，必須更新 `dispatcher.any` 啟用黏著性的檔案

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

如果您有一個發佈例項由一個Dispatcher前端，則啟用Dispatcher的黏著度將沒有幫助，因為負載平衡器可能會將每個請求傳送至Dispatcher。 在此情況下，按一下 **啟用** in **黏著度** 欄位以在負載平衡器層級啟用，如下圖所示：

![影像](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

例如，如果您使用AWS ALB，請參閱 [應用程式負載平衡器的目標組](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) 在ALB層級啟用黏著度。 啟用1天的黏著度。

### 步驟1:設定用戶端標題 {#step-configuring-client-headers}

將下列項目新增至 `/clientheaders`小節：

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 步驟2:設定螢幕篩選器 {#step-configuring-screens-filters}

若要設定Screens篩選器，請新增下列內容至 ***/filter***.

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/libs/granite/csrf/token.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0204 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0210 { /type "allow" /method '(GET|POST)' /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0211 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0212 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0213 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0220 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0222 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### 步驟3:停用Dispatcher快取 {#step-disabling-dispatcher-cache}

停用的Dispatcher快取 ***/content/screens路徑***.

螢幕播放器使用已驗證的工作階段，因此Dispatcher不會快取的任何螢幕播放器請求 `channels/assets`.

若要啟用資產的快取，以便從Dispatcher快取提供資產，您必須：

* 新增 `/allowAuthorization 1` in `/cache` 節
* 將下列規則新增至 `/rules` 區段 `/cache`

```xml
/0000
    {
        /glob "*"
        /type "allow"
    }   

/0001
    {
        # Disable Dispatcher Cache for Screens channels
        /glob "/content/screens/*.html"
        /type "deny" 
    }

/0002
    {
    # Disable Dispatcher Cache for Screens offline manifests
    /glob "/content/screens/*.json"
    /type "deny"
    }

/0003
    { # Disable Dispatcher Cache for Screens devices json 
    /glob "/home/users/screens/*.json"
    /type "deny"
    }
```

## 為資訊清單版本v3配置Dispatcher{#configuring-dispatcherv3}

請務必在Screens運作的發佈執行個體前面的Dispatcher中允許這些篩選器和快取規則。

### 資訊清單v3的先決條件{#prerequisites3}

在設定AEM Screens的Dispatcher（資訊清單版本v3）之前，請務必遵循下列兩個必要條件：

* 請確定您使用 `v3 manifests`. 導覽至 `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` 並確保 `Enable ContentSync Cache` 未勾選。

* 請確定Dispatcher排清代理已設定於 `/etc/replication/agents.publish/dispatcher1useast1Agent` 在發佈例項中。

   ![影像](/help/user-guide/assets/dispatcher/dispatcher-1.png)

   ![影像](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### 篩選條件  {#filter-v3}

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/libs/granite/csrf/token.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0204 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
 
## # Device Dashboard Configurations
/0210 { /type "allow" /method '(GET|POST)' /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0211 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0212 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0213 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
 
## # Content Configurations
/0220 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
#/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you're using experience-fragments
/0222 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" } ## add any other formats required for your project here
 
## # Enable clientlibs proxy servlet
/0230 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

### 快取規則 {#cache-rules-v3}

* 新增 `/allowAuthorized "1"` to `/cache` 區段 `publish_farm.any`.

* 所有Screens播放器將使用已驗證的工作階段連線至AEM（製作/發佈）。 現成可用的Dispatcher不會快取這些url，因此我們應該啟用這些url。

* 新增 `statfileslevel "10"` to `/cache` 區段 `publish_farm.any`
這將支援從快取資料夾快取高達10個層級，並在內容發佈時據以使其無效，而非讓所有內容失效。 您可以隨時根據內容結構的深度來變更此層級

* 將下列項目新增至 `/invalidate section in publish_farm.any`

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* 將下列規則新增至 `/rules` 區段 `/cache` in `publish_farm.any` 或包含在 `publish_farm.any`:

   ```
   ## Don't cache CSRF login tokens
   /0001
       {
       /glob "/libs/granite/csrf/token.json"
       /type "deny"
       }
   ## Allow Dispatcher Cache for Screens channels
   /0002
       {
           /glob "/content/screens/*.html"
           /type "allow"
       }
   ## Allow Dispatcher Cache for Screens offline manifests
   /0003
       {
       /glob "/content/screens/*.manifest.json"
       /type "allow"
       }
   ## Allow Dispatcher Cache for Assets
   /0004
       {
   
       /glob "/content/dam/*"
       /type "allow"
       }
   ## Disable Dispatcher Cache for Screens devices json
   /0005
       {
       /glob "/home/users/screens/*.json"
       /type "deny"
       }
   ## Disable Dispatcher Cache for Screens svc json
   /0006
       {
       /glob "/content/screens/svc.json"
       /type "deny"
       }
   ```

### 新增segments.js的無效規則 {#invalidsegmentjs}

如果您搭配AEM Screens使用目標式促銷活動，則 `segments.js file` 當您在AEM上新增和發佈新區段時，dispatcher提供的內容必須失效。 若沒有此無效規則，新的鎖定目標促銷活動將無法在Screens播放器上運作（會改為顯示預設內容）。

* 將無效規則新增至 `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`. 新增規則如下：

```
    /invalidate {
                        .
                        .
                        /0004 {
                               /glob "conf/<project-name>/settings/wcm/.js"
                               /type "allow"
                        }
                }
```

* 此規則可確保 `segments.js` 檔案失效，修改時會擷取最新檔案。

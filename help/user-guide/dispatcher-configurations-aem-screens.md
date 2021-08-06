---
title: 適用於AEM Screens的Dispatcher設定
seo-title: 適用於AEM Screens的Dispatcher設定
description: 本頁面重點說明為AEM Screens專案設定Dispatcher的准則。
seo-description: 本頁面重點說明為AEM Screens專案設定Dispatcher的准則。
feature: 管理畫面
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 0f32fc015729685c724176c25920da6f07707c00
workflow-type: tm+mt
source-wordcount: '586'
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
如需詳細資訊，請參閱[設定Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) 。

## 為資訊清單v2配置Dispatcher {#configuring-dispatcher}

>[!IMPORTANT]
>下列Dispatcher設定僅適用於資訊清單v2。 如需資訊清單v3，請參閱[資訊清單v3](#configuring-dispatcherv3)版的Dispatcher設定。

AEM Screens播放器或裝置也會使用已驗證的工作階段來存取發佈執行個體中的資源。 因此，當您有多個發佈例項時，請求應一律前往相同的發佈例項，使已驗證的工作階段對來自AEM Screens播放器/裝置的所有請求有效。

請依照下列步驟，為AEM Screens專案設定Dispatcher。

### 啟用嚴格工作階段 {#enable-sticky-session}

如果您想使用由單一Dispatcher前端的多個發佈例項，必須更新`dispatcher.any`檔案以啟用黏著度

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

如果您有一個發佈例項由一個Dispatcher前端，則啟用Dispatcher的黏著度將沒有幫助，因為負載平衡器可能會將每個請求傳送至Dispatcher。 在此情況下，按一下&#x200B;**粘著度**&#x200B;欄位中的&#x200B;**啟用**&#x200B;以在負載平衡器級別啟用它，如下圖所示：

![影像](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

例如，如果您使用AWS ALB，請參閱應用程式負載平衡器](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html)的[目標組，以啟用ALB層級的黏著度。 啟用1天的黏著度。

### 步驟1:設定用戶端標題 {#step-configuring-client-headers}

將下列內容新增至`/clientheaders`區段：

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 步驟2:設定螢幕篩選器 {#step-configuring-screens-filters}

若要設定Screens篩選器，請將下列項目新增至&#x200B;***/filter***。

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

停用&#x200B;***/content/screens path***&#x200B;的Dispatcher快取。

螢幕播放器使用已驗證的工作階段，因此Dispatcher不會快取`channels/assets`的任何螢幕播放器請求。

若要啟用資產的快取，以便從Dispatcher快取提供資產，您必須：

* 在`/cache`區段中新增`/allowAuthorization 1`
* 將下列規則新增至`/cache`的`/rules`區段

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

* 請務必使用`v3 manifests`。 導覽至`https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`，並確認未勾選`Enable ContentSync Cache`。

* 請確定已在發佈執行個體的`/etc/replication/agents.publish/dispatcher1useast1Agent`中設定Dispatcher排清代理程式。

   ![影像](/help/user-guide/assets/dispatcher/dispatcher-1.png)

   ![影像](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### 濾鏡  {#filter-v3}

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

* 將`/allowAuthorized "1"`新增至`publish_farm.any`中的`/cache`區段。

* 所有Screens播放器將使用已驗證的工作階段連線至AEM（製作/發佈）。 現成可用的Dispatcher不會快取這些url，因此我們應該啟用這些url。

* 將`statfileslevel "10"`新增至`publish_farm.any`中的`/cache`區段
這將支援從快取資料夾快取高達10個層級，並在內容發佈時據以使其無效，而非讓所有內容失效。 您可以隨時根據內容結構的深度來變更此層級

* 將下列內容新增至`/invalidate section in publish_farm.any`

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* 將下列規則新增至`publish_farm.any`中`/cache`或`publish_farm.any`所包含檔案中的`/rules`區段：

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

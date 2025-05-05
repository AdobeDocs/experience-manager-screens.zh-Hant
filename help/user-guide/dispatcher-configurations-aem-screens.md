---
title: 適用於AEM Screens的Dispatcher設定
description: 本頁面著重說明為AEM Screens專案設定Dispatcher的指引。
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# 適用於AEM Screens的Dispatcher設定{#dispatcher-configurations-for-aem-screens}

Dispatcher是Adobe Experience Manager的快取或負載平衡工具，或兩者皆有。

以下頁面提供為AEM Screens專案設定Dispatcher的指引。

>[!NOTE]
>
>如果Dispatcher可用，可藉由在Dispatcher規則中篩選來避免與註冊servlet的連線。
>
>如果沒有Dispatcher，請停用OSGi元件清單中的註冊servlet。

在為AEM Screens專案設定Dispatcher之前，請先瞭解Dispatcher。
如需詳細資訊，請參閱[設定Dispatcher](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration)。

## 為資訊清單版本v2設定Dispatcher {#configuring-dispatcher}

>[!IMPORTANT]
>下列Dispatcher設定僅適用於資訊清單版本v2。 請參閱資訊清單版本v3[&#128279;](#configuring-dispatcherv3)的Dispatcher設定，以取得資訊清單版本v3。

AEM Screens播放器或裝置使用已驗證的工作階段來存取發佈執行個體中的資源。 如果有多個發佈執行個體，請求應一律移至相同的發佈執行個體，使已驗證的工作階段對來自AEM Screens播放器或裝置的所有請求有效。

請依照下列步驟，為AEM Screens專案設定Dispatcher。

### 啟用粘性工作階段 {#enable-sticky-session}

如果您想要使用單一Dispatcher前置的多個發佈執行個體，請更新`dispatcher.any`檔案以啟用粘著度。

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

如果您有一個發佈執行個體由一個Dispatcher作前端，在Dispatcher啟用粘著度沒有幫助，因為負載平衡器可能會將每個請求傳送到Dispatcher。 在此情況下，請按一下&#x200B;**粘著度**&#x200B;欄位中的&#x200B;**啟用**，以在您的負載平衡器層級開啟它，如下圖所示：

![影像](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

例如，如果您使用AWS ALB，請參閱[應用程式負載平衡器的目標群組](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html)以啟用ALB層級的粘著度。 啟用一天的粘著度。

### 步驟1：設定使用者端標頭 {#step-configuring-client-headers}

將下列專案新增至`/clientheaders`區段：

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 步驟2：設定Screens篩選器 {#step-configure-screens-filters}

若要設定Screens篩選器，請將下列專案新增至&#x200B;***`/filter`***。

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

### 步驟3：停用Dispatcher快取 {#step-disabling-dispatcher-cache}

停用&#x200B;***/content/screens路徑***&#x200B;的Dispatcher快取。

Screens播放器使用已驗證的工作階段，因此Dispatcher不會快取`channels/assets`的任何screens播放器請求。

若要啟用資產的快取，以便從Dispatcher快取中提供資產，請執行下列動作：

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

## 為資訊清單版本v3設定Dispatcher{#configuring-dispatcherv3}

請務必允許這些篩選器和快取規則位於發佈執行個體前端的Dispatcher中，以便Screens正常運作。

### 資訊清單版本v3的先決條件{#prerequisites3}

為AEM Screens設定Dispatcher （資訊清單版本v3）之前，請遵循下列兩個必要條件：

* 確定您正在使用`v3 manifests`。 導覽至`https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`並確保未勾選`Enable ContentSync Cache`。

* 請確定已在發佈執行個體中的`/etc/replication/agents.publish/dispatcher1useast1Agent`設定Dispatcher排清代理程式。

  ![影像](/help/user-guide/assets/dispatcher/dispatcher-1.png)

  ![影像](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### 篩選條件 {#filter-v3}

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

* 所有AEM Screens播放器都會使用已驗證的工作階段來連線至AEM （作者/發佈）。 Dispatcher不會快取這些URL，因此您應該啟用它們。

* 將`statfileslevel "10"`新增至`publish_farm.any`中的`/cache`區段
此規則支援快取docroot中的最多10個層級，並在內容發佈時據以失效，而不是讓所有內容失效。 您可以根據內容結構的深度，隨時變更此層級

* 新增下列至`/invalidate section in publish_farm.any`

  ```
  /0003 {
      /glob "*.json"
      /type "allow"
  }
  ```

* 將下列規則新增至`publish_farm.any`中`/cache`或從`publish_farm.any`所包含檔案中的`/rules`區段：

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

### 為segments.js新增失效規則 {#invalidsegmentjs}

如果您搭配AEM Screens使用目標式行銷活動，當您在AEM上新增和發佈新區段時，Dispatcher提供的`segments.js file`必須失效。 如果沒有此失效規則，新的目標定位行銷活動將無法在AEM Screens Player上運作（而是顯示預設內容）。

* 將失效規則新增到`/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`。 以下是新增的規則：

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

* 此規則可確保`segments.js`檔案失效，並在修改時擷取最新檔案。

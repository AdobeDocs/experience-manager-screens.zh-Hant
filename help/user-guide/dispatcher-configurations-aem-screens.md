---
title: 適用於AEM Screens的Dispatcher設定
description: 此頁面主要說明為AEM Screens專案設定Dispatcher的准則。
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# 適用於AEM Screens的Dispatcher設定{#dispatcher-configurations-for-aem-screens}

Dispatcher是Adobe Experience Manager的快取和/或負載平衡工具。

以下頁面提供為AEM Screens專案設定Dispatcher的准則。

>[!NOTE]
>
>如果Dispatcher可用，可藉由在Dispatcher規則中篩選來避免與註冊servlet的連線。
>
>如果沒有Dispatcher，請停用OSGi元件清單中的註冊servlet。

在為AEM Screens專案設定Dispatcher之前，您必須先瞭解Dispatcher。
請參閱 [設定Dispatcher](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration) 以取得更多詳細資料。

## 為資訊清單版本v2設定Dispatcher {#configuring-dispatcher}

>[!IMPORTANT]
>下列Dispatcher設定僅適用於Manifest版本v2。 請參閱 [資訊清單版本v3的Dispatcher設定](#configuring-dispatcherv3) 資訊清單版本v3。

AEM Screens播放器或裝置使用已驗證的工作階段來存取發佈執行個體中的資源。 因此，當您有多個發佈執行個體時，請求應一律移至相同的發佈執行個體，這樣已驗證的工作階段就會對來自AEM Screens播放器/裝置的所有請求有效。

請依照下列步驟，為AEM Screens專案設定Dispatcher。

### 啟用粘性工作階段 {#enable-sticky-session}

如果您想要使用單一Dispatcher提前的多個發佈執行個體，請更新 `dispatcher.any` 啟用粘著度的檔案。

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

如果您有一個發佈執行個體由一個Dispatcher做前端，在Dispatcher上啟用粘著沒有幫助，因為負載平衡器可能會將每個請求傳送給Dispatcher。 在此情況下，請選取 **啟用** 在 **粘著度** 欄位，以在您的負載平衡器層級將其開啟，如下圖所示：

![影像](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

例如，如果您使用AWS ALB，請參閱 [應用程式負載平衡器的目標群組](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) 用於啟用ALB層級的粘著度。 啟用一天的粘著度。

### 步驟1：設定使用者端標頭 {#step-configuring-client-headers}

將下列專案新增至 `/clientheaders`區段：

**X-Request-With**

**X設定心率**

**X要求命令**

### 步驟2：設定畫面篩選器 {#step-configure-screens-filters}

若要設定Screens篩選器，請將下列專案新增至 ***/filter***.

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

停用Dispatcher快取 ***/content/screens路徑***.

Screens播放器會使用已驗證的工作階段，因此Dispatcher不會快取播放器請求的任何畫面 `channels/assets`.

若要啟用資產的快取，以便從Dispatcher快取中提供資產，您必須：

* 新增 `/allowAuthorization 1` 在 `/cache` 區段
* 將下列規則新增至 `/rules` 部分 `/cache`

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

在為AEM Screens設定Dispatcher （資訊清單版本v3）之前，請遵循這兩個先決條件：

* 確定您使用 `v3 manifests`. 瀏覽至 `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` 並確保 `Enable ContentSync Cache` 未勾選。

* 請確定Dispatcher Flush代理程式設定在 `/etc/replication/agents.publish/dispatcher1useast1Agent` 在發佈執行個體中。

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

* 新增 `/allowAuthorized "1"` 至 `/cache` 中的區段 `publish_farm.any`.

* 所有AEM Screens播放器都使用已驗證的工作階段來連線至AEM （作者/發佈）。 現成可用的Dispatcher不會快取這些URL，因此您應該啟用這些URL。

* 新增 `statfileslevel "10"` 至 `/cache` 中的區段 `publish_farm.any`
這支援快取docroot中的最多10個層級，並在內容發佈時據以失效，而不是讓所有內容失效。 您可以根據內容結構的深度，隨時變更此層級

* 將下列專案新增至 `/invalidate section in publish_farm.any`

  ```
  /0003 {
      /glob "*.json"
      /type "allow"
  }
  ```

* 將下列規則新增至 `/rules` 中的區段 `/cache` 在 `publish_farm.any` 或包含在檔案中的 `publish_farm.any`：

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

如果您透過AEM Screens使用目標式行銷活動，則 `segments.js file` 當您在AEM上新增和發佈新區段時，Dispatcher提供的服務必須失效。 如果沒有此失效規則，新的目標定位行銷活動將無法在AEM Screens播放器上運作（而是顯示預設內容）。

* 新增失效規則至 `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`. 以下是新增的規則：

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

* 此規則可確保 `segments.js` 檔案會失效，並在修改時擷取最新版本。

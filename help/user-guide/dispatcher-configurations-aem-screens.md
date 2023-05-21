---
title: 用於AEM Screens的調度程式配置
seo-title: Dispatcher Configurations for AEM Screens
description: 本頁重點介紹為AEM Screens項目配置調度程式的指導原則。
seo-description: This page highlights guidelines for configuring dispatcher for an AEM Screens project.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 3%

---

# 用於AEM Screens的調度程式配置{#dispatcher-configurations-for-aem-screens}

Dispatcher 是 Adobe Experience manager 的快取和/或負載平衡工具。

以下頁提供了配置AEM Screens項目調度程式的指導。

>[!NOTE]
>
>如果調度程式可用，則可以通過在調度程式規則中過濾來阻止到註冊servlet的連接。
>
>如果沒有調度程式，請在OSGi元件清單中禁用註冊servlet。

在為AEM Screens項目配置調度程式之前，必須事先瞭解Dispatcher。
請參閱 [配置Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) 的子菜單。

## 為清單版本v2配置Dispatcher {#configuring-dispatcher}

>[!IMPORTANT]
>以下Dispatcher配置僅適用於清單版本v2。 請參閱 [清單版本v3的Dispatcher配置](#configuring-dispatcherv3) 清單版本v3。

AEM Screens玩家或設備使用經過驗證的會話來訪問發佈實例中的資源。 因此，當您具有多個發佈實例時，請求應始終轉到同一發佈實例，以便經過身份驗證的會話對來自AEM Screens玩家/設備的所有請求有效。

按照以下步驟為AEM Screens項目配置調度程式。

### 啟用粘滯會話 {#enable-sticky-session}

如果要使用由單個調度程式所前面的多個發佈實例，則必須更新 `dispatcher.any` 檔案以啟用粘性

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

如果您有一個發佈實例由一個調度程式所前置，則啟用調度程式的粘性將無濟於事，因為負載平衡器可能會將每個請求發送到調度程式。 在這種情況下，按一下 **啟用** 在 **粘性** 欄位以在負載平衡器級別啟用它，如下圖所示：

![影像](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

例如，如果您使用的是AWSALB，請參閱 [應用程式負載平衡器的目標組](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) 在ALB級別實現粘性。 啟用1天的粘性。

### 步驟1:配置客戶端標頭 {#step-configuring-client-headers}

將以下內容添加到 `/clientheaders`部分：

**X請求**

**X-SET-HEARTBATE**

**X請求命令**

### 步驟2:配置螢幕篩選器 {#step-configuring-screens-filters}

要配置螢幕篩選器，請將以下內容添加到 ***/篩選器***。

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

### 第3步：禁用Dispatcher快取 {#step-disabling-dispatcher-cache}

禁用的調度程式快取 ***/內容/螢幕路徑***。

螢幕播放器使用經過驗證的會話，因此調度程式不會快取任何螢幕播放器請求 `channels/assets`。

要為資產啟用快取，以便從調度程式快取處理資產，您必須：

* 添加 `/allowAuthorization 1` 在 `/cache` 節
* 將以下規則添加到 `/rules` 部分 `/cache`

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

## 為清單版本v3配置Dispatcher{#configuring-dispatcherv3}

請確保允許在發佈實例前面的調度程式中使用這些篩選器和快取規則，以便螢幕正常工作。

### 清單版本v3的先決條件{#prerequisites3}

請確保在為AEM Screens配置Dispatcher（清單版本v3）之前遵循以下兩個先決條件：

* 確保您正在使用 `v3 manifests`。 導航到 `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` 確保 `Enable ContentSync Cache` 複選框。

* 確保在以下位置配置了調度程式刷新代理 `/etc/replication/agents.publish/dispatcher1useast1Agent` 在發佈實例中。

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

* 添加 `/allowAuthorized "1"` 至 `/cache` 部分 `publish_farm.any`。

* 所有螢幕播放器都將使用經過驗證的會話AEM連接到（作者/發佈）。 現成的Dispatcher不快取這些URL，因此我們應啟用這些URL。

* 添加 `statfileslevel "10"` 至 `/cache` 部分 `publish_farm.any`
這將支援從快取域快取多達10個級別，並在發佈內容時相應失效，而不是使所有內容失效。 根據內容結構的深度，隨時更改此級別

* 將以下內容添加到 `/invalidate section in publish_farm.any`

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* 將以下規則添加到 `/rules` 部分 `/cache` 在 `publish_farm.any` 或包含在 `publish_farm.any`:

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

### 添加segments.js的無效規則 {#invalidsegmentjs}

如果您正在與AEM Screens一起使用定向活動，則 `segments.js file` 在上添加和發佈新段時，調度程式提供的服務需要失效AEM。 如果沒有此無效規則，新的目標市場活動將無法在螢幕播放器上運行（它將顯示預設內容）。

* 將無效規則添加到 `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`。 以下是要添加的規則：

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

* 此規則確保 `segments.js` 檔案無效，修改後將讀取最新檔案。

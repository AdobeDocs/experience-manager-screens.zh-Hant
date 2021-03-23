---
title: Dispatcher Configurations forAEM Screens
seo-title: Dispatcher Configurations forAEM Screens
description: 本頁重點介紹為AEM Screens項目配置調度程式的指導方針。
seo-description: 本頁重點介紹為AEM Screens項目配置調度程式的指導方針。
feature: 管理畫面
role: 開發人員、商業從業人員
level: 中級
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 3%

---


# AEM Screens的調度器配置{#dispatcher-configurations-for-aem-screens}

Dispatcher 是 Adobe Experience manager 的快取和/或負載平衡工具。

下頁提供了為AEM Screens項目配置調度程式的指導。

>[!NOTE]
>
>如果調度程式可用，則可以通過在調度程式規則中進行過濾來阻止與註冊servlet的連接。
>
>如果沒有調度程式，請禁用OSGi元件清單中的註冊servlet。

## 先決條件{#pre-requisites}

在為AEM Screens項目配置調度程式之前，您必須具備Dispatcher的先前知識。

有關詳細資訊，請參閱[配置Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html)。

## 設定 Dispatcher {#configuring-dispatcher}

AEM Screens播放器／裝置也使用驗證的作業來存取發佈例項中的資源。 因此，當您有多個發佈例項時，請求應一律前往相同的發佈例項，如此驗證的作業階段就對來自AEM Screens播放器／裝置的所有請求有效。

按照以下步驟為AEM Screens項目配置調度程式。

### 啟用粘滯會話{#enable-sticky-session}

如果您想使用由單一發送器前端的多個發佈實例，則必須更新`dispatcher.any`檔案以啟用粘性

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

如果您有一個發佈實例由一個調度程式前置，則啟用調度程式的粘滯性將無濟於事，因為負載平衡器可能會向調度程式發送每個請求。 在這種情況下，按一下&#x200B;**粘著**&#x200B;欄位中的&#x200B;**啟用** ，以在負載平衡器級別啟用它，如下圖所示：

![影像](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

例如，如果您使用AWS ALB，請參閱[應用程式負載平衡器](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html)的目標組，以在ALB級別啟用粘性。 1天的黏性。

### 步驟1:配置客戶端標題{#step-configuring-client-headers}

將下列內容新增至`/clientheaders`區段：

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 步驟2:配置螢幕過濾器{#step-configuring-screens-filters}

若要設定「畫面」篩選，請將下列項目新增至&#x200B;***/filter***。

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

### 步驟3:禁用Dispatcher快取{#step-disabling-dispatcher-cache}

停用&#x200B;***/content/screens path***&#x200B;的Dispatcher caching。

畫面播放器使用已驗證的作業，因此分派器不會快取任何畫面播放器對`channels/assets`的要求。

若要啟用資產的快取，以便從分派器快取中提供資產，您必須：

* 在`/cache`節中添加`/allowAuthorization 1`
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

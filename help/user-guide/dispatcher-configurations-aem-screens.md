---
title: AEM畫面的Dispatcher Configurations
seo-title: AEM畫面的Dispatcher Configurations
description: 本頁反白說明為AEM Screens專案設定分派程式的准則。
seo-description: 本頁反白說明為AEM Screens專案設定分派程式的准則。
translation-type: tm+mt
source-git-commit: 37025002d02603ab8a5c571086524be858389557
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 5%

---


# AEM畫面的Dispatcher Configurations{#dispatcher-configurations-for-aem-screens}

Dispatcher 是 Adobe Experience manager 的快取和/或負載平衡工具。

以下頁面提供為AEM Screens專案設定分派程式的准則。

>[!NOTE]
>
>如果調度程式可用，則可以通過在調度程式規則中進行過濾來阻止與註冊servlet的連接。
>
>如果沒有調度程式，請禁用OSGi元件清單中的註冊servlet。

## 先決條件 {#pre-requisites}

在您為AEM Screens專案設定分派程式之前，您必須具備Dispatcher的先前知識。

有關詳細 [資訊，請參閱Configuring Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) 。

## 設定 Dispatcher {#configuring-dispatcher}

請依照下列步驟，為AEM Screens專案設定分派程式。

### 啟用嚴格作業 {#enable-sticky-session}

如果任何人想要將多個發佈實例與dispatcher一起使用，則必須更新其dispatcher.any檔案。

```xml
/stickyConnections {
  /paths
  {
    "/content/screens"
    "/home/users/screens"
    "/libs/granite/csrf/token.json"
  }
}
```

### 步驟1:配置客戶端標題 {#step-configuring-client-headers}

將下列內容新增至 `/clientheaders`區段：

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 步驟2:設定畫面篩選 {#step-configuring-screens-filters}

若要設定「畫面」篩選，請將下列新增至 ***/篩選***。

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

### 步驟3:禁用Dispatcher快取 {#step-disabling-dispatcher-cache}

停用 ***/content/screens路徑的Dispatcher快取***。

畫面播放器使用已驗證的作業，因此分派器不會快取任何畫面播放器的要求 `channels/assets`。

若要啟用資產的快取，以便從分派器快取中提供資產，您必須：

* 新增 `/allowAuthorization 1` 至區 `/cache` 段
* 將下列規則新增至 `/rules` 的區段 `/cache`

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

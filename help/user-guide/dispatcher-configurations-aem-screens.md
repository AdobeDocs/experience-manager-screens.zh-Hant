---
title: AEM畫面的Dispatcher Configurations
seo-title: AEM畫面的Dispatcher Configurations
description: 本頁反白說明為AEM Screens專案設定分派程式的准則。
seo-description: 本頁反白說明為AEM Screens專案設定分派程式的准則。
uuid: ec5219b7-73f9-4026-99e5-e4a02201b128
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 1b1a36a4-4f95-41e3-b0a8-74249efb0119
docset: aem65
translation-type: tm+mt
source-git-commit: 9bee12b69ae85e84572b6f9e8c70f792895d9a32

---


# AEM畫面的Dispatcher Configurations{#dispatcher-configurations-for-aem-screens}

Dispatcher 是 Adobe Experience manager 的快取和/或負載平衡工具。

以下頁面提供為AEM Screens專案設定分派程式的准則。

>[!NOTE]
>如果調度程式可用，則可以通過在調度程式規則中進行過濾來阻止與註冊servlet的連接。
>如果沒有調度程式，請禁用OSGi元件清單中的註冊servlet。

## 先決條件 {#pre-requisites}

在您為AEM Screens專案設定分派程式之前，您必須具備Dispatcher的先前知識。

有關詳細 [資訊，請參閱Configuring Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) 。

## 設定 Dispatcher {#configuring-dispatcher}

請依照下列步驟，為AEM Screens專案設定分派程式。

### 步驟1:配置客戶端標題 {#step-configuring-client-headers}

將下列內容新增至 `/clientheaders`區段：

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 步驟2:設定畫面篩選 {#step-configuring-screens-filters}

若要設定「畫面」篩選，請將下列新增至 ***/篩選&#x200B;***。

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0204 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0205 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0206 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0207 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0208 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0209 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0210 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### 步驟3:禁用Dispatcher快取 {#step-disabling-dispatcher-cache}

停用 ***/content/screens路徑的Dispatcher快取&#x200B;***。

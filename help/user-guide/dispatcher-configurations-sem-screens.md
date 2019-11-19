---
title: AEM畫面的Dispatcher Configurations
seo-title: AEM畫面的Dispatcher Configurations
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: ea68ca72-bbe7-42d5-9043-97aea7edcd6e
contentOwner: jsyal
discoiquuid: 046ec5ae-600d-422f-aa59-c39f16cf71de
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# AEM畫面的Dispatcher Configurations{#dispatcher-configurations-for-aem-screens}

Dispatcher 是 Adobe Experience manager 的快取和/或負載平衡工具。

以下頁面提供為AEM Screens專案設定分派程式的准則。

## 先決條件 {#pre-requisites}

在您為AEM Screens專案設定分派程式之前，您必須具備Dispatcher的先前知識。

有關詳細 **[資訊，請參閱Configuring Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html)** 。

## 設定 Dispatcher {#configuring-dispatcher}

請依照下列步驟，為AEM Screens專案設定分派程式。

### 步驟1:配置客戶端標題 {#step-configuring-client-headers}

將下列內容新增至區 `/clientheaders` 段

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 步驟2:設定畫面篩選 {#step-configuring-screens-filters}

若要設定「畫面」篩選，請將下列新增至 ***/篩選***。

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

停用 ***/content/screens路徑的Dispatcher快取***。

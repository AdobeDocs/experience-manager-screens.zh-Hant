---
title: 配置和部署AEM Screens
seo-title: Configuring and Deploying Screens
description: 該AEM Screens播放器可用於Android、Chrome OS、iOS和Windows。 本頁介紹了AEM Screens的配置和部署，並總結了播放器設備的h/w選擇准則。
seo-description: The AEM Screens player is available for Android, Chrome OS, iOS, and Windows. This page describes the configuration and deployment of AEM Screens and also summarizes the h/w selection guidelines for player device.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
role: Admin
level: Intermediate
exl-id: 8cf4240c-1d6c-441d-b8a0-f01516455543
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 0%

---

# 配置和部署AEM Screens {#configuring-and-deploying-aem-screens}

此頁顯示如何在設備上安裝和配置螢幕播放器。

## 伺服器配置 {#server-configuration}

>[!NOTE]
>
>**重要**:
>
>AEM Screens播放器不使用跨站點請求偽造(CSRF)令牌。 因此，為了配置和服AEM務器以便為AEM Screens使用，請通過允許空引用站跳過引用站篩選器。

## 運行狀況檢查框架 {#health-check-framework}

運行狀況檢查框架允許用戶在運行AEM Screens項目之前檢查是否設定了兩個必需的配置。

它允許用戶驗證以下兩個配置檢查以運行AEM Screens項目，即檢查以下兩個篩選器的狀態：

1. **允許空引用**
2. **htps**

按照以下步驟檢查是否為AEM Screens啟用了以下兩個重要配置：

1. 導航到 [Adobe Experience ManagerWeb控制台Sling運行狀況檢查](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=)。

   ![資產](assets/health-check1.png)


2. 按一下 **執行所選運行狀況檢查** 運行上述兩個屬性的驗證。

   如果兩個篩選器都已啟用，則 **螢幕配置運行狀況服務** 顯示 **結果** 如 **確定** 兩個配置均已啟用。

   ![資產](assets/health-check2.png)

   如果禁用一個或兩個篩選器，則會顯示用戶的警報，如下圖所示。

   以下警報顯示是否禁用了這兩個篩選器：
   ![資產](assets/health-check3.png)

>[!NOTE]
>
>* 啟用 **Apache Sling引用篩選器**，請參閱 [允許空引用者請求](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests)。
>* 啟用 **HTTP** 服務，請參閱 [基於Apache Felix Jetty的HTTP服務](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service)。


### 必備條件 {#prerequisites}

以下要點有助於配置和服AEM務器以便為AEM Screens使用。

#### 允許空引用者請求 {#allow-empty-referrer-requests}

1. 導航到 **Adobe Experience ManagerWeb控制台配置** 通AEM過實例 — >錘表徵圖 —  **操作** —> **Web控制台**。

   ![影像](assets/config/empty-ref1.png)

1. **Adobe Experience ManagerWeb控制台配置** 的上界。 搜索Sling引用者。

   要搜索吊具引用屬性，請按 **命令+F** 為 **Mac** 和 **控制項+F** 為 **窗口**。

1. 檢查 **允許空** 的下界。

   ![影像](assets/config/empty-ref2.png)

1. 按一下 **保存** 啟用Apache Sling引用過濾器允許空。


#### 基於Apache Felix Jetty的HTTP服務 {#allow-apache-felix-service}

1. 導航到 **Adobe Experience ManagerWeb控制台配置** 通AEM過實例 — >錘表徵圖 —  **操作** —> **Web控制台**。

   ![影像](assets/config/empty-ref1.png)

1. **Adobe Experience ManagerWeb控制台配置** 的上界。 搜索基於Apache Felix Jetty的HTTP服務。

   要搜索此屬性，請按 **命令+F** 為 **Mac** 和 **控制項+F** 為 **窗口**。

1. 檢查 **啟用HTTP** 的下界。

   ![影像](assets/config/config-1.png)

1. 按一下 **保存** 啟用 *http* 服務。

#### 為AEM Screens啟用觸摸UI {#enable-touch-ui-for-aem-screens}

AEM Screens需要TOUCH UI，不會與Adobe Experience Manager的CLASSIC UI(AEM)配合。

1. 導航到 *&lt;yourauthorinstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. 確保 **預設創作UI模式** 設定為 **觸摸**，如下圖所示

或者，也可以使用AuthorInstance執行相同的設定 *->* 工具（錘表徵圖） — > **操作** -> **Web控制台** 並搜索 **WCM創作UI模式服務**。

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>您始終可以使用用戶首選項為特定用戶啟用經典用戶介面。

#### 在AEMNOSAMPLECONTENT運行模式中 {#aem-in-nosamplecontent-runmode}

在生AEM產中運行使用 **NOSAMPLECONTENT** 運行模式。 刪除 *X — 幀 — 選項=SAMEORIGIN* 標題（在其他響應標題部分中）

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`。

這是AEM Screens播放器播放線上頻道所必需的。

#### 密碼限制 {#password-restrictions}

對 ***設備服務實施***，您不必刪除密碼限制。

您可以配置 ***設備服務實施*** 在為螢幕設備用戶建立密碼時，從以下連結啟用密碼限制：

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

按照以下步驟配置 ***設備服務實施***:

1. 導航到 **Adobe Experience ManagerWeb控制台配置** 通AEM過實例 — >錘表徵圖 —  **操作** —> **Web控制台**。

1. **Adobe Experience ManagerWeb控制台配置** 的上界。 搜索 *設備服務*。 要搜索屬性，請按 **命令+F** macOS **控制項+F** MicrosoftWindows。

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### 調度程式配置 {#dispatcher-configuration}

要瞭解如何為AEM Screens項目配置調度程式，請參閱 [為AEM Screens項目配置Dispatcher](dispatcher-configurations-aem-screens.md)。

#### Java編碼 {#java-encoding}

設定 ***Java編碼*** 到Unicode。 比如說， *Dfile.encoding=Cp1252* 不會奏效。

>[!NOTE]
>**建議：**
>建議在生產使用中使用HTTPS用於AEM Screens伺服器。

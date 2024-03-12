---
title: Screens Feature Pack 20240215發行說明
description: 請詳閱本頁，以取得2024年2月15日發行的AEM Screens Feature Pack 20240215資訊。
feature: Feature Pack
role: Developer
level: Intermediate
source-git-commit: d5b94814df33f00e23fcd22e85e50d6f02947d45
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 5%

---

# Feature Pack 20240215發行說明 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>建議您升級至6.5 Adobe Experience Manager (AEM 6.5)的最新版本。 我們可以從取得最新版本資訊 [此處](https://experienceleague.adobe.com/docs/experience-manager-65/content/release-notes/release-notes.html?lang=en)

## 可用性 {#availability}

AEM Screens已發行AEM 6.5 Feature Pack 11.3。

若要下載AEM Screens 6.5.11.3版的最新Feature Pack，請前往 [軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 使用您的Adobe ID。 瀏覽至 **Adobe Experience Manager** 標籤並搜尋 **Screens** 以取得標題為 **AEM 6.5畫面FP11.3**.

## 發行日期 {#release-date}

AEM Screens Feature Pack 20240215的發行日期為2024年2月15日。

### 新增功能 {#what-is-new}

此版本僅包含安全性修正。

### 錯誤修正 {#bug-fixes}

* 已移除先前在FP11.1中針對XSS （位於）提供的修正的切換檢查 `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* XSS問題位於 `libs/screens/dcc/components/clientlibs/columnviewnavigatorshim.js`. (SCRNS-3973)

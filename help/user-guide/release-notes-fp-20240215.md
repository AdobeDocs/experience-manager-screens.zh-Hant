---
title: Screens Feature Pack 20240215發行說明
description: 進一步瞭解2024年2月15日發行的AEM Screens Feature Pack 20240215。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e4149f5b-42c0-43c8-b275-ecbe90104a98
source-git-commit: fe4f7d593ccea91f6109a0c759aea3faa37ae471
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 5%

---

# Feature Pack 20240215發行說明 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobe建議您升級至6.5 Adobe Experience Manager (AEM 6.5)的最新版本。 您可以透過取得最新版本資訊 [此處](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/release-notes/release-notes).

## 可用性 {#availability}

AEM Screens已發行AEM 6.5 Feature Pack 11.3。

若要下載AEM Screens 6.5.11.3版的最新Feature Pack，請前往 [軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 使用您的Adobe ID。 導覽至 **Adobe Experience Manager** 標籤並搜尋 **Screens** 以取得標題為 **AEM 6.5畫面FP11.3**.

## 發行日期 {#release-date}

AEM Screens Feature Pack 20240215的發行日期為2024年2月15日。

### 新增功能 {#what-is-new}

此版本僅包含安全性修正。

### 錯誤修正 {#bug-fixes}

* 已移除先前在FP11.1中針對XSS （位於）提供的修正的切換檢查 `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* XSS問題位於 `libs/screens/dcc/components/clientlibs/columnviewnavigatorshim.js`. (SCRNS-3973)

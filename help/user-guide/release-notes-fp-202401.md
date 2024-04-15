---
title: Screens Feature Pack 202401發行說明
description: 瞭解2024年1月2日發行的AEM Screens Feature Pack 202401。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
source-git-commit: 10c168cd00b79964d229e3d2a14049e799d89d77
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 4%

---

# Feature Pack 202401發行說明 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobe建議您升級至6.5 Adobe Experience Manager (AEM 6.5)的最新版本。 從取得最新版本資訊 [此處](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/release-notes/release-notes)

## 可用性 {#availability}

AEM Screens已發行AEM 6.5 Feature Pack 11.1 。

若要下載AEM Screens 6.5.11.1版的最新Feature Pack，請前往 [軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 使用您的Adobe ID。 瀏覽至 **Adobe Experience Manager** 標籤並搜尋 **Screens** 以取得標題為 **AEM 6.5 Screens FP11.1**.

## 發行日期 {#release-date}

AEM Screens Feature Pack 202204的發行日期為2024年1月2日。

### 新增功能 {#what-is-new}

此版本僅包含安全性修正。

### 錯誤修正 {#bug-fixes}

* AEM Screens裝置的「閒置文字」欄位發生XSS問題。 (SCRNS-2614)

* XSS問題位於 `screens/dashboard/device.html` 透過 `Clear cache` 動作對話方塊。 (SCRNS-2632)

* Screens播放器設定中的XSS問題位於 `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* 裝置刪除時，裝置標題中儲存的XSS便會觸發。 (SCRNS-2653)

* XSS問題位於 `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* 透過引數反映的XSS `item` 在 `/screens/register-device-wizard.html`. (SCRNS-2670)

* 在中反映的XSS `screens/dashboard/device.html` 透過 `returnPage` 引數。 (SCRNS-3056)

* 在assign-device-wizard.html上開啟「重新導向」。 (SCRNS-3444)

* 在裝置控制面板上開啟重新導向。 (SCRNS-3443)

* XSS問題位於 `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* 修正、遺失週期性排程和新增排程按鈕：在頻道排程中發現的問題。 (SCRNS-2739)

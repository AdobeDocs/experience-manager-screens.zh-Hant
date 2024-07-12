---
title: Screens Feature Pack 202401發行說明
description: 瞭解2024年1月2日發行的AEM Screens Feature Pack 202401。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 4%

---

# Feature Pack 202401發行說明 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobe建議您升級至6.5 Adobe Experience Manager (AEM 6.5)的最新版本。 從[這裡](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/release-notes/release-notes)取得最新版本資訊。

## 可用性 {#availability}

AEM Screens已發行AEM 6.5 Feature Pack 11.1。

您可以使用您的Adobe ID，從[軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載AEM Screens 6.5.11.1版的最新Feature Pack。 瀏覽至&#x200B;**Adobe Experience Manager**&#x200B;索引標籤並搜尋&#x200B;**Screens**，以取得標題為&#x200B;**AEM 6.5 Screens FP11.1**&#x200B;的最新功能套件。

## 發行日期 {#release-date}

AEM Screens Feature Pack 202204的發行日期為2024年1月2日。

### 新增功能 {#what-is-new}

此版本僅包含安全性修正。

### 錯誤修正 {#bug-fixes}

* AEM Screens裝置的「閒置文字」欄位發生XSS問題。 (SCRNS-2614)

* 透過`Clear cache`動作對話方塊，`screens/dashboard/device.html`出現XSS問題。 (SCRNS-2632)

* 在`libs/screens/player/browser/firmware.html`的Screens播放器設定中出現XSS問題。 (SCRNS-2652)

* 裝置刪除時，裝置標題中儲存的XSS便會觸發。 (SCRNS-2653)

* `/libs/screens/core/components/device/info.json.html`的XSS問題。 (SCRNS-2659)

* 在`/screens/register-device-wizard.html`處反映引數`item`的XSS。 (SCRNS-2670)

* 透過`returnPage`引數在`screens/dashboard/device.html`中反映XSS。 (SCRNS-3056)

* 在assign-device-wizard.html上開啟「重新導向」。 (SCRNS-3444)

* 在裝置控制面板上開啟重新導向。 (SCRNS-3443)

* `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`的XSS問題。 (SCRNS-3459)

* 修正、遺失週期性排程和新增排程按鈕：在頻道排程中發現的問題。 (SCRNS-2739)

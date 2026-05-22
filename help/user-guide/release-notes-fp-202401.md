---
title: Screens Feature Pack 202401發行說明
description: 瞭解2024年1月2日發行的AEM Screens Feature Pack 202401。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
TQID: https://experienceleague.adobe.com/b6ZM04Vl6ozehx8E-y9iV1KAo-FI7DZSpDcHvhudkMI
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 248
ht-degree: 10%

---

# Feature Pack 202401發行說明 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobe建議您升級至6.5 Adobe Experience Manager (AEM 6.5)的最新版本。 從[這裡](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/release-notes/release-notes)取得最新版本資訊。

## 可用性 {#availability}

AEM Screens已發行AEM 6.5 Feature Pack 11.1。

您可以使用您的Adobe ID，從[軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載AEM Screens 6.5.11.1發行版的最新Feature Pack。 導覽至&#x200B;**Adobe Experience Manager**&#x200B;標籤並搜尋&#x200B;**Screens**，以取得標題為&#x200B;**AEM 6.5 Screens FP11.1**&#x200B;的最新功能套件。

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

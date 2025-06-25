---
title: Screens Feature Pack 20250327發行說明
description: 深入瞭解於2025年3月27日發行的AEM Screens Feature Pack 20250327。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: cadd83cd-fe64-436d-b3fd-6d72b9565885
source-git-commit: 6cdf350fa4e45b816d50b64252b8ed6d5e0904d0
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 3%

---

# Feature Pack 20250327發行說明 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobe建議您升級至6.5 Adobe Experience Manager (AEM 6.5)的最新版本。 您可以從[這裡](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/release-notes/release-notes)取得最新版本資訊。
>&#x200B;>Adobe建議您搭配SP(servicepack) >= 21使用FP11.6。

## 可用性 {#availability}

AEM Screens已發行AEM 6.5 Feature Pack 11.6。

您可以使用您的Adobe ID，從[軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載AEM Screens 6.5.11.6發行版的最新Feature Pack。 導覽至&#x200B;**Adobe Experience Manager**&#x200B;標籤並搜尋&#x200B;**Screens**，以取得標題為&#x200B;**AEM 6.5 Screens FP11.6**&#x200B;的最新功能套件。

## 發行日期 {#release-date}

AEM Screens Feature Pack 20250327的發行日期為2025年3月27日。

### 新增功能 {#what-is-new}

* 此版本修正了使用者使用Service Pack 21及更高版本時面臨的套件衝突。

* 此版本修正SP22及更高版本的卡片檢視問題。

* 在AEM Screens Players上&#x200B;**更新**
   * Linux架構的AEM Screens Player已正式淘汰。 建議使用者移轉至AEM Screens支援的其他作業系統。
   * Android型AEM Screens Player不再有進一步的更新或增強功能。 建議使用者移轉至AEM Screens支援的替代作業系統。

### 錯誤修正 {#bug-fixes}

* Service Pack 21和Screens Feature Pack出現套件衝突。 (SCRNS-4638)

* Screens Dashboard無法運作。 (SCRNS-4749)

* /libs/screens/dcc/components/dashboard/clientlibs/device-clear-cache.js上的XSS問題(SCRNS-4761)

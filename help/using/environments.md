---
title: '[!UICONTROL AEM Screens]的環境'
seo-title: '[!UICONTROL AEM Screens]的環境'
description: 本頁面說明AEM Screens專案的環境。
seo-description: 本頁面重點說明AEM Screens專案的環境。
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 4%

---


# 環境 {#environments}

預先決定用戶端具有和將預期您使用的AEM環境，兩者皆適用於&#x200B;*development*&#x200B;和&#x200B;*deployment*。

>[!NOTE]
>
>AEM Screens需要數個套件，專案才能運作。 所有環境都應執行相同版本的Adobe Experience Manager。

請依照下列准則，為您的AEM Screens專案設定環境：

1. 針對您的Adobe Experience Manager版本執行下列套件的最新版本：

   * **AEM Service Pack**
   * **Screens Feature Pack**
   * **AEM Cumulative Fix Pack**

1. 識別所需的任何開發套件（例如WCM核心元件）或第三方工具套件（例如SAP Hybris）。

1. 在您的本機開發環境上安裝相同的軟體套件。

1. 指示您的用戶端在其所有QA、預備和生產伺服器上採用相同的設定。 不匹配的伺服器配置在部署和測試時會造成問題。

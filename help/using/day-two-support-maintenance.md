---
title: 第二天支援與維護
description: 瞭解AEM Screens的第二天支援與維護。
exl-id: 2b5511ff-c8f4-4ea3-8a65-f17f3a1ec39b
TQID: https://experienceleague.adobe.com/IMuRCxE7v8DyK-T4Q3lehhclfgGtu0VIHyIsODOpEzA
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 186
ht-degree: 0%

---

# 第二天平台支援與維護 {#day-two-support-maintenance}

>[!IMPORTANT]
>此內容對AEM內部部署/AMS （AEM 6.5LTS和AEM 6.5）有效。 如需AEM as a Cloud Service Screens內容，請參閱[AEM as a Cloud Service指南](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

AEM Screens需要數個套件才能讓專案運作。 所有環境都必須執行相同版本的Adobe Experience Manager。

遵循專案開發階段第二天的支援和維護准則：

1. 針對您的Adobe Experience Manager版本執行以下套件的最新版本：

   * **AEM Service Pack**
   * **Screens Feature Pack**
   * **AEM Cumulative Fix Pack**

1. 識別所需的任何開發套件（例如WCM核心元件）或第三方工具套件（例如SAP Hybris）。

1. 將相同的軟體套件安裝至本機開發環境。

1. 指示您的使用者端在其所有QA、Stage及生產伺服器上採用相同的設定。 不相符的伺服器設定會在部署和測試時造成問題。


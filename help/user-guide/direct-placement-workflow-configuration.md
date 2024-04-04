---
title: 直接放置工作流程設定
seo-title: Direct Placement Workflow Configuration
description: 本頁面主要說明直接放置工作流程設定。
seo-description: This page highlights Direct Placement Workflow Configuration.
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 1%

---


# 直接放置工作流程設定 {#direct-placement-workflow}

請依照本頁面的說明了解如何設定資產工作流程，好讓您以程式設計方式將資產插入預先定義的AEM Screens管道。

本節涵蓋下列主題：

* 概觀
* 設定直接放置工作流程

## 概觀 {#overview}

直接放置工作流程設定會將AEM Screens專案頻道對應至資產中的特定資料夾，並可在該資料夾中放置任何資產。 建議您觸發大量離線更新，以便完成發佈。

或者，作為內容作者，您可以手動按一下 **更新離線內容**.

>[!NOTE]
>
>若要瞭解如何使用大量離線更新，請參閱 [內容更新即服務](/help/user-guide/content-update-as-a-service.md).

## 設定直接放置工作流程 {#configuring-workflow}

>[!IMPORTANT]
>
>開始設定前，您必須先安裝 [示範套件](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip). 安裝套件後，您應該就能從AEM執行個體>工具（圖示） >檢視及存取套件 **工作流程** > **工作流程模型**.

請依照下列步驟設定直接放置工作流程：

1. 從您的AEM執行個體瀏覽至AEM Screens，並建立標題為 **資產工作流程**.

1. 建立標題為 **Workflow-Assets** 在 **頻道** 資料夾。


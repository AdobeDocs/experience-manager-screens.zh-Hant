---
title: 直接放置工作流程設定
description: 本頁面主要說明直接放置工作流程設定。
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 1%

---


# 直接放置工作流程設定 {#direct-placement-workflow}

請依照本頁面的說明進行，以便瞭解如何設定資產工作流程，讓您以程式設計方式將資產插入預先定義的AEM Screens管道。

本節涵蓋下列主題：

* 概觀
* 設定直接放置工作流程

## 概觀 {#overview}

直接放置工作流程設定會將AEM Screens專案頻道對應至資產中的特定資料夾，並可在該資料夾中放置任何資產。 Adobe建議您觸發大量離線更新，以完成發佈。

或者，作為內容作者，您可以手動選擇 **更新離線內容**.

>[!NOTE]
>
>若要瞭解如何使用大量離線更新，請參閱 [內容更新即服務](/help/user-guide/content-update-as-a-service.md).

## 設定直接放置工作流程 {#configuring-workflow}

>[!IMPORTANT]
>
>開始設定前，請先安裝 `[Demo  Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)`. 安裝套件後，您應該能夠從AEM執行個體>工具（圖示） >檢視及存取套件 **工作流程** > **工作流程模型**.

請依照下列步驟設定直接放置工作流程：

1. 從您的AEM執行個體瀏覽至AEM Screens，並建立標題為 **資產工作流程**.

1. 建立標題為 **Workflow-Assets** 在 **頻道** 資料夾。


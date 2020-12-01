---
title: '直接放置工作流程設定 '
seo-title: 直接放置工作流程設定
description: 此頁面反白顯示「直接位置工作流程設定」。
seo-description: 此頁面反白顯示「直接位置工作流程設定」。
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# 直接放置工作流配置{#direct-placement-workflow}

請依照本頁進一步瞭解如何設定資產工作流程，讓您以程式設計方式將資產插入預先定義的AEM Screens頻道。

本節涵蓋下列主題：

* 概覽
* 設定直接位置工作流程

## 概覽 {#overview}

「直接位置工作流程設定」會將AEM Screens專案頻道對應至資產中的特定檔案夾，並允許將任何資產放置在該檔案夾中。 建議觸發大量離線更新以完成出版物。

或者，身為內容作者，您可以手動按一下「更新離線內容」。****

>[!NOTE]
>
>要瞭解如何使用大量離線更新，請參閱[內容更新為服務](/help/user-guide/content-update-as-a-service.md)。

## 配置直接放置工作流{#configuring-workflow}

>[!IMPORTANT]
>
>在啟動配置之前，必須安裝[Demo Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)。 在安裝套件後，您應能夠從AEM實例—>工具（圖示）—> **Workflow** —> **Workflow Models**&#x200B;檢視並存取它。

請依照下列步驟來設定直接放置工作流程：

1. 從您的AEM例項導覽至「AEM畫面」，並建立標題為&#x200B;**資產工作流程**&#x200B;的「畫面」專案。

1. 在&#x200B;**Channels**&#x200B;資料夾下建立標題為&#x200B;**Workflow-Assets**&#x200B;的渠道。


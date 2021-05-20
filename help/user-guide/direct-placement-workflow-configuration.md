---
title: '直接放置工作流程設定 '
seo-title: 直接放置工作流程設定
description: 此頁面會反白顯示「直接放置工作流程設定」。
seo-description: 此頁面會反白顯示「直接放置工作流程設定」。
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# 直接放置工作流配置{#direct-placement-workflow}

請依照本頁了解如何設定資產工作流程，以供您以程式設計方式將資產插入預先定義的AEM Screens管道。

本節涵蓋下列主題：

* 概覽
* 設定直接放置工作流程

## 概覽 {#overview}

直接放置工作流程設定會將AEM Screens專案通道對應至資產中的特定資料夾，並允許放置該資料夾中的任何資產。 建議您觸發大量離線更新，以完成發佈。

或者，身為內容作者，您可以手動按一下&#x200B;**更新離線內容**。

>[!NOTE]
>
>若要了解如何使用大量離線更新，請參閱[Content Update As a Service](/help/user-guide/content-update-as-a-service.md)。

## 配置直接放置工作流{#configuring-workflow}

>[!IMPORTANT]
>
>開始配置之前，必須安裝[Demo Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)。 安裝軟體包後，您應該能夠從AEM實例 — >工具（表徵圖） — > **工作流** —> **工作流模型**&#x200B;查看和訪問該軟體包。

請依照下列步驟，設定直接刊登版位工作流程：

1. 從您的AEM例項導覽至AEM Screens，並建立標題為&#x200B;**Asset Workflow**&#x200B;的Screens專案。

1. 在&#x200B;**Channels**&#x200B;資料夾下，建立標題為&#x200B;**Workflow-Assets**&#x200B;的管道。


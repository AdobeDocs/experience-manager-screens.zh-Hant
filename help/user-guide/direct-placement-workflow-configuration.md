---
title: 直接放置工作流配置
seo-title: Direct Placement Workflow Configuration
description: 此頁突出顯示直接放置工作流配置。
seo-description: This page highlights Direct Placement Workflow Configuration.
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# 直接放置工作流配置 {#direct-placement-workflow}

按照此頁瞭解如何配置資產工作流，該工作流允許您以寫程式方式將資產插入預定義的AEM Screens渠道。

本節介紹以下主題：

* 概觀
* 配置直接放置工作流

## 概觀 {#overview}

直接放置工作流配置將AEM Screens項目通道映射到資產中的特定資料夾，並允許放置該資料夾中的任何資產。 建議觸發批量離線更新以完成發佈。

或者，作為內容作者，您可以手動按一下 **更新離線內容**。

>[!NOTE]
>
>要瞭解如何使用批量離線更新，請參閱 [內容更新為服務](/help/user-guide/content-update-as-a-service.md)。

## 配置直接放置工作流 {#configuring-workflow}

>[!IMPORTANT]
>
>在啟動配置之前，必須安裝 [演示包](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)。 安裝軟體包後，您應該能夠從實例查看和訪問AEM它 — >工具（表徵圖） — > **工作流** —> **工作流模型**。

按照以下步驟配置直接放置工作流：

1. 從實例導航到AEM ScreensAEM，然後建立標題為 **資產工作流**。

1. 建立標題為 **工作流 — 資產** 在 **頻道** 的子菜單。


---
title: 建立視頻填充工作流
seo-title: Creating a Video Padding Workflow
description: 按照此頁瞭解如何在工作流中為資產建立視頻填充。
seo-description: Follow this page to learn about creating a video padding in the workflow for your assets.
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 16180f96-2855-4250-9d55-24ed77a908b7
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# 建立視頻填充工作流 {#creating-a-video-padding-workflow}

本節介紹以下主題：

* **概觀**
* **必備條件**
* **建立視頻填充工作流**
   * **建立工作流**
   * **在AEM Screens項目中使用工作流**

* **驗證工作流的輸出**

## 概觀 {#overview}

以下用例涉及放置視頻(例如：在顯示器為1920 x 1080且視頻被放置在0x0（左上）的通道中。 不應以任何方式拉伸或修改視頻，也不應使用 **封面** 的子菜單。

視頻將作為對象在像素1到像素1280之間和像素1到像素720之間向下顯示，其餘的通道將是預設顏色。

## 必備條件 {#prerequisites}

在為視頻建立工作流之前，請完成以下先決條件：

1. 在中上載視頻 **資產** 實例中的文AEM件夾
1. 建立AEM Screens項目(例如， **測試視頻格式副本**)和名為(**視頻呈現**)，如下圖所示：

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## 建立視頻填充工作流 {#creating-a-video-padding-workflow-1}

要建立視頻填充工作流，必須為視頻建立工作流，然後在AEM Screens項目渠道中使用該工作流。

按照以下步驟建立和使用工作流：

1. 建立工作流
1. 在AEM Screens項目中使用工作流

### 建立工作流 {#creating-a-workflow}

按照以下步驟為視頻建立工作流：

1. 導航到實AEM例，然後從側滑軌按一下工具。 選擇 **工作流** —> **模型** 的子菜單。

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. 按一下 **模型** —> **建立** —> **建立模型**。 輸入 **標題** (a) **視頻格式副本**) **名稱** 的 **添加工作流模型**。 按一下 **完成** 的子菜單。

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. 建立工作流模型後，選擇模型(**視頻格式副本**)，然後按一下 **編輯** 按鈕。

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. 拖放 **命令行** 元件。

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. 選擇 **命令行** ，然後開啟「屬性」對話框。

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. 選擇 **參數** 的子菜單。 **命令行 — 步驟屬性** 對話框。

   在 **MIME類型** (a) ***視頻/mp4***)和命令(***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=0:color=black&quot; cq5dam.video.fullhd-hp.mp4**)，以在 **命令** 的子菜單。

   請參閱 **MIME類型** 和 **命令** 注。

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. 選擇工作流(**視頻格式副本**) **啟動工作流** 開啟 **運行工作流** 對話框。

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. 在 **負載** (a) ***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***)並輸入 **標題** 如 ***運行視頻*** 按一下 **運行**。

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### 在AEM Screens項目中使用工作流 {#using-the-workflow-in-an-aem-screens-project}

按照以下步驟在您的AEM Screens項目中使用工作流：

1. 導航到AEM Screens項目(**測試視頻格式副本** —> **頻道** —>**視頻格式副本**)。

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. 按一下 **編輯** 按鈕。 拖放您最初上載到的視頻 **資產**。

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. 上傳視頻後，按一下 **預覽** 按鈕。

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## 驗證工作流的輸出 {#validating-the-output-for-the-workflow}

您可以通過以下方式驗證輸出：

* 檢查頻道中視頻的預覽
* 導航到 ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** CRXDE Lite中，如下圖所示：

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

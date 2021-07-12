---
title: 建立視訊填補工作流程
seo-title: 建立視訊填補工作流程
description: 請依照本頁面了解如何在資產的工作流程中建立影片填補。
seo-description: 請依照本頁面了解如何在資產的工作流程中建立影片填補。
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
feature: 製作畫面
role: Admin, Developer
level: Intermediate
exl-id: 16180f96-2855-4250-9d55-24ed77a908b7
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 0%

---

# 建立視訊填補工作流程 {#creating-a-video-padding-workflow}

本節涵蓋下列主題：

* **概覽**
* **必備條件**
* **建立視訊填補工作流程**
   * **建立工作流程**
   * **在AEM Screens專案中使用工作流程**

* **驗證工作流的輸出**

## 概覽 {#overview}

下列使用案例涉及放置視訊(範例：1280 x 720)，在顯示為1920 x 1080的通道中，將視頻放置在0x0（左上）。 視訊不應以任何方式延伸或修改，且請勿在視訊元件中使用&#x200B;**Cover**。

視頻將被顯示為從像素1到像素1280跨越像素1到像素720向下的對象，其餘的通道將是預設顏色。

## 必備條件 {#prerequisites}

建立視訊的工作流程之前，請先完成下列必要條件：

1. 在AEM例項的&#x200B;**Assets**&#x200B;資料夾中上傳視訊
1. 建立AEM Screens專案（例如&#x200B;**TestVideoRendition**）和名為(**VideoRendering**)的管道，如下圖所示：

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## 建立視訊填補工作流程 {#creating-a-video-padding-workflow-1}

若要建立視訊填補工作流程，您必須為視訊建立工作流程，然後在AEM Screens專案通道中使用相同的工作流程。

請依照下列步驟建立及使用工作流程：

1. 建立工作流程
1. 在AEM Screens專案中使用工作流程

### 建立工作流程 {#creating-a-workflow}

請依照下列步驟，為影片建立工作流程：

1. 導覽至您的AEM例項，然後按一下側邊欄中的「工具」。 選擇&#x200B;**工作流** —> **模型**&#x200B;以建立新模型。

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. 按一下&#x200B;**Models** —> **Create** —> **Create Model**。 在&#x200B;**添加工作流模型**&#x200B;中輸入&#x200B;**Title**（作為&#x200B;**VideoRendition**）和&#x200B;**名稱**。 按一下&#x200B;**Done**&#x200B;以新增工作流程模型。

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. 建立工作流模型後，請選擇模型(**VideoRendition**)，然後從操作欄按一下&#x200B;**Edit**。

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. 將&#x200B;**命令行**&#x200B;元件拖放到工作流中。

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. 選擇&#x200B;**命令行**&#x200B;元件並開啟屬性對話框。

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. 選擇&#x200B;**參數**&#x200B;頁簽以輸入&#x200B;**命令行 — 步驟屬性**&#x200B;對話框中的欄位。

   在&#x200B;**Mime類型**&#x200B;中輸入格式（如&#x200B;***video/mp4***），並輸入命令(***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=0:color=black&quot; cq5dam.video.hp-mp4***)，以在&#x200B;**命令**&#x200B;欄位中啟動工作流。

   請參閱以下注釋中&#x200B;**Mime類型**&#x200B;和&#x200B;**命令**&#x200B;的詳細資訊。

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. 選擇工作流(**VideoRenditions**)，然後從操作欄按一下&#x200B;**Start Workflow**&#x200B;以開啟&#x200B;**Run Workflow**&#x200B;對話框。

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. 在&#x200B;**Payload**(as ***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***)中選取資產路徑，然後輸入&#x200B;**Title**&#x200B;作為&#x200B;***RunVideo***，然後按一下&#x200B;**Run**。

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### 在AEM Screens專案中使用工作流程 {#using-the-workflow-in-an-aem-screens-project}

請依照下列步驟，使用AEM Screens專案中的工作流程：

1. 導覽至AEM Screens專案(**TestVideoRendition** —> **Channels** —>**VideoRendition**)。

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. 按一下動作列中的&#x200B;**編輯**。 拖放您最初上傳至&#x200B;**Assets**&#x200B;的視訊。

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. 上傳視訊後，按一下&#x200B;**預覽**&#x200B;以檢視輸出。

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## 驗證工作流的輸出 {#validating-the-output-for-the-workflow}

您可以透過下列方式驗證輸出：

* 檢查頻道中的視訊預覽
* 導覽至CRXDE Lite中的&#x200B;***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4***，如下圖所示：

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

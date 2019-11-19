---
title: 建立視訊填補工作流程
seo-title: 建立視訊填補工作流程
description: 請依照本頁進行，以瞭解如何在工作流程中建立資產的視訊間距。
seo-description: 請依照本頁進行，以瞭解如何在工作流程中建立資產的視訊間距。
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 建立視訊填補工作流程 {#creating-a-video-padding-workflow}

本節涵蓋下列主題：

* **綜覽**
* **必備條件**
* **建立視訊填補工作流程**
   * **建立工作流程**
   * **在AEM Screens專案中使用工作流程**

* **驗證工作流的輸出**

## 概覽 {#overview}

下列使用案例涉及放置視訊(範例：1280 x 720)，在顯示器為1920 x 1080且視訊放置於0x0（左上）的頻道中。 視訊不應以任何方式拉伸或修改，也不應在視訊元件中使 **用** 「封面」。

視訊會以物件的形式顯示，從像素1到像素1280橫跨像素1到像素720向下，而其餘的色版則為預設顏色。

## 必備條件 {#prerequisites}

在建立視訊工作流程之前，請先完成下列必要條件：

1. 在AEM例項的 **Assets** 檔案夾中上傳影片
1. 建立AEM Screens專案(例如 **TestVideoRendition**)和名為(**VideoRendering**)的頻道，如下圖所示：

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## 建立視訊填補工作流程 {#creating-a-video-padding-workflow-1}

若要建立視訊填補工作流程，您必須為視訊建立工作流程，然後在AEM Screens專案頻道中使用相同的工作流程。

請依照下列步驟來建立和使用工作流程：

1. 建立工作流程
1. 在AEM Screens專案中使用工作流程

### 建立工作流程 {#creating-a-workflow}

請依照下列步驟，為您的視訊建立工作流程：

1. 導覽至您的AEM例項，然後從側欄按一下工具。 選擇「 **工作流** 」(Workflow **)** —&gt;「模型」(Models)以建立新模型。

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. 按一下「 **模型** 」(Models **)—&gt;「創** 建 **」(Create**)—&gt;「建立模型」(Create Model)。 在「 **Workflow** Add Model Alignment」（工作流模型添加標題）中，輸入 **VideoRendition**(作為VideoRendition **)和****** Name（名稱）。 按一 **下「完成** 」(Done)以新增工作流程模型。

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. 建立工作流程模型後，選取模型(**VideoRendition**)，然後從動作列按一 **下「編輯** 」。

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. 將**命令行**元件拖放到工作流中。

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. 選取「命 **令行」(Command Line** )元件並開啟屬性對話框。

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. 選擇「 **參數** 」頁籤，以輸入「命令行——步 **驟屬性」對話框中的欄位** 。

   在 **Mime類型** (如 ***video/mp4***)中輸入格式，並輸入命令(***/usr/local/Cellar/ffmpeg -i ${filename} -vf "pad=1920:height=1080:x=0:y=0:color=black" cq5dam.video.fullhd-hp4**)，在「命令」欄位中啟動 **工作流** 。

   請參閱以下注 **意事項中****的** Mime類型和命令。

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. 選擇工作流(**VideoRenditions**)，然後從操作欄中按一下「啟動工作流 **」(Start Workflow** )以開啟「 **運行工作流」(Run Workflow** )對話框。

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. 在 **Payload** (as ***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***)中選擇資產路徑，然後輸入**Title **(as ***RunVideo***)並按一下 **** RunRunCrossroads。

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### 在AEM Screens專案中使用工作流程 {#using-the-workflow-in-an-aem-screens-project}

請依照下列步驟，在您的AEM Screens專案中使用工作流程：

1. 導覽至AEM Screens專案(**TestVideoRendition** —&gt; **Channels** —&gt;**VideoRendition**)。

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. 從動 **作列按一下** 「編輯」。 拖放您最初上傳至「資產」的視 **訊**。

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. 上傳視訊後，按一下「 **預覽** 」以檢視輸出。

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## 驗證工作流的輸出 {#validating-the-output-for-the-workflow}

您可以通過以下方式驗證輸出：

* 檢查頻道中的視訊預覽
* 導覽至 ***CRXDE Lite中的/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** ，如下圖所示：

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)


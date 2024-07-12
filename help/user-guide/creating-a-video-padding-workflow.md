---
title: 建立視訊邊框間距工作流程
description: 進一步瞭解如何在工作流程中為資產建立視訊邊框間距。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 16180f96-2855-4250-9d55-24ed77a908b7
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# 建立視訊邊框間距工作流程 {#creating-a-video-padding-workflow}

本節涵蓋下列主題：

* **概觀**
* **必備條件**
* **建立視訊填補工作流程**
   * **建立工作流程**
   * **在AEM Screens專案中使用工作流程**

* **正在驗證工作流程的輸出**

## 概觀 {#overview}

下列使用案例涉及將視訊（範例： 1280 x 720）放置在顯示為1920 x 1080的通道中，並將視訊放置在0x0 （左上方）。 視訊不應以任何方式延伸或修改，且請勿在視訊元件中使用&#x200B;**Cover**。

視訊會以物件的形式顯示，從畫素1到畫素1280 （橫跨畫素1），以及從畫素1到畫素720 （朝下）。 色版的其餘部分為預設顏色。

## 先決條件 {#prerequisites}

在建立視訊工作流程之前，請先完成下列必要條件：

1. 在AEM執行個體的&#x200B;**Assets**&#x200B;資料夾中上傳視訊
1. 建立AEM Screens專案（例如&#x200B;**TestVideoRendition**）和名為(**VideoRendering**)的頻道，如下圖所示：

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## 建立視訊邊框間距工作流程 {#creating-a-video-padding-workflow-1}

若要建立視訊邊框間距工作流程，請為視訊建立工作流程，然後在AEM Screens專案頻道中使用相同的工作流程。

請依照下列步驟建立及使用工作流程：

1. 建立工作流程
1. 在AEM Screens專案中使用工作流程

### 建立工作流程 {#creating-a-workflow}

請依照下列步驟，為您的影片建立工作流程：

1. 導覽至您的AEM執行個體。
1. 按一下側邊欄中的工具。
1. 按一下「**工作流程**」>「**模型**」以建立模型。

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. 按一下「**模型**」>「**建立**」>「**建立模型**」。 在&#x200B;**新增工作流程模型**&#x200B;中輸入&#x200B;**標題** （例如&#x200B;**VideoRendition**）和&#x200B;**名稱**。 按一下&#x200B;**完成**&#x200B;以新增工作流程模型。

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. 建立工作流程模型之後，請按一下模型(**VideoRendition**)，然後按一下動作列中的&#x200B;**編輯**。

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. 將&#x200B;**`Command Line`**&#x200B;元件拖放到工作流程中。

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. 按一下&#x200B;**`Command Line`**&#x200B;元件，然後開啟屬性對話方塊。

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. 按一下&#x200B;**引數**&#x200B;標籤。
1. 在&#x200B;**命令列 — 步驟屬性**&#x200B;對話方塊中，在&#x200B;**Mime型別** （如&#x200B;***video/mp4***）中輸入格式，並將命令輸入為(***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920：height=1080：x=0：y=0：color=black&quot; cq5dam.video.fullhd-hp.mp4***)。 此命令會在&#x200B;**命令**&#x200B;欄位中啟動工作流程。

   請參閱以下附註中&#x200B;**Mime型別**&#x200B;和&#x200B;**命令**&#x200B;的詳細資料。

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. 按一下工作流程（**視訊轉譯**）。
1. 按一下動作列中的&#x200B;**開始工作流程**。

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. 在&#x200B;**執行工作流程**&#x200B;對話方塊中，按一下&#x200B;**裝載**&#x200B;中資產的路徑（如&#x200B;***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***），並輸入&#x200B;**Title**&#x200B;如&#x200B;***RunVideo***，然後按一下&#x200B;**執行**。

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### 在AEM Screens專案中使用工作流程 {#using-the-workflow-in-an-aem-screens-project}

請依照下列步驟，在您的AEM Screens專案中使用工作流程：

1. 導覽至AEM Screens專案（**TestVideoRendition** > **頻道** >**VideoRendition**）。

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. 按一下動作列中的&#x200B;**編輯**。 拖放您最初上傳至&#x200B;**Assets**&#x200B;的視訊。

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. 上傳視訊後，按一下&#x200B;**預覽**&#x200B;以檢視輸出。

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## 驗證工作流程的輸出 {#validating-the-output-for-the-workflow}

您可以透過以下方式驗證輸出：

* 檢查頻道中的視訊預覽
* 導覽至CRXDE Lite中的&#x200B;***/content/dam/testvideo.mp4/jcr：content/renditions/cq5dam.video.fullhd-hp.mp4***，如下圖所示：

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

---
title: 文字重疊
seo-title: 文字重疊
description: 「文字覆蓋」是AEM Screens中提供的功能，可讓您在「序列頻道」中提供覆蓋在影像上方的標題或描述，以建立引人入勝的體驗。 請依照本頁進一步瞭解。
seo-description: 「文字覆蓋」是AEM Screens中提供的功能，可讓您在「序列頻道」中提供覆蓋在影像上方的標題或描述，以建立引人入勝的體驗。 請依照本頁進一步瞭解。
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 文字重疊 {#text-overlay}

本節涵蓋下列主題：

* **綜覽**
* **使用文字覆蓋**
* **必備條件**
* **瞭解文字覆蓋屬性**

>[!CAUTION]
>
>只有在 **您已安裝AEM 6.3 Feature Pack 5或AEM 6.4 Feature Pack 3時，「文字覆蓋** 」功能才可用。

## 概覽 {#overview}

「文字覆蓋」是AEM Screens中提供的功能，可讓您在「序列頻道」中提供覆蓋在影像上方的標題或描述，以建立引人入勝的體驗。

若要瞭解如何建立您自己的自訂元件，請參閱「 **擴充AEM畫面元件」**。

本節僅展示如何在AEM Screens專案中使用和運用海報元件，並將它當做序列頻道中的文字覆蓋。

## 使用文字覆蓋 {#using-text-overlay}

下節說明在AEM Screens專案中使用文字覆蓋的情形。

### 必備條件 {#prerequisites}

開始實作此功能之前，請確定您已將專案設定為開始實作文字覆蓋的先決條件。 例如，

* 建立AEM Screens專案(在此範例中為 **TextOverlayDemo**)

* 在「頻道」檔案夾 **下建立頻道** ，做 **為TextSample**

* 將內容新增至 **TextSample** Channel

下圖顯示TextOverlayDemo專 **案，其中** TextSample頻道位於「頻道」資 **料夾中****** 。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

1. 導覽至 **TextOverlayDemo** —&gt; **Channels** —&gt; **TextSample** ，然後按一下 **** EditExt從動作列開啟編輯器。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 選取影像，然後按一下「 **設定** （扳手圖示）」以開啟屬性對話方塊。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 從對話 **方塊的導覽列中選取「文字覆蓋** 」選項，如下圖所示。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 瞭解文字覆蓋屬性 {#understanding-text-overlay-properties}

使用「文字覆蓋」屬性，您可以將文字新增至「畫面」專案中的任何元件。 下節提供「文字覆蓋」中可用屬性的概述：

![文字](assets/text.gif)

您可以在文字方塊中新增文字，並新增排版強調，例如粗體、斜體、底線等。

**顏色變異** ：此選項允許文字為「深色」（黑色文字）或「淺色」（白色文字）。

**調整大小和定位** ：此選項可讓使用者水準或垂直對齊文字，或另外使用精細的工具來對齊文字。

>[!NOTE]
>
>若要正確使用精密的工具，請務必使用(px)做為字尾，例如200px，以像素為單位識別正確的位置。 此運算式的結果是從起點開始200像素。


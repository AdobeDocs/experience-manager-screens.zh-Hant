---
title: 使用工作流程自動更新AEM Screens頻道的資產
seo-title: 使用工作流程自動更新AEM Screens頻道的資產
description: 瞭解如何建立工作流程，以自動處理上傳至Adobe Experience Manager的資產，並將資產動態指派至畫面頻道。 在此範例中，當將影像新增至特定資料夾時，會觸發套用動態浮水印並將影像指派至「畫面」頻道的工作流程。 從此範例中吸取的教訓可套用至各種自動化案例。
seo-description: 瞭解如何建立工作流程，以自動處理上傳至Adobe Experience Manager的資產，並將資產動態指派至畫面頻道。 在此範例中，當將影像新增至特定資料夾時，會觸發套用動態浮水印並將影像指派至「畫面」頻道的工作流程。 從此範例中吸取的教訓可套用至各種自動化案例。
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: 開發螢幕
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 1667fd10f415214a5301e9740d205eb33cc34f89
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 2%

---


# 使用工作流程自動更新AEM Screens頻道{#automate-channel-updates-workflow}的資產

瞭解如何建立工作流程，以自動處理上傳至Adobe Experience Manager的資產，並將資產動態指派至畫面頻道。 在此範例中，當將影像新增至特定資料夾時，會觸發套用動態浮水印並將影像指派至「畫面」頻道的工作流程。 從此範例中吸取的教訓可套用至各種自動化案例。

## 必備條件 {#prerequisites}

要完成本教學課程，需要以下內容：

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=zh-Hant)
1. [AEM Service Pack 8或更新版本](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=zh-Hant)
1. [AEM 6.5螢幕FP7或更新版本](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html)

## 快速設定{#quick-setup}

以下視訊說明如何安裝范常式式碼套件，以引入新的工作流程至Adobe Experience Manager。 此功能可讓使用者更新AEM Assets的資料夾屬性，以指向「畫面」頻道。 每當影像新增至該資料夾時，就會將影像新增至指定的畫面頻道。

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. 下載編譯的程式碼套件：**[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. 使用Package Manager安裝上AEM述套件。

## 工作流程模型 {#workflow-model}

已建立自訂資料夾中繼資料結構，以擷取應新增影像的目標畫面頻道。 使用兩種工作流程模型來自動化資產處理。 **DAM更新資產**&#x200B;工作流程已修改為呼叫自訂工作流程&#x200B;**畫面示範資產處理**，此工作流程將檢查資產的包含資料夾以判斷目標畫面頻道。 **畫面展示資產處理**&#x200B;工作流程也負責將浮水印套用至影像。

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## 自訂工作流程程式步驟{#workflow-process-step}

Inspect公司在&#x200B;**畫面示範資產處理**&#x200B;工作流程中使用的兩個自訂工作流程程式步驟。

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` 是自訂工作流程程式，會對工作流程的裝載執行檢查，以判斷裝載是否為資產，以及是否將包含資料夾設定為指向「畫面」頻道。如果滿足要求，流程步驟會將`screen-channel`和`asset-path`兩個屬性保留在工作流的元資料中。

`AddAssetToChannel.java` 是自訂工作流程程式步驟，會檢查工作流程的中繼資料並更新「畫面」頻道以參考影像。

1. 下載原始碼：**[screens-demo-main-zip](./assets/screens-demo-main.zip)**
1. 使用您最愛的IDE解壓縮並檢視程式碼。

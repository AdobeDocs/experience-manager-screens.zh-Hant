---
title: 使用工作流程為AEM Screens管道自動進行資產更新
seo-title: 使用工作流程為AEM Screens管道自動進行資產更新
description: 了解如何建立工作流程以自動處理上傳至Adobe Experience Manager的資產，並以動態方式將資產指派至Screens頻道。 在此範例中，當影像新增至特定資料夾時，會觸發工作流程，套用動態浮水印並將影像指派至Screens頻道。 從本示例中吸取的經驗教訓可以應用於各種自動化方案。
seo-description: 了解如何建立工作流程以自動處理上傳至Adobe Experience Manager的資產，並以動態方式將資產指派至Screens頻道。 在此範例中，當影像新增至特定資料夾時，會觸發工作流程，套用動態浮水印並將影像指派至Screens頻道。 從本示例中吸取的經驗教訓可以應用於各種自動化方案。
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: 開發螢幕
role: Developer
level: Intermediate
source-git-commit: 8d1633dab9e70ea988516cf9ee4d1b0a780bc7e9
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 2%

---


# 使用工作流程自動更新AEM Screens通道{#automate-channel-updates-workflow}的資產

了解如何建立工作流程以自動處理上傳至Adobe Experience Manager的資產，並以動態方式將資產指派至Screens頻道。 在此範例中，當影像新增至特定資料夾時，會觸發套用動態文字覆蓋（浮水印處理）並將影像指派至Screens頻道的工作流程。 從本示例中吸取的經驗教訓可以應用於各種自動化方案。

## 必備條件 {#prerequisites}

若要完成本教學課程，需要執行下列操作：

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=zh-Hant)
1. [AEM Service Pack 8或更新版本](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=zh-Hant)
1. [AEM 6.5 Screens FP7或更高版本](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html)

## 快速設定{#quick-setup}

以下影片說明如何安裝范常式式碼套件，以導入新的工作流程至Adobe Experience Manager。 此功能可讓使用者更新AEM Assets中資料夾的屬性，以指向Screens頻道。 每當影像新增至該資料夾時，就會將其新增至指定的螢幕頻道。

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. 下載已編譯的程式碼套件：**[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. 使用AEM Package Manager安裝上述套件。

## 工作流程模型 {#workflow-model}

已建立自訂資料夾中繼資料結構，以擷取應新增影像的目標Screens頻道。 兩種工作流程模型可用來自動化資產處理。 已修改&#x200B;**DAM更新資產**&#x200B;工作流程，以呼叫自訂工作流程&#x200B;**Screens示範資產處理**，該工作流程將檢查資產的容納資料夾，以判斷目標Screens通道。 **Screens演示資產處理**&#x200B;工作流還負責將水印應用到影像。

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## 自訂工作流程處理步驟{#workflow-process-step}

Inspect兩個自訂工作流程處理步驟，用於&#x200B;**Screens示範資產處理**&#x200B;工作流程。

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` 是自訂工作流程程式，會對工作流程的裝載執行檢查，以判斷裝載是否為資產，以及容納資料夾是否設定為指向Screens頻道。如果滿足要求，處理步驟會將`screen-channel`和`asset-path`這兩個屬性保存到工作流的元資料中。

`AddAssetToChannel.java` 是自訂工作流程處理步驟，可檢查工作流程的中繼資料並更新Screens頻道以參考影像。

1. 下載原始碼：**[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. 使用您最喜愛的IDE解壓縮並查看代碼。

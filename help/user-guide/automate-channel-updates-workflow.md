---
title: 使用工作流程自動化AEM Screens頻道的資產更新
description: 瞭解如何建立工作流程，以自動處理上傳至Adobe Experience Manager的資產，並動態將其指派至Screens頻道。
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
source-git-commit: 3c4b37b3b9f268b500562fa4ce3782b7be1e7d74
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 1%

---


# 使用工作流程自動化AEM Screens頻道的資產更新 {#automate-channel-updates-workflow}

瞭解如何建立工作流程，以自動處理上傳至Adobe Experience Manager的資產，並動態將其指派至Screens頻道。 在此範例中，將影像新增至特定資料夾時，會觸發套用動態文字覆蓋（浮水印程式）的工作流程，並將影像指派至Screens色版。 從這個範例中學到的經驗教訓可以應用於各種自動化情境。

## 先決條件 {#prerequisites}

若要完成本教學課程，您需要下列專案：

1. [AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65)
1. [AEM Service Pack 8或更新版本](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/release-notes/release-notes)
1. [AEM 6.5 Screens FP7或更新版本](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103)

## 快速設定 {#quick-setup}

以下影片說明如何安裝範常式式碼套件，該套件會為Adobe Experience Manager引入新的工作流程。 此功能可讓使用者更新AEM Assets中資料夾的屬性，以指向Screens頻道。 每當將影像新增至該資料夾時，它就會新增至指定的AEM Screens頻道。

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. 下載編譯的程式碼套件： **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. 使用AEM Package Manager安裝上述套件。

## 工作流程模型 {#workflow-model}

已建立自訂資料夾中繼資料結構，以擷取應新增影像的目標Screens頻道。 使用兩個工作流程模型來自動化資產處理。 此 **DAM更新資產** 修改工作流程以呼叫自訂工作流程 **Screens示範資產處理** ，可檢查資產的容納資料夾以決定目標Screens頻道。 此 **Screens示範資產處理** 工作流程也負責將浮水印套用至影像。

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## 自訂工作流程處理步驟 {#workflow-process-step}

Inspect作為一部分使用的兩個自訂工作流程處理步驟 **Screens示範資產處理** 工作流程。

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

此 `AssetProcessingCheck.java` 自訂工作流程是對工作流程的裝載執行檢查的程式。 它會判斷裝載是否為資產，以及容納資料夾是否已設定為指向AEM Screens頻道。 如果滿足需求，流程步驟會持續存在兩個屬性， `screen-channel` 和 `asset-path`，至工作流程的中繼資料。

此 `AddAssetToChannel.java` 自訂工作流程是一個程式步驟，會檢查工作流程的中繼資料並更新AEM Screens頻道以參考影像。

1. 下載原始程式碼： **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. 使用您最愛的IDE解壓縮並檢視程式碼。

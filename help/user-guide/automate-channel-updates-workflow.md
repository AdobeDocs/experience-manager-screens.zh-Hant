---
title: 使用工作流自動更新AEM Screens渠道的資產
seo-title: Use workflow to automate asset updates for an AEM Screens channel
description: 瞭解如何建立工作流以自動處理上載到Adobe Experience Manager的資產並將其動態分配給螢幕通道。 在本示例中，當將影像添加到特定資料夾時，將觸發應用動態水印並將影像分配給螢幕通道的工作流。 從本示例中吸取的經驗教訓可應用於各種自動化場景。
seo-description: Learn how to create a workflow to automatically process assets uploaded to Adobe Experience Manager and dynamically assign them to a Screens channel. In this example when an image is added to a specific folder, a workflow is triggered that applies a dynamic watermark and assigns the image to a Screens channel. Lessons learned from this example can be applied to a wide variety of automation scenarios.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
source-git-commit: 8d1633dab9e70ea988516cf9ee4d1b0a780bc7e9
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 5%

---


# 使用工作流自動更新AEM Screens渠道的資產 {#automate-channel-updates-workflow}

瞭解如何建立工作流以自動處理上載到Adobe Experience Manager的資產並將其動態分配給螢幕通道。 在此示例中，當將影像添加到特定資料夾時，將觸發一個工作流，該工作流應用動態文本覆蓋（水印過程）並將影像分配給螢幕通道。 從本示例中吸取的經驗教訓可應用於各種自動化場景。

## 必備條件 {#prerequisites}

要完成本教程，需要執行以下操作：

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=zh-Hant)
1. [AEM Service Pack 8或更高版本](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html)
1. [6AEM.5螢幕FP7或更高版本](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html)

## 快速設定 {#quick-setup}

下面的視頻說明了如何安裝示例代碼包，該示例代碼包將向Adobe Experience Manager引入新工作流。 此功能允許用戶更新AEM Assets中資料夾的屬性以指向螢幕通道。 每當將影像添加到該資料夾時，都會將其添加到指定的螢幕通道中。

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. 下載已編譯的代碼包： **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. 使用包管理器安AEM裝上述包。

## 工作流程模型 {#workflow-model}

已建立自定義資料夾元資料架構以捕獲應添加映像的目標螢幕通道。 兩個工作流模型用於自動化資產處理。 的 **DAM更新資產** 修改工作流以調用自定義工作流， **螢幕演示資產處理** 它將檢查資產的包含資料夾以確定目標螢幕通道。 的 **螢幕演示資產處理** 工作流還負責將水印應用到影像。

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## 自定義工作流進程步驟 {#workflow-process-step}

Inspect兩個用作部分的自定義工作流進程步驟 **螢幕演示資產處理** 工作流。

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` 是自定義工作流進程，它對工作流的負載執行檢查以確定負載是否為資產，以及是否將包含資料夾配置為指向「螢幕」通道。 如果滿足要求，則流程步驟將保留兩個屬性， `screen-channel` 和 `asset-path`，到工作流的元資料。

`AddAssetToChannel.java` 是自定義工作流進程步驟，它檢查工作流的元資料並更新「螢幕」通道以引用影像。

1. 下載原始碼： **[螢幕demo-main.zip](./assets/screens-demo-main.zip)**
1. 使用您喜愛的IDE解壓並查看代碼。

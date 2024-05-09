---
title: 建立和管理顯示器
description: 瞭解如何在AEM Screens中建立顯示器和裝置設定。 另外，瞭解顯示控制面板。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 1%

---

# 建立和管理顯示器 {#creating-and-managing-displays}

顯示器是彼此相鄰放置之熒幕的虛擬群組。 顯示相對於安裝是永久性的。 它是內容作者搭配使用的物件，且一律會參照為邏輯顯示，而不是其實體計數器部分。

當您建立位置時，必須建立位置的顯示。

此頁面顯示建立及管理Screens的顯示畫面。

**先決條件**：

* [設定和部署Screens](configuring-screens-introduction.md)
* [建立和管理Screens專案](creating-a-screens-project.md)
* [建立和管理頻道](managing-channels.md)
* [建立和管理位置](managing-locations.md)

## 建立新顯示區 {#creating-a-new-display}

>[!NOTE]
>
>在建立顯示之前先建立位置。 另請參閱 [建立和管理位置](managing-locations.md) 以取得詳細資訊。

1. 導覽至適當位置，例如 `http://localhost:4502/screens.html/content/screens/TestProject`.
1. 按一下您的位置資料夾，然後按一下 **建立** 位於動作列中的加號圖示旁。
1. 按一下 **顯示** 從 **建立** 精靈，然後按一下 **下一個**.
1. 輸入您的 **名稱** 和 **標題** 以取得您的顯示位置。
1. 在 **顯示** 頁簽，選擇配置圖的詳細資訊。 選擇所需的 **解析度**，例如 **Full HD**. 選擇水平與垂直裝置數量。
1. 按一下&#x200B;**建立**。

顯示區(*StoreDisplay*)建立並新增至位置(*SanJose*)。

![顯示](assets/display.gif)

當您有顯示器就位時，下一步就是為該特定顯示器建立裝置設定。

>[!NOTE]
>
>**下一步**：
>
>當您為位置建立顯示區時，請為顯示區指派頻道，以使用內容。
>
>請參閱 [指派管道](channel-assignment.md) 一節，以瞭解如何指派管道給顯示。

## 建立新的裝置設定 {#creating-a-new-device-config}

裝置設定可做為尚未安裝之實際數位看板裝置的預留位置。

1. 導覽至適當的顯示畫面，例如， `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. 按一下您的顯示資料夾，然後按一下 **檢視控制面板** 於動作列中。
1. 按一下 **+新增裝置設定** 右上角的 **裝置** 面板。

1. 按一下 **裝置設定** 作為所需範本，然後按一下 **下一個**.

1. 視需要輸入屬性，然後按一下 **建立**.

裝置設定已建立並新增至目前的顯示畫面(在下列示範中，新的裝置設定為 *裝置設定*)。

![裝置設定](assets/deviceconfig.gif)

>[!NOTE]
>
>當裝置設定設定為顯示在該位置時，下一步將指派頻道給您的顯示。
>
>如果裝置設定在「 」中顯示為「未指派」，如下圖所示 **裝置** 面板（如果沒有指派頻道給該特定裝置設定）。
>
>您應預先瞭解如何建立和管理管道。 另請參閱 [建立和管理頻道](managing-channels.md) 以取得更多詳細資料。

![chlimage_1-9](assets/chlimage_1-9.png)

## 顯示控制面板 {#display-dashboard}

顯示儀表板提供您管理顯示裝置的不同面板。 它也可讓您設定裝置。

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>您可以按一下控制面板清單並觸發專案的批次動作，而不是分別檢視每個專案。
>
>例如，下圖顯示如何從顯示圖示板按一下多個色版。

![cqdoc9456](assets/cqdoc9456.gif)

### 顯示資訊面板 {#display-information-panel}

此 **顯示資訊** 面板提供顯示屬性。

按一下(**...**)的右上角 **顯示資訊** 面板，讓您可以檢視屬性並預覽顯示。


#### 檢視屬性 {#viewing-properties}

按一下 **屬性** 以便檢視或變更顯示內容。

此外，您也可以調整下方的互動式管道事件計時器值 **顯示** 標籤。 預設值設為 *300秒*.

使用 **CRXDE Lite**，以存取 **idleTimeout** 屬性，也就是說， `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels`.


### 已指派的色版面板 {#assigned-channels-panel}

此 **已指派的管道** 面板會顯示指派給此裝置的通道。


### 裝置面板 {#devices-panel}

此 **裝置** 面板提供裝置設定的相關資訊。

按一下(**...**)的右上角 **裝置** 面板，方便您新增裝置設定和更新裝置。

此外，按一下裝置設定即可檢視屬性、指派裝置，或完全刪除裝置。

![chlimage_1-13](assets/chlimage_1-13.png)

#### 後續步驟 {#the-next-steps}

當您完成建立位置的顯示時，請為顯示指派頻道。

另請參閱 [指派管道](channel-assignment.md) 以取得更多詳細資料。

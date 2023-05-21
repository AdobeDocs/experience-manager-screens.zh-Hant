---
title: 建立和管理顯示
seo-title: Managing Displays
description: 按照本頁瞭解如何建立新的顯示和設備配置。 此外，瞭解顯示儀表板。
seo-description: Follow this page to learn about creating a new display and device config. Additionally, learn about the display dashboard.
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 1%

---

# 建立和管理顯示 {#creating-and-managing-displays}

顯示器是通常彼此相鄰放置的螢幕的虛擬分組。 顯示器通常對於安裝是永久的。 這將是對象內容作者將使用的對象，並始終引用為邏輯顯示，而不是其物理計數器部分。

建立位置後，必須為位置建立新顯示。

此頁顯示螢幕的建立和管理顯示。

**先決條件**:

* [配置和部署螢幕](configuring-screens-introduction.md)
* [建立和管理螢幕項目](creating-a-screens-project.md)
* [建立和管理渠道](managing-channels.md)
* [建立和管理位置](managing-locations.md)

## 建立新顯示 {#creating-a-new-display}

>[!NOTE]
>
>在建立顯示之前，需要建立一個位置。 要查看如何建立位置，請參閱 [建立和管理位置](managing-locations.md) 的子菜單。

要在您的位置建立新顯示，請執行以下步驟：

1. 導航至相應位置，例如 `http://localhost:4502/screens.html/content/screens/TestProject`。
1. 選擇您的位置資料夾並點擊/按一下 **建立** 按鈕。 將會開啟嚮導。
1. 選擇 **顯示** 從 **建立** 嚮導 **下一個**。

1. 輸入 **名稱** 和 **標題** 顯示位置。

1. 在 **顯示** 頁籤。 選擇所需 **解決** (例如， **全高清**)。 此外，您可以水準和垂直選擇設備的數量。

1. 按一下&#x200B;**建立**。

顯示(*商店顯示*)建立並添加到位置(*聖何塞*)。

![顯示](assets/display.gif)

在顯示到位後，下一步將為該特定顯示建立設備配置。 按照下面的部分建立新設備配置。

>[!NOTE]
>
>**下一步**:
>
>為您的位置建立顯示器後，您需要為顯示器分配一個頻道以利用內容。
>
>請參閱 [分配通道](channel-assignment.md) 的子菜單。

## 建立新設備配置 {#creating-a-new-device-config}

設備配置用作尚未安裝的實際數字標牌設備的佔位符。

按照以下步驟建立新設備配置：

1. 導航至相應的顯示，例如， `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`。
1. 選擇顯示資料夾並點擊/按一下 **查看儀表板** 的子菜單。
1. 點擊/按一下 **+添加設備配置** 右上角 **設備** 的子菜單。

1. 選擇 **設備配置** 按為所需模板，然後點擊/按一下 **下一個**。

1. 根據需要輸入屬性，然後點擊/按一下 **建立**。

將建立設備配置並將其添加到當前顯示中(在下面的演示中，新設備配置將 *設備配置*)。

![設備配置](assets/deviceconfig.gif)

一旦將設備配置設定為位置中的顯示器，下一步將為顯示器分配通道。

>[!NOTE]
>
>一旦將設備配置設定為位置中的顯示器，下一步將為顯示器分配通道。
>
>如下圖所示，如果設備配置在 **設備** 如果沒有為該特定設備配置分配通道，則顯示面板。
>
>您應該事先瞭解建立和管理渠道。 請參閱 [建立和管理渠道](managing-channels.md) 的子菜單。

![chlimage_1-9](assets/chlimage_1-9.png)

## 顯示控制面板 {#display-dashboard}

顯示面板為您提供了不同的面板，用於管理顯示設備和設備配置。

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>您可以選擇儀表板清單並觸發項目上的批量操作，而不是單獨處理每個項目。
>
>例如，下圖顯示了如何從顯示操控板中選擇多個通道。

![cqdoc9456](assets/cqdoc9456.gif)

### 顯示資訊面板 {#display-information-panel}

的 **顯示資訊** 面板提供顯示屬性。

按一下(**...**) **顯示資訊** 的子菜單。


#### 查看屬性 {#viewing-properties}

按一下 **屬性** 查看或更改顯示的屬性。

此外，您還可以在 **空閒超時** 財產 **顯示** 頁籤。 預設值設定為 *300秒*。

使用 **CRXDE Lite**，以訪問 **空閒超時** 財產，就是 `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` 。


### 分配的通道面板 {#assigned-channels-panel}

的 **分配的頻道** 面板顯示指定給此設備的通道。


### 設備面板 {#devices-panel}

的 **設備** 面板提供有關設備配置的資訊。

按一下(**...**) **設備** 面板，用於添加設備配置和更新設備。

此外，按一下設備配置可查看屬性、指定設備或將其完全刪除。

![chlimage_1-13](assets/chlimage_1-13.png)

#### 後續步驟 {#the-next-steps}

完成為位置建立顯示後，需要為顯示指定通道。

請參閱 [分配通道](channel-assignment.md) 的子菜單。

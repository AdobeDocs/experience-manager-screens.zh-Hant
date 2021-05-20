---
title: 建立和管理顯示
seo-title: 管理顯示
description: 請依照本頁面了解如何建立新的顯示和裝置設定。 此外，還可了解顯示控制面板。
seo-description: 請依照本頁面了解如何建立新的顯示和裝置設定。 此外，還可了解顯示控制面板。
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
feature: 製作畫面
role: Administrator, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 0%

---

# 建立和管理顯示{#creating-and-managing-displays}

顯示器是通常彼此相鄰的螢幕的虛擬分組。 對於安裝，顯示器通常是永久的。 這將是作者將使用的物件內容，且一律以邏輯顯示方式參照，而非其實體計數器部分。

建立位置後，您必須為位置建立新的顯示。

此頁面顯示如何建立和管理螢幕的顯示。

**先決條件**:

* [設定和部署畫面](configuring-screens-introduction.md)
* [建立和管理Screens專案](creating-a-screens-project.md)
* [建立和管理管道](managing-channels.md)
* [建立和管理位置](managing-locations.md)

## 建立新顯示{#creating-a-new-display}

>[!NOTE]
>
>您必須先建立位置，才能建立顯示。 若要查看如何建立位置，請參閱[建立和管理位置](managing-locations.md)以了解詳細資訊。

要在您的位置中建立新顯示，請執行以下步驟：

1. 導覽至適當的位置，例如`http://localhost:4502/screens.html/content/screens/TestProject`。
1. 選取您的位置資料夾，然後點選/按一下動作列中加號圖示旁的「建立&#x200B;****」。 嚮導將開啟。
1. 從&#x200B;**Create**&#x200B;嚮導中選擇&#x200B;**Display**，然後按一下&#x200B;**Next**。

1. 輸入顯示位置的&#x200B;**名稱**&#x200B;和&#x200B;**標題**。

1. 在&#x200B;**Display**&#x200B;標籤下，選擇「佈局」的詳細資訊。 選擇所需的&#x200B;**解析度**（例如，**全高清**）。 此外，您還可以水準和垂直選擇裝置數量。

1. 按一下&#x200B;**建立**。

顯示(*StoreDisplay*)被建立並添加到位置(*SanJose*)。

![顯示](assets/display.gif)

顯示於位置後，下一步就是為該特定顯示建立裝置設定。 請依照下節建立新裝置設定。

>[!NOTE]
>
>**下一步**:
>
>為您的位置建立顯示器後，您需要為顯示器指派頻道，以運用內容。
>
>請參閱[指派頻道](channel-assignment.md)區段，了解如何指派頻道給顯示器。

## 建立新設備配置{#creating-a-new-device-config}

裝置設定可作為實際數位看板裝置（尚未安裝）的預留位置。

請依照下列步驟建立新裝置設定：

1. 導覽至適當的顯示，例如`http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`。
1. 選取您的顯示資料夾，然後點選/按一下動作列中的「檢視控制面板」**。**
1. 點選/按一下&#x200B;**Devices**&#x200B;面板右上方的&#x200B;**+ Add Device Config**。

1. 選擇&#x200B;**Device Config**&#x200B;作為所需模板，然後點選/按一下&#x200B;**Next**。

1. 視需要輸入屬性，然後點選/按一下「**建立**」。

裝置設定會建立並新增至目前的顯示（在下列示範中，新的裝置設定為&#x200B;*DeviceConfig*）。

![設備配置](assets/deviceconfig.gif)

一旦將裝置設定設為位置中的顯示器，下一步就是指派通道給您的顯示器。

>[!NOTE]
>
>一旦將裝置設定設為位置中的顯示器，下一步就是指派通道給您的顯示器。
>
>如下圖所示，如果設備配置在&#x200B;**DEVICES**&#x200B;面板中顯示為未分配，則沒有為該特定設備配置分配通道。
>
>您應先了解建立和管理管道的相關事項。 如需詳細資訊，請參閱[建立和管理通道](managing-channels.md)。

![chlimage_1-9](assets/chlimage_1-9.png)

## 顯示控制面板 {#display-dashboard}

顯示控制面板提供您不同的面板，以管理您的裝置的顯示裝置和裝置組態。

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>您可以選取控制面板清單並觸發項目上的大量動作，而不必個別逐一處理每個項目。
>
>例如，下圖顯示如何從顯示控制面板選取多個通道。

![cqdoc9456](assets/cqdoc9456.gif)

### 顯示資訊面板{#display-information-panel}

「**顯示資訊**」面板提供顯示屬性。

按一下(**...**)，以檢視屬性並預覽顯示。****


#### 查看屬性{#viewing-properties}

按一下「**屬性**」以查看或更改顯示的屬性。

此外，您也可以在&#x200B;**Display**&#x200B;標籤下的&#x200B;**Idle timeout**&#x200B;屬性中調整互動通道的事件計時器值。 預設值設為&#x200B;*300秒*。

使用&#x200B;**CRXDE Lite**&#x200B;來存取&#x200B;**idleTimeout**&#x200B;屬性，即`http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` 。


### 「指定通道」面板{#assigned-channels-panel}

**已分配通道**&#x200B;面板顯示為此設備分配的通道。


### 設備面板{#devices-panel}

**DEVICES**&#x200B;面板提供有關裝置設定的資訊。

按一下(**...**)，以新增裝置設定和更新裝置。****

此外，按一下裝置設定即可檢視屬性、指派裝置或將其完全刪除。

![chlimage_1-13](assets/chlimage_1-13.png)

#### 後續步驟{#the-next-steps}

完成為位置建立顯示器後，您需要為顯示器指派通道。

如需詳細資訊，請參閱[指派管道](channel-assignment.md) 。

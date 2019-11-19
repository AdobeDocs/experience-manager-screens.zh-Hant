---
title: 建立和管理顯示
seo-title: 管理顯示
description: 請依照本頁瞭解如何建立新的顯示和裝置設定。 此外，還可瞭解顯示控制面板。
seo-description: 請依照本頁瞭解如何建立新的顯示和裝置設定。 此外，還可瞭解顯示控制面板。
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 建立和管理顯示 {#creating-and-managing-displays}

顯示器是通常彼此相鄰的虛擬畫面群組。 對於安裝，顯示器通常是永久的。 這將是作者將使用的物件內容，並一律參照為邏輯顯示，而非物理計數器部分。

建立位置後，您必須為您的位置建立新的顯示。

此頁面顯示如何建立和管理「畫面」的顯示。

**先決條件**:

* [設定和部署畫面](configuring-screens-introduction.md)
* [建立和管理畫面專案](creating-a-screens-project.md)
* [建立和管理渠道](managing-channels.md)
* [建立和管理位置](managing-locations.md)

## 建立新顯示 {#creating-a-new-display}

>[!NOTE]
>
>您必須先建立位置，再建立顯示。 若要瞭解如何建立位置，請參閱建 [立和管理位置](managing-locations.md) ，以取得詳細資訊。

若要在您的位置建立新顯示，請遵循下列步驟：

1. 例如，導覽至適當的位置 `http://localhost:4502/screens.html/content/screens/TestProject`。
1. 選取您的位置資料夾，並點選／按 **一下動作列中** 加號圖示旁的「建立」。 嚮導將開啟。
1. 從「創 **建** 」嚮導中選擇「顯 **示」** ，然後按一下「 **下一步**」。

1. 輸入 **顯示位** 置的名稱 **** 和標題。

1. 在「顯 **示** 」標籤下，選擇「版面」的詳細資訊。 選擇所需的 **解析度** (例如， **全高清**)。 此外，您還可以水準和垂直選擇裝置數。

1. 按一下&#x200B;**「建立」**。

顯示(*StoreDisplay*)會建立並新增至&#x200B;*位置(SanJose*)。

![顯示](assets/display.gif)

在顯示位置後，下一步是為該特定顯示建立裝置組態。 請依照下節來建立新的裝置設定。

>[!NOTE]
>
>**下一步**:
>
>為您的位置建立顯示器後，您需要為顯示器指派頻道，以運用內容。
>
>請參 [閱指派渠道](channel-assignment.md) ，瞭解如何指派渠道至顯示。

## Creating a New Device Config {#creating-a-new-device-config}

裝置組態可當成尚未安裝之實際數位標牌裝置的預留位置。

請依照下列步驟建立新的裝置設定：

1. 導覽至適當的顯示，例如 `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`。
1. 選取您的顯示資料夾，並點選／按一下動 **作列中的「檢視控制面板** 」(View Dashboard)。
1. 點選／按一下「 **Devices（裝置）」面板右上方的「** + Add Device Config **(新增裝置** 設定)」。

1. 選擇「 **Device Config** （設備配置）」作為所需模板，然後點選／按一下「 **Next（下一步）」**。

1. 視需要輸入屬性，然後點選／按一下「 **建立**」。

設備配置將建立並添加到當前顯示中(在以下演示中，新設備配置是 *DeviceConfig*)。

![設備配置](assets/deviceconfig.gif)

一旦將裝置組態設定設定為您在位置中的顯示，下一步就是指派頻道給您的顯示。

>[!NOTE]
>
>一旦將裝置組態設定設定為您在位置中的顯示，下一步就是指派頻道給您的顯示。
>
>如下圖所示，如果設備配置在 **DEVICES** 面板中顯示為未分配，則沒有為該特定設備配置分配通道。
>
>您應事先瞭解建立和管理渠道。 如需詳 [細資訊，請參閱建立及](managing-channels.md) 管理渠道。

![chlimage_1-9](assets/chlimage_1-9.png)

## 顯示控制面板 {#display-dashboard}

顯示控制面板提供您不同的面板，以管理顯示裝置和裝置組態。

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>您可以選取控制面板清單並觸發項目上的大量動作，而不是個別執行每個項目。
>
>例如，下圖顯示如何從顯示控制面板選取多個色版。

![cqdoc9456](assets/cqdoc9456.gif)

### 顯示資訊面板 {#display-information-panel}

「顯 **示資訊** 」面板提供顯示屬性。

按一下****顯示資訊**面板右上角的**(...)，以檢視屬性並預覽顯示。

![chlimage_1-10](assets/chlimage_1-10.png)

#### 查看屬性 {#viewing-properties}

按一 **下「屬性** 」以檢視或變更顯示的屬性。

此外，您也可以在「顯示」標籤下的「**閒置逾時**屬性」中調整互動頻道的事件計時器 **值** 。 預設值設為 *300秒*。

使 **用CRXDE Lite**，存取 **idleTimeout** 屬性，即 `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` 。

![chlimage_1-1](assets/chlimage_1-1.gif)

### 指派的頻道面板 {#assigned-channels-panel}

「指 **派的頻道** 」面板會顯示指派給此裝置的頻道。

![chlimage_1-11](assets/chlimage_1-11.png)

### 裝置面板 {#devices-panel}

「 **DEVICES** Panel（設備面板）」提供有關設備配置的資訊。

按一下****裝置**面板右上角的**(...)，以新增裝置設定和更新裝置。

![chlimage_1-12](assets/chlimage_1-12.png)

此外，按一下裝置組態以檢視屬性、指派裝置或完全刪除裝置。

![chlimage_1-13](assets/chlimage_1-13.png)

#### 後續步驟 {#the-next-steps}

完成為您的位置建立顯示器後，您需要為顯示器指定頻道。

如需詳 [細資訊，請參閱](channel-assignment.md) 「指派渠道」。

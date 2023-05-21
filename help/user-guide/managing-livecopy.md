---
title: 建立和管理即時拷貝
seo-title: Managing LiveCopy
description: 本頁介紹如何建立和管理渠道的即時拷貝。
seo-description: Follow this page to create live copy of a channel, view properties, check status, and propagate changes from a channel to its live copy.
uuid: 78ec7219-95ab-44d1-9514-1b97aded5bf4
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 84085a03-1798-4f1d-858c-6014a3f6aff6
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 4a4b3a83-2b02-42a0-86a7-fce6bbf47c7d
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 2%

---

# 建立和管理即時拷貝 {#creating-and-managing-a-live-copy}

本頁介紹如何建立和管理渠道的即時拷貝。

A ***即時拷貝*** 是與原始源保持即時關係的特定網站內容的副本。 此即時關係允許即時副本從源繼承內容和頁面屬性。

本頁介紹如何建立頻道的即時拷貝、查看屬性、檢查狀態以及將更改從頻道傳播到其即時拷貝。


## 建立即時副本 {#creating-a-live-copy}

按照以下步驟在項目資料夾中建立渠道的即時副本。

1. 選擇Adobe Experience Manager連結（左上），然後 **螢幕**。 或者，您可以直接訪問： `http://localhost:4502/screens.html/content/screens`。

1. 導航到「螢幕」項目，然後按一下 **頻道**。
1. 按一下 **建立** 選擇 **即時拷貝** 建立頻道的即時副本。

1. 選擇目標並按一下 **下一個**。
1. 選擇即時副本所在的位置。
1. 輸入 **標題** 和 **名稱** 的 **建立即時拷貝** 的子菜單。

1. 按一下 **開啟** 查看新即時副本的內容，或 **完成** 的子菜單。

或者，請參閱下面的步驟以獲取建立頻道新即時副本的視覺表示。

以下示例顯示即時副本的建立(***IdleLiveCopy***) ***空閒通道*** 將目標資料夾設定為 ***頻道***。

![chlimage_1-2](assets/chlimage_1-2.gif)

## 查看即時複製頻道的內容 {#viewing-content-of-the-live-copy-channel}

即時拷貝是已存在的通道的拷貝。

要查看即時副本的內容，請參閱以下步驟：

1. 導航至「螢幕」項目，然後按一下原始建立即時副本的位置，如上節所示。 (這裡，選擇的位置是 **頻道** 資料夾)

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. 按一下 **編輯** 的子菜單。

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >查看即時複製頻道的內容時，您將在菜單中查看附加項目， **即時複製狀態**。 有關詳細資訊，請參閱下面的部分。

### 查看即時副本的屬性 {#viewing-properties-of-a-live-copy}

此外，您還可以查看即時複製頻道的屬性。

1. 導航到您的即時拷貝頻道，然後按一下 **屬性** 按鈕。

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. 選擇 **即時拷貝** 的子菜單。

   ![chlimage_1-21](assets/chlimage_1-21.png)

### 即時副本狀態 {#live-copy-status}

模式 **即時複製狀態**，如下圖所示，允許您查看渠道中所有資產的關係狀態。

1. 按一下 **編輯** 的子菜單。 **即時複製狀態** 並查看頻道內容與原始頻道（從中生成即時副本）的關聯。

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. 選擇 **即時複製狀態** 的子菜單。

   所有帶綠色邊框的資源都顯示內容是從原始渠道繼承的。

   ![chlimage_1-23](assets/chlimage_1-23.png)

### 斷絕繼承 {#breaking-the-inheritance}

也可以取消對livecopy的繼承，因此內容將獨立於原始分支。

下面的示例顯示您在編輯模式下選擇影像，然後按一下右上角的取消繼承符號。

![chlimage_1-24](assets/chlimage_1-24.png)

### 將更改傳播到即時複製通道 {#propagating-changes-to-the-live-copy-channel}

如果在原始通道中進行更改/更新，則需要將這些更改傳播到即時複製通道。

按照以下步驟來確保您的更改從原始通道傳播到即時複製通道：

1. 選擇原始通道(***空閒通道***) **編輯** 按鈕。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 編輯此頻道內容。 例如，從此通道中刪除影像。

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. 選擇頻道的即時副本(***IdleLiveCopy***) **編輯** 按鈕。 您會注意到您刪除的影像在即時副本中仍然可見。

   為了傳播更改，需要同步通道。

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. 要將更改傳播到即時複製通道，請導航到儀AEM表板，然後選擇即時複製通道，然後按一下 **屬性** 按鈕。

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. 選擇 **即時拷貝** 頁籤 **同步** 按鈕。

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. 按一下 **同步** 確認更改。 按一下 **保存並關閉** 導航回儀表板AEM。

   ![chlimage_1-30](assets/chlimage_1-30.png)

   您會注意到該影像現在也已從即時複製頻道中刪除。

---
title: 多區域佈局
seo-title: 多區域佈局
description: 「多區域配置」可讓您建立多個區域內容，並使用各種資產，例如視訊、影像和文字，這些資產可以在單一畫面中結合。 請詳閱本頁以了解更多。
seo-description: 「多區域配置」可讓您建立多個區域內容，並使用各種資產，例如視訊、影像和文字，這些資產可以在單一畫面中結合。 請詳閱本頁以了解更多。
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
feature: 製作畫面
role: Administrator, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 0%

---

# 多區域佈局{#multi-zone-layout}

以下頁面說明多區域版面的使用方式，並涵蓋下列主題：

* 概覽
* 建立多區域佈局
* 必備條件
* 在一或多個區域中使用單一資產
* 在一個或多個區域中使用序列內容

## 概覽 {#overview}

***多區域*** 佈局允許您建立多個區域內容，並使用視頻、影像和文本等各種資產，這些資產可以在單個螢幕中組合。您可以提取影像、影片和文字，讓影像、影片和文字融為一體，打造直覺的數位體驗。

根據專案需求，有時您需要在通道中建立多個區域，並以一個完整單位編輯這些區域。 例如，產品序列與相關社交媒體摘要會在單一頻道的三個獨立區域中執行。


### 必備條件 {#prerequisites}

開始實作此功能之前，請確定您具備下列概念知識：

* [建立AEM Screens專案](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [建立顯示](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [為顯示指定通道](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/channel-assignment.html)

## 建立多區域佈局{#creating-multi-zone-layout}

建立管道時，您可以使用不同的範本，在管道中建立區域。 您可以新增單一影像、視訊或內嵌通道，讓多個資產可依序顯示。

**建立管道**

1. 選取Adobe Experience Manager連結（左上角），然後選取&#x200B;**Screens**。 或者，您也可以直接前往：`http://localhost:4502/screens.html/content/screens`。
1. 導覽至「**頻道**」資料夾，然後從動作列按一下「**建立**」。

1. 從&#x200B;**Create**&#x200B;嚮導中選擇&#x200B;**1x2分割螢幕通道**。

1. 按一下&#x200B;**Next**&#x200B;並將&#x200B;**title**&#x200B;輸入為&#x200B;**MultiZone**。

1. 按一下&#x200B;**Create**&#x200B;以完成通道建立。

### 在一或多個區域中使用單一資產{#using-single-assets-in-one-or-more-zones}

您可以在所有個別區域中使用單一資產，例如影像或視訊。 請依照下列步驟來實作：

1. **新增內容至頻道**

   1. 導航到&#x200B;**Zones** —> **Channels**—> **MultiZone**。
   1. 選擇&#x200B;**MultiZone**&#x200B;通道，然後從操作欄按一下&#x200B;**Edit**&#x200B;以開啟編輯器。

1. **將影像新增至通道**

   若要在兩個區域中播放單一影像或影片，只需將影像拖放至頻道編輯器中的每個區域，如下圖所示：

   ![影像](/help/user-guide/assets/multi-zone/multizone-img3.png)

### 在一個或多個區域中使用序列化內容{#using-sequenced-content-in-one-or-more-zones}

如果希望區域在不同區域中顯示影像和視頻的序列，請按照以下步驟了解詳細資訊。

1. **建立管道資料夾**

   1. 導航到&#x200B;**Zones** —> **MultiZone** —> **Channels**，然後從操作欄按一下&#x200B;**Create**。
   1. 從&#x200B;**Create**&#x200B;嚮導中選擇&#x200B;**Channels資料夾**，然後按一下&#x200B;**Next**。
   1. 輸入標題為&#x200B;**EmbeddedChannels** ，然後按一下&#x200B;**Create**。

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **新增兩個管道至管道資料夾**

   1. 導航到&#x200B;**Zones** —> **Channels** —> **EmbeddedChannels**，然後從操作欄按一下&#x200B;**Create**。
   1. 從&#x200B;**Create**&#x200B;嚮導中選擇&#x200B;**Sequence Channel**&#x200B;以建立標題為&#x200B;**Zone1**&#x200B;的通道。
   1. 選擇&#x200B;**Zone1**，然後從操作欄中按一下&#x200B;**Edit**&#x200B;以開啟編輯器。
   1. 將幾個影像拖放到此通道。
   1. 同樣地，在&#x200B;**EmbeddedChannels**&#x200B;資料夾中建立另一個名為&#x200B;**Zone2**&#x200B;的序列通道。
   1. 拖放視訊至此頻道。

   下圖顯示了通道&#x200B;**Zone1**&#x200B;和&#x200B;**Zone2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   新增至&#x200B;**Zone1**&#x200B;序列頻道編輯器的影像如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   新增至&#x200B;**Zone2**&#x200B;序列頻道編輯器的視訊如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **將嵌入序列（元件）添加到主通道(MultiZone)**

   1. 導航到&#x200B;**Zones** —> **Channels** —> **MultiZone**。
   1. 按一下動作列中的&#x200B;**編輯**&#x200B;以開啟編輯器。
   1. 將&#x200B;**Embedded Sequence**&#x200B;元件拖放到這兩個區域。
   1. 在其中一個區域中選擇嵌入序列。
   1. 按一下編輯器中其中一個內嵌序列的&#x200B;**設定**（扳手）圖示。
   1. 選擇通道路徑作為&#x200B;**Zones** —> **Channels** —> **EmbeddedChannels** —> **Zone1**，如下圖所示。
   1. 同樣地，將&#x200B;**Zone2**&#x200B;添加到編輯器中的另一個嵌入序列元件。

      ![影像](/help/user-guide/assets/multi-zone/multizone-3.png)

### 建立位置和顯示{#creating-location}

您必須建立位置和顯示器，才能檢視Screens播放器中的內容。 請依照下列步驟建立位置和顯示。

1. **建立位置**

   1. 導航到&#x200B;**Zones** —> **Locations**&#x200B;資料夾。
   1. 選擇&#x200B;**Locations**&#x200B;資料夾，然後從操作欄按一下&#x200B;**Create**。
   1. 從&#x200B;**Create**&#x200B;嚮導中選擇&#x200B;**Location**，然後按一下&#x200B;**Next**。
   1. 輸入&#x200B;**Title**&#x200B;作為&#x200B;**SanJose**，然後按一下&#x200B;**Create**。

1. **建立顯示**

   1. 導航到&#x200B;**Zones** —> **Locations**&#x200B;資料夾。
   1. 選擇&#x200B;**SanJose**&#x200B;位置，然後從操作欄按一下&#x200B;**Create**。
   1. 從&#x200B;**Create**&#x200B;嚮導中選擇&#x200B;**Display**，然後按一下&#x200B;**Next**。
   1. 輸入&#x200B;**Title**&#x200B;作為&#x200B;**Lobby**，然後按一下&#x200B;**Create**。

### 為顯示{#channel-channel}指定通道

您必須指派頻道給顯示，才能檢視內容。 請依照下列步驟，將管道指派給顯示器。

1. **為顯示指定通道**

   1. 導航到&#x200B;**Zones** —> **Locations** —> **SanJose**—> **Lobby**。
   1. 選擇&#x200B;**Lobby**&#x200B;顯示，然後從操作欄按一下&#x200B;**Assign Channel**。
   1. 在&#x200B;**通道路徑**&#x200B;中輸入&#x200B;**MultiZone**&#x200B;通道的路徑。
   1. 將&#x200B;**支援的事件**&#x200B;設定為&#x200B;**初始載入**、**空閒螢幕**&#x200B;和&#x200B;**計時器**。
   1. 按一下「**儲存**」。

      ![影像](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. 同樣，您必須將其他兩個嵌入通道（**Zone1**&#x200B;和&#x200B;**Zone2**）分配給此顯示。
   1. 將所有三個通道指派給&#x200B;**Lobby**&#x200B;顯示後，您應該可以從顯示控制面板檢視指派的通道。

      ![影像](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > 一旦將主通道（在此例中為&#x200B;**MultiZone**）指定給顯示器後，必須將其他兩個嵌入通道&#x200B;**Zone1**&#x200B;和&#x200B;**Zone2**&#x200B;也指定給同一顯示器。

### 註冊設備{#registering-device}

設定位置和顯示器後，請按照以下步驟註冊設備並為設備分配顯示器。

1. **註冊設備**

   1. 導航至&#x200B;**Zones** —> **Devices**&#x200B;資料夾。
   1. 選擇&#x200B;**Devices**&#x200B;資料夾，然後從操作欄按一下&#x200B;**Device Manager**。
   1. 按一下「**設備註冊**」並從清單中選擇掛起的設備。

      >[!NOTE]
      > 設備的標題必須與&#x200B;**Device Registration**&#x200B;頁簽中顯示的設備令牌（**Token**&#x200B;欄位）匹配。
   1. 如果標題與設備令牌匹配，則選擇設備，然後從操作欄中按一下&#x200B;**註冊設備**。
   1. 如果註冊代碼與Screens播放器&#x200B;**Device Registration**&#x200B;標籤中的代碼匹配，請按一下動作列中的&#x200B;**Validate**。
      ![影像](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. 將&#x200B;**Title**&#x200B;輸入為&#x200B;**Chrome-Device1**，然後按一下&#x200B;**Register**。
   1. 選擇&#x200B;**分配顯示**&#x200B;並選擇設備配置的路徑。

   >[!NOTE]
   >如果您嘗試在Screens播放器中檢視內容，請務必按一下頻道控制面板中指派給顯示的每個頻道的&#x200B;**更新離線內容**。

### 查看結果{#viewing-the-result}

使用前述步驟實施多區域佈局後，將顯示以下輸出。

勾選Screens播放器，以檢視顯示兩個不同區域內內容的輸出。 左和右區域（都使用嵌入序列作為元件）。

左區域是序列頻道，右區域包括視訊。

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)

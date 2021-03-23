---
title: 多區域版面
seo-title: 多區域版面
description: 多區域版面可讓您建立多個區域內容，並使用多種資產，例如視訊、影像和文字，這些資產可結合在單一畫面中。 請依照本頁進一步瞭解。
seo-description: 多區域版面可讓您建立多個區域內容，並使用多種資產，例如視訊、影像和文字，這些資產可結合在單一畫面中。 請依照本頁進一步瞭解。
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
feature: 製作畫面
role: 管理員、開發人員
level: 中級
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---


# 多區域佈局{#multi-zone-layout}

下頁說明多區域版面配置的使用，並涵蓋下列主題：

* 概覽
* 建立多區域版面
* 必備條件
* 在一或多個區域中使用單一資產
* 在一或多個區域中使用排序的內容

## 概覽 {#overview}

***多區域版*** 面可讓您建立多個區域內容，並使用多種資產，例如視訊、影像和文字，這些資產可以結合在單一畫面中。您可以拉進影像、視訊和文字，讓所有影像、視訊和文字融為一體，創造直覺式數位體驗。

根據專案需求，有時您需要一個通道中的多個區域，並將它們作為一個完整單元進行編輯。 例如，產品序列，其相關社交媒體摘要會在單一頻道的三個獨立區域中執行。


### 必備條件 {#prerequisites}

開始實作此功能之前，請確定您已具備以下概念性知識：

* [建立AEM Screens專案](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [建立顯示](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [指派頻道至顯示](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/channel-assignment.html)

## 建立多區域佈局{#creating-multi-zone-layout}

建立渠道時，您可以使用不同的範本，以便在渠道中建立區域。 您可以新增單一影像、視訊或內嵌頻道，讓多個資產可以在序列中顯示。

**建立渠道**

1. 選擇Adobe Experience Manager連結（左上角），然後選擇&#x200B;**螢幕**。 或者，您也可以直接前往：`http://localhost:4502/screens.html/content/screens`。
1. 導航到&#x200B;**Channels**&#x200B;資料夾，然後從操作欄按一下&#x200B;**Create**。

1. 從&#x200B;**建立**&#x200B;嚮導中選擇&#x200B;**1x2拆分螢幕通道**。

1. 按一下「**Next**」，然後將&#x200B;**title**&#x200B;輸入為&#x200B;**MultiZone**。

1. 按一下&#x200B;**建立**&#x200B;以完成通道建立。

### 在一或多個區域中使用單一資產{#using-single-assets-in-one-or-more-zones}

您可以在所有個別區域中使用單一資產，例如影像或視訊。 請依照下列步驟進行實施：

1. **新增內容至頻道**

   1. 導航至&#x200B;**Zones** —> **Channels**—> **MultiZone**。
   1. 選擇&#x200B;**MultiZone**&#x200B;頻道，然後從操作欄按一下&#x200B;**Edit**&#x200B;以開啟編輯器。

1. **將影像新增至頻道**

   若要在兩個區域中播放單一影像或視訊，只需將影像拖放至頻道編輯器中的每個區域，如下圖所示：

   ![影像](/help/user-guide/assets/multi-zone/multizone-img3.png)

### 在一個或多個區域中使用排序內容{#using-sequenced-content-in-one-or-more-zones}

如果您希望區域在不同區域中顯示影像和視頻的序列，請遵循以下步驟瞭解詳細資訊。

1. **建立渠道資料夾**

   1. 導覽至&#x200B;**Zones** —> **MultiZone** —> **Channels**，然後從操作欄按一下&#x200B;**Create**。
   1. 從&#x200B;**建立**&#x200B;嚮導中選擇&#x200B;**渠道資料夾** ，然後按一下&#x200B;**Next**。
   1. 將標題輸入為&#x200B;**EmbeddedChannels** ，然後按一下&#x200B;**Create**。

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **新增兩個渠道至渠道資料夾**

   1. 導覽至&#x200B;**Zones** —> **Channels** —> **EmbeddedChannels**，然後從操作欄按一下&#x200B;**Create**。
   1. 從&#x200B;**建立**&#x200B;嚮導中選擇&#x200B;**序列通道**&#x200B;以建立名為&#x200B;**區域1**&#x200B;的通道。
   1. 選擇&#x200B;**Zone1**，然後從操作欄按一下&#x200B;**Edit**&#x200B;以開啟編輯器。
   1. 將幾張影像拖放至此頻道。
   1. 同樣地，在&#x200B;**EmbeddedChannels**&#x200B;資料夾中建立另一個名為&#x200B;**Zone2**&#x200B;的序列頻道。
   1. 將視訊拖放至此頻道。

   下圖顯示了通道&#x200B;**Zone1**&#x200B;和&#x200B;**Zone2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   添加到&#x200B;**Zone1**&#x200B;序列通道編輯器的影像如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   添加到&#x200B;**Zone2**&#x200B;序列頻道編輯器的視頻如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **將嵌入序列（元件）添加到主通道（多區域）**

   1. 導航至&#x200B;**Zones** —> **Channels** —> **MultiZone**。
   1. 按一下操作欄中的&#x200B;**編輯**&#x200B;以開啟編輯器。
   1. 將&#x200B;**嵌入序列**&#x200B;元件拖放到兩個區域。
   1. 選擇其中一個區域中的嵌入序列。
   1. 在編輯器中，按一下其中一個內嵌序列的&#x200B;**Configure**（扳手）圖示。
   1. 選擇通道路徑作為&#x200B;**Zones** —> **Channels** —> **EmbeddedChannels** —> **Zone1**，如下圖所示。
   1. 同樣地，將&#x200B;**Zone2**&#x200B;添加到編輯器中的另一個嵌入式序列元件。

      ![影像](/help/user-guide/assets/multi-zone/multizone-3.png)

### 建立位置和顯示{#creating-location}

您必須建立位置和顯示，才能在「畫面」播放器中檢視內容。 請依照下列步驟建立位置和顯示。

1. **建立位置**

   1. 導航至&#x200B;**Zones** —> **Locations**&#x200B;資料夾。
   1. 選擇&#x200B;**Locations**&#x200B;資料夾，然後從操作欄中按一下&#x200B;**Create**。
   1. 從&#x200B;**建立**&#x200B;嚮導中選擇&#x200B;**位置** ，然後按一下&#x200B;**下一步**。
   1. 將&#x200B;**Title**&#x200B;輸入為&#x200B;**SanJose**，然後按一下&#x200B;**Create**。

1. **建立顯示**

   1. 導航至&#x200B;**Zones** —> **Locations**&#x200B;資料夾。
   1. 選擇&#x200B;**SanJose**&#x200B;位置，然後從操作欄中按一下&#x200B;**建立**。
   1. 從&#x200B;**建立**&#x200B;嚮導中選擇&#x200B;**顯示** ，然後按一下&#x200B;**Next**。
   1. 將&#x200B;**Title**&#x200B;輸入為&#x200B;**Lobby**，然後按一下&#x200B;**Create**。

### 為顯示{#channel-channel}指定頻道

您必須將頻道指派給顯示，才能檢視內容。 請依照下列步驟，將頻道指派給顯示器。

1. **將頻道指派給顯示**

   1. 導覽至&#x200B;**Zones** —> **Locations** —> **SanJose**—>**Lobby**。
   1. 選擇&#x200B;**Lobby**&#x200B;顯示，然後從操作欄按一下&#x200B;**Assign Channel**。
   1. 在&#x200B;**通道路徑**&#x200B;中輸入到&#x200B;**多區域**&#x200B;通道的路徑。
   1. 將「**受支援事件**」設定為「初始負載&#x200B;**」、「空閒螢幕**」和「計時器&#x200B;**」。******
   1. 按一下「**儲存**」。

      ![影像](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. 同樣地，您必須將其他兩個嵌入式通道（**Zone1**&#x200B;和&#x200B;**Zone2**）分配給此顯示。
   1. 在您將所有三個頻道指派給&#x200B;**Lobby**&#x200B;顯示後，您應可從顯示控制面板檢視指派的頻道。

      ![影像](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > 一旦將主通道（在本例中為&#x200B;**MultiZone**）分配給顯示器，則必須將其他兩個嵌入通道&#x200B;**Zone1**&#x200B;和&#x200B;**Zone2**&#x200B;也分配給同一顯示器。

### 註冊設備{#registering-device}

在您設定位置和顯示器後，請依照下列步驟註冊裝置並指派顯示器至裝置。

1. **註冊設備**

   1. 導航到&#x200B;**Zones** —> **Devices**&#x200B;資料夾。
   1. 選擇&#x200B;**Devices**&#x200B;資料夾，然後從動作列按一下&#x200B;**Device Manager**。
   1. 按一下「**設備註冊**」並從清單中選擇待審設備。

      >[!NOTE]
      > 設備的標題必須與&#x200B;**設備註冊**&#x200B;頁籤中顯示的設備Token（**Token**&#x200B;欄位）匹配。
   1. 如果標題與裝置Token相符，請選取裝置，然後從動作列按一下「註冊裝置」。****
   1. 如果註冊代碼與Screens player **Device Registration**&#x200B;標籤中的代碼相符，請從動作列按一下&#x200B;**Validate**。
      ![影像](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. 將&#x200B;**Title**&#x200B;輸入為&#x200B;**Chrome-Device1**，然後按一下「註冊&#x200B;**」。**
   1. 選擇&#x200B;**Assign Display**&#x200B;並選擇設備配置的路徑。

   >[!NOTE]
   >如果您嘗試在「畫面播放器」中檢視內容，請務必從頻道控制面板按一下「更新離線內容」，以取得指派給顯示器的每個頻道。****

### 查看結果{#viewing-the-result}

使用上述步驟實作多區域版面後，會顯示下列輸出。

勾選「畫面播放器」以檢視顯示兩個不同區域內內容的輸出。 左側和右側區域（兩者都使用嵌入序列作為元件）。

左區域是序列頻道，右區域包含視訊。

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)



---
title: 多區域版面
seo-title: 多區域版面
description: 多區域版面可讓您建立多個區域內容，並使用多種資產，例如視訊、影像和文字，這些資產可結合在單一畫面中。 請依本頁瞭解詳細資訊。
seo-description: 多區域版面可讓您建立多個區域內容，並使用多種資產，例如視訊、影像和文字，這些資產可結合在單一畫面中。 請依本頁瞭解詳細資訊。
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
translation-type: tm+mt
source-git-commit: 052cf1ccde6f18ec72307b14ffbac63be61127b0
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 0%

---


# 多區域版面 {#multi-zone-layout}

下頁說明多區域版面配置的使用，並涵蓋下列主題：

* 概覽
* 建立多區域版面
* 必備條件
* 在一或多個區域中使用單一資產
* 在一或多個區域中使用排序的內容

## 概覽 {#overview}

***多區域版面*** (Multi-zone Layout)可讓您建立多個區域內容，並使用多種資產，例如視訊、影像和文字，這些資產可結合在單一畫面中。 您可以拉進影像、視訊和文字，讓所有影像、視訊和文字融為一體，創造直覺式數位體驗。

根據專案需求，有時您需要一個通道中的多個區域，並將它們作為一個完整單元進行編輯。 例如，產品序列，其相關社交媒體摘要會在單一頻道的三個獨立區域中執行。


### 必備條件 {#prerequisites}

在開始實作此功能之前，請確定您對以下方面的概念性知識：

* [建立AEM Screens專案](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [建立顯示](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [指派頻道至顯示](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/channel-assignment.html)

## 建立多區域版面 {#creating-multi-zone-layout}

建立渠道時，您可以使用不同的範本，以便在渠道中建立區域。 您可以新增單一影像、視訊或內嵌頻道，讓多個資產可以在序列中顯示。

**建立渠道**

1. 依序選取Adobe Experience Manager連結（左上）和「畫 **面」**。 或者，您也可以直接前往： `http://localhost:4502/screens.html/content/screens`.
1. 導覽至「 **Channels** 」檔案夾，然後按 **一下動作列中的「** 建立」。

1. 從「 **建立」精靈中選取** 1x2「分割 **畫面頻道** 」。

1. 按一下「 **Next** (下一步 **)」 ，然後將標題** 輸入為 **「** MultiZone（多區域）」。

1. 按一 **下「建立** 」以完成渠道建立。

### 在一或多個區域中使用單一資產 {#using-single-assets-in-one-or-more-zones}

您可以在所有三個不同的區域中使用單一資產，例如影像或視訊。 請依照下列步驟進行實施：

1. **新增內容至頻道**

   1. 導覽至 **Zones** —> **Channels**—> **MultiZone**。
   1. 選擇「 **MultiZone** 」(多區域 **)頻道，然後從操** 作欄按一下「編輯」以開啟編輯器。

1. **將影像新增至頻道**

   若要在兩個區域中播放單一影像或視訊，只需將影像拖放至頻道編輯器中的每個區域，如下圖所示：

   ![影像](/help/user-guide/assets/multi-zone/multizone-img3.png)

### 在一或多個區域中使用排序的內容 {#using-sequenced-content-in-one-or-more-zones}

如果您希望區域在兩個不同區域中顯示影像和視頻的序列，請遵循以下步驟瞭解詳細資訊。

1. **建立渠道資料夾**

   1. 導航至「 **區域** 」 —>「多 **區域** 」 —>「通道」 **，然後從操****** 作欄中按一下「建立」。
   1. 從「建 **立」精靈中選取「頻道資料夾** 」，然後按一下「下 **一步******」。
   1. 輸入標題為 **EmbeddedChannels** ，然後單 **擊Create**。
   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **新增兩個渠道至渠道資料夾**

   1. 導覽至「 **Zones** —> **Channels** —> **EmbeddedChannels** 」 ，然後從操作欄 **** 中按一下「建立Create Channels」。
   1. 從「 **建立** 」精靈中選取「順序渠道」，以建立名為「 **Zone1」的渠道******。
   1. 選擇 **Zone1** ，然後從操作欄 **中按一下Edit** （編輯）以開啟編輯器。
   1. 將幾張影像拖放至此頻道。
   1. 同樣地，在EmbeddedChannels資料夾中建立另一個名 **為Zone2** 的 **序列渠道** 。
   1. 將視訊拖放至此頻道。
   下圖顯示了通道 **Zone1** 和 **Zone2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   新增至 **Zone1序列頻道編輯器的影像** ，如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   新增至 **Zone2序列頻道編輯器的視訊** ，如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **將嵌入序列（元件）添加到主通道（多區域）**

   1. 導覽至 **Zones** —> **Channels** —> **MultiZone**。
   1. 按一 **下動作列** 中的「編輯」以開啟編輯器。
   1. 將「嵌入序列」( **Embedded Sequence** )元件拖放到兩個區域。
   1. 選擇其中一個區域中的嵌入序列。
   1. 在編輯器 **中，按一下其中一個內嵌序列的「設定** （扳手）」圖示。
   1. 選擇通道路徑 **為Zones** —> **Channels** —> **EmbeddedChannels** —> **** Zone1Zone，如下圖所示。
   1. 同樣地，將 **Zone2添加到** editor中另一個嵌入序列元件。

      ![影像](/help/user-guide/assets/multi-zone/multizone-3.png)

### 建立位置和顯示 {#creating-location}

您必須建立位置和顯示，才能在「畫面」播放器中檢視內容。 請依照下列步驟建立位置和顯示。

1. **建立位置**

   1. 導航至 **Zones** —> **Locations** 資料夾。
   1. 選擇「位 **置** 」資料夾，然後從操作 **欄中按一下「建立** 」。
   1. 從「創 **建」嚮導中選** 擇「位置 **」，然後按一下「** 下一步 ****」。
   1. 將標題輸 **入為** SanJose **，然後按一** 下建立 ****。

1. **建立顯示**

   1. 導航至 **Zones** —> **Locations** 資料夾。
   1. 選擇 **SanJose位置** ，然後從操作 **欄中按一下Create** 。
   1. 從「創 **建** 」嚮導中選擇「顯 **示」** ，然後按一下「 **下一步**」。
   1. 將標題輸 **入為** Lobby **，然後按一下** 建立 ****。

### 將頻道指派給顯示 {#channel-channel}

您必須將頻道指派給顯示，才能檢視內容。 請依照下列步驟，將頻道指派給顯示器。

1. **將頻道指派給顯示**

   1. 導覽至 **Zones** —> **Locations** —> **SanJose**— ****> Lobby Lebby Clobby
   1. 選取「 **Lobby** 」（大堂）顯示，然後從 **動作列按一下「Assign Channel** 」（指派頻道）。
   1. 在「通道路徑」中 **輸入MultiZone** 通道 **的路徑**。
   1. 將支援的 **事件設定為** 「初始 **負載」、「**&#x200B;空閒螢幕 **」和「******&#x200B;計時器」。
   1. 按一下&#x200B;**「儲存」**。

      ![影像](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. 同樣地，您必須將其他兩個嵌入通道(**Zone1****和Zone2**)分配給此顯示。
   1. 在您將所有三個頻道指派給 **Lobby** display後，您就可以從顯示控制面板檢視指派的頻道。

      ![影像](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!I重要]
      > 一旦將主通道(在本例中為 **MultiZone**)指定給顯示器，則必須將其他兩個嵌入通道 **Zone1** 和 **** Zone2也指定給同一顯示器。

### 註冊設備 {#registering-device}

在您設定位置和顯示器後，請依照下列步驟註冊裝置並指派顯示器至裝置。

1. **註冊設備**

   1. 導覽至 **Zones** —> **Devices** 資料夾。
   1. 選擇「 **Devices** （設備）」資料夾，然後從操 **作欄中按一下「Device Manager** （設備管理器）」。
   1. 按一 **下「裝置註冊** 」，然後從清單中選取待審裝置。
      >[!NOTE]
      > 裝置的標題必須符合「裝置註冊」標籤中顯&#x200B;**示的裝置Token** ( **Token欄位)** 。
   1. 如果標題符合裝置Token，請選取裝置，然後從動作列按一 **下「註冊裝置** 」。
   1. 如果註冊代碼與「Screens player **Device Registration** 」（畫面播放器裝置註冊）標籤中的代碼相符 **，請按一下** 動作列中的「Validate」（驗證）。
      ![影像](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. 將「標 **題** 」輸 **入為Chrome-Device1** ，然後按一 **下「註冊**」。
   1. 選擇 **指定顯示** ，然後選擇設備配置的路徑。
   >[!NOTE]
   >如果您嘗試在「畫面播放器」中檢視內容，請務必按一下「頻道控制面板 **中的更新離線內容** 」。

### 查看結果 {#viewing-the-result}

使用上述步驟實作多區域版面後，會顯示下列輸出。

勾選「畫面播放器」以檢視顯示兩個不同區域內內容的輸出。 左側和右側區域（兩者都使用嵌入序列作為元件）。

左區域是序列頻道，右區域包含視訊。

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)



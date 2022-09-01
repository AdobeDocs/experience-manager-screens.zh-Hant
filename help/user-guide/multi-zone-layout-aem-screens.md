---
title: 多區域佈局
seo-title: Multi-zone Layout
description: 「多區域版面」可讓您建立多個區域內容，並使用各種資產，例如視訊、影像和文字，這些資產可在單一畫面中結合。 請詳閱本頁以了解更多。
seo-description: Multi-zone Layout allows you to create multiple zone content and use a variety of assets such as videos, images and text that can be combined in a single screen. Follow this page to learn more.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 0%

---

# 多區域佈局 {#multi-zone-layout}

以下頁面說明多區域版面的使用方式，並涵蓋下列主題：

* 總覽
* 建立多區域佈局
* 必備條件
* 在一或多個區域中使用單一資產
* 在一個或多個區域中使用序列內容

## 總覽 {#overview}

***多區域佈局*** 可讓您建立多個區域內容，並使用各種資產，例如視訊、影像和文字，這些可在單一畫面中結合。 您可以提取影像、影片和文字，讓影像、影片和文字融為一體，打造直覺的數位體驗。

根據專案需求，有時您需要在通道中建立多個區域，並以一個完整單位編輯這些區域。 例如，產品序列與相關的社交媒體摘要，會在單一管道的三個獨立區域中執行。


### 必備條件 {#prerequisites}

開始實作此功能之前，請確定您具備下列概念知識：

* [建立AEM Screens專案](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [建立顯示](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [為顯示指定通道](/help/user-guide/channel-assignment.md)

## 建立多區域佈局 {#creating-multi-zone-layout}

建立管道時，您可以使用不同的範本，在管道中建立區域。 您可以新增單一影像、視訊或內嵌通道，讓多個資產可依序顯示。

**建立管道**

1. 選取Adobe Experience Manager連結（左上角），然後 **Screens**. 或者，您也可以直接前往： `http://localhost:4502/screens.html/content/screens`.
1. 導覽至 **管道** 資料夾，按一下 **建立** 從動作列。

1. 選擇 **1x2分屏通道** 從 **建立** 嚮導。

1. 按一下 **下一個** 並輸入 **標題** as **多區域**.

1. 按一下 **建立** 以完成管道建立。

### 在一或多個區域中使用單一資產 {#using-single-assets-in-one-or-more-zones}

您可以在所有個別區域中使用單一資產，例如影像或視訊。 請依照下列步驟來實作：

1. **新增內容至頻道**

   1. 導覽至 **區域** —> **管道**—> **多區域**.
   1. 選取 **多區域** 頻道和點按 **編輯** 從動作列開啟編輯器。

1. **將影像新增至通道**

   若要在兩個區域中播放單一影像或影片，只需將影像拖放至頻道編輯器中的每個區域，如下圖所示：

   ![影像](/help/user-guide/assets/multi-zone/multizone-img3.png)

### 在一個或多個區域中使用序列內容 {#using-sequenced-content-in-one-or-more-zones}

如果希望區域在不同區域中顯示影像和視頻的序列，請按照以下步驟了解詳細資訊。

1. **建立管道資料夾**

   1. 導覽至 **區域** —> **多區域** —> **管道** 按一下 **建立** 從動作列。
   1. 選擇 **通道資料夾** 從 **建立** 精靈，按一下 **下一個**.
   1. 將標題輸入為 **內嵌通道** 按一下 **建立**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **新增兩個管道至管道資料夾**

   1. 導覽至 **區域** —> **管道** —> **內嵌通道** 按一下 **建立** 從動作列。
   1. 選擇 **序列頻道** 從 **建立** 建立管道的精靈，名為 **區域1**.
   1. 選擇 **區域1** 按一下 **編輯** 從動作列開啟編輯器。
   1. 將幾個影像拖放到此通道。
   1. 同樣地，請建立另一個序列管道，標題為 **區域2** in **內嵌通道** 檔案夾。
   1. 拖放視訊至此頻道。

   下圖顯示了通道 **區域1** 和 **區域2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   新增至的編輯器的影像 **區域1** 序列通道如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   新增至的編輯器的影片 **區域2** 序列通道如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **將嵌入序列（元件）添加到主通道(MultiZone)**

   1. 導覽至 **區域** —> **管道** —> **多區域**.
   1. 按一下 **編輯** 從動作列開啟編輯器。
   1. 拖放 **嵌入序列** 元件。
   1. 在其中一個區域中選擇嵌入序列。
   1. 按一下 **設定** （扳手）圖示，顯示編輯器中其中一個內嵌序列。
   1. 選取通道路徑作為 **區域** —> **管道** —> **內嵌通道** —> **區域1**，如下圖所示。
   1. 同樣地，新增 **區域2** 到編輯器中的另一個嵌入序列元件。

      ![影像](/help/user-guide/assets/multi-zone/multizone-3.png)

### 建立位置和顯示 {#creating-location}

建立位置和顯示器以檢視Screens播放器中的內容。

1. **建立位置**

   1. 導覽至 **區域** —> **位置** 檔案夾。
   1. 選取 **位置** 資料夾，按一下 **建立** 從動作列。
   1. 選擇 **位置** 從 **建立** 精靈，按一下 **下一個**.
   1. 輸入 **標題** as **聖荷西** 按一下 **建立**.

1. **建立顯示**

   1. 導覽至 **區域** —> **位置** 檔案夾。
   1. 選取 **聖荷西** 位置，按一下 **建立** 從動作列。
   1. 選擇 **顯示** 從 **建立** 精靈，按一下 **下一個**.
   1. 輸入 **標題** as **大堂** 按一下 **建立**.

### 為顯示指定通道 {#channel-channel}

將頻道指派給顯示以檢視內容。 請依照下列步驟，將管道指派給顯示器。

1. **為顯示指定通道**

   1. 導覽至 **區域** —> **位置** —> **聖荷西**—> **大堂**.
   1. 選取 **大堂** 顯示和點按 **指派管道** 從動作列。
   1. 輸入路徑 **多區域** 頻道 **通道路徑**.
   1. 設定 **支援的事件** as **初始載入**, **空閒螢幕**，和 **計時器**.
   1. 按一下「**儲存**」。

      ![影像](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. 同樣地，您必須指派其他兩個內嵌通道(**區域1** 和 **區域2**)顯示。
   1. 將這三個管道指派給 **大堂** 顯示時，您應該可以從顯示控制面板檢視指派的通道。

      ![影像](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > 指派主管道後(在此例中， **多區域**)，則必須指派其他兩個內嵌通道 **區域1** 和 **區域2** 也會顯示在相同的顯示畫面中。

### 註冊設備 {#registering-device}

設定位置和顯示器後，請按照以下步驟註冊設備並為設備分配顯示器。

1. **註冊設備**

   1. 導覽至 **區域** —> **裝置** 檔案夾。
   1. 選取 **裝置** 資料夾，按一下 **裝置管理員** 從動作列。
   1. 按一下 **設備註冊** 並從清單中選擇掛起的設備。

      >[!NOTE]
      > 裝置的標題必須符合裝置代號(**代號** 欄位) **設備註冊** 標籤。
   1. 如果標題符合裝置代號，請選取裝置，然後按一下 **註冊設備** 從動作列。
   1. 如果註冊代碼與Screens播放器中的代碼匹配 **設備註冊** 按一下 **驗證** 從動作列。
      ![影像](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. 輸入 **標題** as **Chrome-Device1** 按一下 **註冊**.
   1. 選擇 **分配顯示** 並選擇設備配置的路徑。

   >[!NOTE]
   >如果您嘗試在Screens播放器中檢視內容，請確定您按一下 **更新離線內容** 從「管道」控制面板，針對指派給顯示的每個管道。

### 查看結果 {#viewing-the-result}

使用前述步驟實施多區域佈局後，將顯示以下輸出。

勾選Screens播放器，以檢視顯示兩個不同區域內內容的輸出。 左和右區域（都使用嵌入序列作為元件）。

左區域是序列頻道，右區域包括視訊。

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)

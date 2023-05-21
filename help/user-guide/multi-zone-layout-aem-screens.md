---
title: 多區域佈局
seo-title: Multi-zone Layout
description: 多區域佈局允許您建立多個區域內容，並使用可在單個螢幕中組合的視頻、影像和文本等各種資源。 請按照此頁瞭解詳細資訊。
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

下頁介紹了多區域佈局的用法，並介紹以下主題：

* 概觀
* 建立多區域佈局
* 必備條件
* 在一個或多個區域中使用單個資產
* 在一個或多個區域中使用序列內容

## 概觀 {#overview}

***多區域佈局*** 允許您建立多個區域內容並使用各種資源，如視頻、影像和文本，這些資源可以組合在一個螢幕中。 您可以將影像、視頻和文本拉入其中，使其全部融合在一起，並建立直觀的數字型驗。

根據項目要求，有時您需要一個通道中的多個區域，並將它們作為一個綜合單元進行編輯。 例如，具有相關社交媒體源的產品序列，它在一個頻道上運行在三個獨立的區域中。


### 必備條件 {#prerequisites}

在開始實施此功能之前，請確保您對以下方面有概念性知識：

* [建立AEM Screens項目](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [建立顯示](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [為顯示器分配通道](/help/user-guide/channel-assignment.md)

## 建立多區域佈局 {#creating-multi-zone-layout}

建立通道時，可以使用不同的模板在通道中建立區域。 您可以添加單個影像、視頻或嵌入通道，允許按順序顯示多個資產。

**建立通道**

1. 選擇Adobe Experience Manager連結（左上），然後 **螢幕**。 或者，您可以直接訪問： `http://localhost:4502/screens.html/content/screens`。
1. 導航到 **頻道** 資料夾，按一下 **建立** 按鈕。

1. 選擇 **1x2分屏通道** 從 **建立** 的子菜單。

1. 按一下 **下一個** 輸入 **標題** 如 **多區域**。

1. 按一下 **建立** 以完成通道建立。

### 在一個或多個區域中使用單個資產 {#using-single-assets-in-one-or-more-zones}

可以在所有單獨的區域中使用單個資產，如影像或視頻。 按照以下步驟執行：

1. **將內容添加到渠道**

   1. 導航到 **區域** —> **頻道**—> **多區域**。
   1. 選擇 **多區域** 按一下 **編輯** 的子菜單。

1. **向通道添加映像**

   要在兩個區域中播放單個影像或視頻，只需將影像拖放到通道編輯器中的每個區域，如下圖所示：

   ![影像](/help/user-guide/assets/multi-zone/multizone-img3.png)

### 在一個或多個區域中使用序列內容 {#using-sequenced-content-in-one-or-more-zones}

如果希望區域顯示不同區域中的影像和視頻序列，請按照以下步驟瞭解詳細資訊。

1. **建立通道資料夾**

   1. 導航到 **區域** —> **多區域** —> **頻道** 按一下 **建立** 按鈕。
   1. 選擇 **通道資料夾** 從 **建立** 嚮導 **下一個**。
   1. 輸入標題為 **嵌入式通道** 按一下 **建立**。

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **向通道資料夾添加兩個通道**

   1. 導航到 **區域** —> **頻道** —> **嵌入式通道** 按一下 **建立** 按鈕。
   1. 選擇 **序列通道** 從 **建立** 嚮導，建立標題為 **區域1**。
   1. 選擇 **區域1** 按一下 **編輯** 的子菜單。
   1. 將很少的影像拖放到此通道。
   1. 同樣，建立另一個名為 **區域2** 在 **嵌入式通道** 的子菜單。
   1. 將視頻拖放到此頻道。

   下圖顯示了通道 **區域1** 和 **區域2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   添加到的編輯器中的影像 **區域1** 序列通道如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   添加到的編輯器中的視頻 **區域2** 序列通道如下所示：

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **將嵌入序列（元件）添加到主通道(MultiZone)**

   1. 導航到 **區域** —> **頻道** —> **多區域**。
   1. 按一下 **編輯** 的子菜單。
   1. 拖放 **嵌入序列** 元件。
   1. 選擇其中一個區域中的嵌入序列。
   1. 按一下 **配置** （扳手）表徵圖。
   1. 選擇通道路徑作為 **區域** —> **頻道** —> **嵌入式通道** —> **區域1**，如下圖所示。
   1. 同樣，添加 **區域2** 到編輯器中的其他嵌入序列元件。

      ![影像](/help/user-guide/assets/multi-zone/multizone-3.png)

### 建立位置和顯示 {#creating-location}

建立位置和顯示器以查看螢幕播放器中的內容。

1. **建立位置**

   1. 導航到 **區域** —> **位置** 的子菜單。
   1. 選擇 **位置** 資料夾，按一下 **建立** 按鈕。
   1. 選擇 **位置** 從 **建立** 嚮導 **下一個**。
   1. 輸入 **標題** 如 **聖何塞** 按一下 **建立**。

1. **建立顯示**

   1. 導航到 **區域** —> **位置** 的子菜單。
   1. 選擇 **聖何塞** 按一下 **建立** 按鈕。
   1. 選擇 **顯示** 從 **建立** 嚮導 **下一個**。
   1. 輸入 **標題** 如 **大堂** 按一下 **建立**。

### 將通道指派給顯示 {#channel-channel}

將頻道分配給顯示器以查看內容。 按照以下步驟將通道指定給顯示器。

1. **為顯示器分配通道**

   1. 導航到 **區域** —> **位置** —> **聖何塞**—> **大堂**。
   1. 選擇 **大堂** 顯示並按一下 **分配通道** 按鈕。
   1. 輸入路徑 **多區域** 通道 **通道路徑**。
   1. 設定 **支援的事件** 如 **初始載入**。 **空閒螢幕**, **計時器**。
   1. 按一下「**儲存**」。

      ![影像](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. 同樣，您必須指定其他兩個嵌入式通道(**區域1** 和 **區域2**)顯示。
   1. 將所有三個通道分配給 **大堂** 顯示時，您應該能夠從顯示操控板中查看指定的通道。

      ![影像](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > 一旦指定了主通道(在本例中， **多區域**)顯示時，必須指定其他兩個嵌入式通道 **區域1** 和 **區域2** 同一顯示。

### 註冊設備 {#registering-device}

設定位置和顯示器後，請按照以下步驟註冊設備並為設備分配顯示。

1. **註冊設備**

   1. 導航到 **區域** —> **設備** 的子菜單。
   1. 選擇 **設備** 資料夾，按一下 **設備管理器** 按鈕。
   1. 按一下 **設備註冊** 並從清單中選擇待處理設備。

      >[!NOTE]
      > 設備的標題必須與設備令牌(**令牌** 欄位) **設備註冊** 頁籤。
   1. 如果標題與設備令牌匹配，則選擇設備並按一下 **寄存器設備** 按鈕。
   1. 如果註冊代碼與螢幕播放器中的代碼匹配 **設備註冊** 按鈕 **驗證** 按鈕。
      ![影像](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. 輸入 **標題** 如 **鉻設備1** 按一下 **註冊**。
   1. 選擇 **分配顯示** 並選擇設備配置的路徑。

   >[!NOTE]
   >如果試圖查看螢幕播放器中的內容，請確保按一下 **更新離線內容** 從「通道」操控板中為分配給顯示的每個通道指定。

### 查看結果 {#viewing-the-result}

使用上述步驟實施多區域佈局後，將顯示以下輸出。

選中「螢幕」播放器以查看顯示兩個不同區域內內容的輸出。 左區域和右區域（都使用嵌入序列作為元件）。

左區域是序列通道，右區域包括視頻。

![新2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)

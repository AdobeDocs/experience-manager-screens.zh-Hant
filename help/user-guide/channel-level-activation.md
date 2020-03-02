---
title: 頻道層級啟動——單一事件播放
seo-title: 頻道層級啟動——單一事件播放
description: 請依照本指南，瞭解使用單一事件播放的頻道層級啟動。
seo-description: 請依照本指南，瞭解使用單一事件播放的頻道層級啟動。
uuid: 87230344-5f9a-42a4-a7a8-ae4203303612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: c28fd669-f23e-4d53-bec1-a2911274567d
noindex: true
translation-type: tm+mt
source-git-commit: 1dbbe62875cdc1a0c1c7d5fe45221d7ebd12207f

---


# 通路層級啟動 {#channel-level-activation-single-event-playback}

使用渠道層級啟動涵蓋下列主題：

* 概覽
* 將頻道層級啟動當成單一事件播放

## 概覽 {#overview}

***「渠道層級啟動*** 」允許渠道在特定的排程後切換。 單事件頻道在設定排程後取代主頻道並播放特定時間，直到主頻道再次播放其內容。

以下範例針對下列關鍵詞提供解決方案：

* 全 ***局序列的主序列*** (channel)
* 一 ***次只執行一次的單一事件渠道*** ,
* 為主 ***序列頻道內發生的單一播放事件*** ，設定排程和優先順序

## 使用渠道層級啟動 {#using-channel-level-activation}

下節將說明如何在AEM Screens專案的頻道內建立單一事件播放。

### 必備條件 {#prerequisites}

開始實作此功能之前，請確定您已具備下列必要條件，可開始實作渠道層級啟動：

* 建立AEM Screens專案，在此範例中為「頻道 **層級啟動」**

* 在「頻道」資料夾 **下建立頻道** ，做 **為MainAdChannel**

* 在「頻道」資料夾 **下建立另一個頻道** ，做 **為TargetedSinglePlay**

* 將相關資產新增至兩個通道

下圖顯示MainAdChannel **和TargetedSinglePlayChannels資料夾** 中的Channel Level Activation **專案，其中包** 含MainAdChannel **和****** TargetedSinglePlayChannels資料夾。

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>如需如何建立專案以及如何建立序列頻道的詳細資訊，請參閱下列資源：
>
>* [建立和管理專案](creating-a-screens-project.md)
   >
   >
* [管理渠道](managing-channels.md)
>



### 實施 {#implementation}

在AEM Screens專案中實作「頻道層級啟動」需執行三項主要工作：

1. **設定項目分類法，包括渠道、位置和顯示**
1. **指派頻道以顯示**
1. **設定排程和優先順序**

請依照下列步驟來實作功能：

1. **建立位置**

   導覽至AEM Screens專 **案中的** Locations檔案夾，並建立「地區」 **位置**。

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >要瞭解如何建立位置，請參閱創 **[建和管理位置](managing-locations.md)**。

1. **在「位置」下建立顯示**

   1. 導覽至「 **渠道層級啟動** >位 **置** >地 **區」**。
   1. 選擇「 **地區** 」(Region **)，然後從操作欄中按一下「+建立** 」(Create)。
   1. 從向 **導中選擇** 「顯示」，並建立標題為「區域顯 **示」的顯示。**
   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **指定要顯示的渠道**

   針對 **MainAdChannel:**

   1. 導航至「渠 **道級激活** > **>** > **>********** Display Channel Locations 」區域從操作中按一下Display Channel Click Bar。
   1. **「渠道分配** 」對話框開啟。
   1. 選擇 **參考渠道**。 依路徑.
   1. 選擇「通 **道路徑****級激活」** —>「通 ***道*** 」 — ******>「主AdChannel」。
   1. 渠道 **角色** (Channel Role **)會填**&#x200B;入為mainadchannel。
   1. 選擇「優 **先順序** 」( **Priority**)為1。
   1. 選取「支 **援的事件** 」(Supported Events **)** 為「初始載入 **」(Initial Load)**&#x200B;和「閒置」(Idle)畫面。
   1. 按一下&#x200B;**「儲存」**。
   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >您也可以從顯示儀表板通過以下方式來分配渠道： **渠道級激活** —> **位置** —> **Locations** Region — **> Display Display Dashboard和Clicking Adshboard****** brar。 從「已 **指派的頻道與排程** 」面板按 **一下「+指派頻道** 」。

   同樣地，指派頻道 **TargetedSinglePlay** 以進行顯示**:

   1. 導航至「 **渠道級別激活** —>位 **置** —> **地區** — ******** >地區顯示欄」和「從活動中分配渠道激活」。
   1. **「渠道分配** 」對話框開啟。
   1. 選擇 **參考渠道**。 依路徑.
   1. 選擇渠 **道路徑****作為渠道級激活*** —> ***渠道*** — ***>目標單***&#x200B;一播放。
   1. 渠道 **角色** (Channel Role)會填 **入為定位單一播放**。
   1. 將「優 **先順序** 」設 **為2**。
   1. 選擇「受 **支援的事件** 」作 **為「初始載入**」、「空閒 **螢幕」和「計******&#x200B;時器」*，如下圖所示。
   1. 選擇有效日 **期** ，從2018年11月27日 **11:59 pm開始，有效到2018年11月** 28日12:05 am。
   1. 按一下&#x200B;**「儲存」**。
   >[!CAUTION]
   您必須將 **TargetedSinglePlay頻道的優先順序設** 定在高於 **MainAdSegment頻道** 的位置。

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   要選擇同一天，您必須選擇第二天，然後手動將日期編輯為同一天，但是稍後。 這會限制使用者選取過去的日期。 請參閱以下範例：

   ![new1](assets/new1.gif)

## 查看結果 {#viewing-the-results}

在您設定頻道和顯示完成後，請啟動AEM Screens播放器以檢視內容。

播放器會顯示 **MainAdChannel** ，並在晚上11:59（如排程中所設定）時， **TargetedSinglePlay** 頻道會顯示其內容，直到上午12:05，然後 **** MainAdChannel將會再次繼續播放其內容。

>[!NOTE]
若要瞭解AEM Screen Player，請參閱下列資源：
* [AEM Screens Player下載](https://download.macromedia.com/screens/)
* [使用AEM Screens Player](working-with-screens-player.md)


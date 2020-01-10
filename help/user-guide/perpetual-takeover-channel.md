---
title: Perpetual TakeOver Channel
seo-title: Perpetual TakeOver Channel
description: 請依照此使用案例來建立永久TakeOver頻道。
seo-description: 請依照本使用案例，設定專案，以建立持續播放特定時間日與時間的永久接管頻道。
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 874ddde28be840d0dcac197e48ca579a12661994

---


# Perpetual TakeOver Channel {#perpetual-takeover-channel}

下頁展示了一個使用案例，重點說明如何設定專案，以建立持續播放特定時間日與時間的永久TakeOver頻道。

## 使用案例說明 {#use-case-description}

此使用案例說明如何為顯示器 *或顯示器* 群組建立從正常播放的頻道接管的頻道。 接管將持續在特定日期和時間內進行。
例如，有一個永久TakeOver頻道，每週五從上午9點到上午10點播放。 在此期間，不應播放其他頻道。 以下範例展示建立永久接管頻道的方式，讓內容每週三從下午2:00至4:00播放2小時。

### 先決條件 {#preconditions}

開始此使用案例之前，請務必瞭解如何：

* **[建立和管理渠道](managing-channels.md)**
* **[建立和管理位置](managing-locations.md)**
* **[建立和管理計畫](managing-schedules.md)**
* **[裝置註冊](device-registration.md)**

### 主要操作者 {#primary-actors}

內容作者

## 設定專案 {#setting-up-the-project}

請依照下列步驟設定專案：

**設定頻道和顯示**

1. 建立標題為 **PerpetualTakeOver的AEM Screens專案**，如下所示。

   ![資產](assets/p_usecase1.png)

1. 在「頻 **道」檔案夾中** ，建立 **MainAdChannel** 。

   ![資產](assets/p_usecase2.png)

1. 選取 **MainAdChannel** ，然後從動 **作列按一下「編輯** 」。 將部分資產（影像、視訊、內嵌序列）拖放至您的頻道。

   ![資產](assets/p_usecase3.png)


   >[!NOTE]
   >此范 **例中的MainAdChannel** ，會示範連續播放內容的序列頻道。

1. 建立 **TakeOver** 頻道，以接管 **** MainAdChannel中的內容，並將於每週三下午2:00至4:00播放。

1. 選擇「 **TakeOver** 」，然後從操 **作欄中按一下「Edit** 」（編輯）。 將一些資產拖放至您的渠道。 下列範例將展示新增至此頻道的單一區域影像。

   ![資產](assets/p_usecase4.png)

1. 設定頻道的位置和顯示。 例如，為此項目設 **定了以下位** 置MainLobby **和** display mainLobbyDisplay。

   ![資產](assets/p_usecase5.png)

**將頻道指派給顯示**

1. 從「位置」 **資料夾中選取顯** 示MainLobbyDisplay **** (MainLobbyDisplay)。 從操 **作欄按一下「指定渠道** 」，以開啟「渠道 **** 指定」對話方塊。

   >[!NOTE]
   >若要瞭解如何指派頻道至顯示器，請參閱頻道 **[指派](channel-assignment.md)**。

1. 從&#x200B;**Channel AssignmentSave和click to assignTheMainChannel Ad Ad** to your display中，填入Channel Path **、Priority**&#x200B;和Supported Events **(Channel Path、Priority**&#x200B;和Events ************ )欄位（ChannelPrioriorityPoriority,Pority，優先順序和受支援事件）。

   * **渠道路徑**:選取MainAdChannel頻道 **的路徑** 。
   * **優先順序**:將此渠道的優先順序設定為1。
   * **支援的事件**:選擇「 **初始載入** 」和「 **空閒」螢幕**。
   ![資產](assets/p_usecase6.png)

1. 從「位置」 **資料夾中** ，選 **取顯示TakeOver** 。 從動 **作列按一下「指定渠道** 」，以指定接管渠道。

1. 若要在排 **程時將TakeOver** 頻道指派給您的顯示，並從「頻道指派」對話方塊填入下列欄位，然後按一下「儲 **存******」:

   * **渠道路徑**:選取TakeOver頻道的 **路徑** 。
   * **優先順序**:將此頻道的優先順序設定為大於 **MainAdChannel**。 例如，此範例中的優先順序設定為8。
   * **支援的事件**:選擇「 **Idle Screen** (空閒屏 **幕)」和「Timer（計時器）**」。
   * **排程**:輸入您希望此渠道執行顯示的排程文字。 此範例中提 **及的** 「排程」中的文字 *是星期三14:00後和16:00前*。
      >[!NOTE]
      >若要進一步瞭解可新增至排程的運算式 **，請參閱下方**&#x200B;的「範例運算式 [](#example-expressions) 」區段。
   * **活動自**:開始日期和時間。
   * **活動到**:結束日期和時間。
   例如，此處「排程」中 **的文字和「從** 」和「活動到」的 ******** 文字可讓內容在每週三的下午2:00到4:00之間播放。


   ![資產](assets/p_usecase7.png)

   從TakeOver **—>** Locations **—** MainLobby **>** MainLobby大堂— **MainLobby DisplayBar導航到分配的優先順序渠道的視圖（如下所示）中的TakeOver****** —> Locations> MainLobbbbbb。

   >[!NOTE]
   >必須將接管渠道的優先順序設定為最高。

   ![asset](assets/p_usecase8.png)Now, **TakeOver頻道將於下午2:00接管** MainAdChannel **** ，持續2小時，直到每週三下午4:00，並播放其內容，從2020年1月9日到2020年1月31日。

### 範例運算式 {#example-expressions}

下表摘要了一些示例表達式，您可以在將渠道分配給顯示時將其添加到調度中。

| **運算式** | **解釋** |
|---|---|
| 早上8:00之前 | 頻道每天早上8點之前播放 |
| 下午2點多 | 頻道每天下午2點後播放 |
| 12:15後和12:45前 | 該頻道每天下午12:15後播放30分鐘 |
| 12:15之前，12:45之後 | 頻道每天在下午12:15之前播放，然後在下午12:45之後播放 |
| 1月1日下午2點多，也是1月2日，也是1月3日凌晨3點多 | 頻道從一月一號下午十二點四十五分開始播放，一月二號一天持續播放到一月三號凌晨三點 |
| 1月1-2日下午2:00後，也是1月2-3日凌晨3:00前 | 頻道播放器於1月1日下午12:45後開始播放，持續播放至1月2日凌晨3:00，然後於1月2日下午12:45再次播放，直到1月3日凌晨3:00 |

>[!NOTE]
>您也可以使 _用軍事時間_ （即14:00）來取代 *am/pm* （即2:00 pm）。

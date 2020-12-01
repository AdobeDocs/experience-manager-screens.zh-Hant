---
title: Perpetual TakeOver Channel
seo-title: Perpetual TakeOver Channel
description: 請依照此使用案例來建立永久TakeOver頻道。
seo-description: 請依照本使用案例，設定專案，以建立持續播放特定時間日與時間的永久接管頻道。
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 1%

---


# 永久接管通道{#perpetual-takeover-channel}

下頁展示了一個使用案例，重點說明如何設定專案，以建立持續播放特定時間日與時間的永久TakeOver頻道。

## 使用案例說明{#use-case-description}

此使用案例說明如何建立&#x200B;*從正常播放的頻道接管*的頻道，以用於顯示或顯示群組。 接管將持續在特定日期和時間內進行。
例如，有一個永久TakeOver頻道，每週五從上午9點到上午10點播放。 在此期間，不應播放其他頻道。 以下範例展示建立永久接管頻道的方式，讓內容每週三從下午2:00至4:00播放2小時。

### 先決條件{#preconditions}

開始此使用案例之前，請務必瞭解如何：

* **[建立和管理渠道](managing-channels.md)**
* **[建立和管理位置](managing-locations.md)**
* **[建立和管理計畫](managing-schedules.md)**
* **[裝置註冊](device-registration.md)**

### 主要操作者{#primary-actors}

內容作者

## 設定項目{#setting-up-the-project}

請依照下列步驟設定專案：

**設定頻道和顯示**

1. 建立標題為&#x200B;**PerpetualTakeOver**&#x200B;的AEM Screens專案，如下所示。

   ![資產](assets/p_usecase1.png)

1. 在&#x200B;**Channels**&#x200B;資料夾中建立&#x200B;**MainAdChannel**。

   ![資產](assets/p_usecase2.png)

1. 選擇&#x200B;**MainAdChannel**，然後從操作欄中按一下&#x200B;**編輯**。 將部分資產（影像、視訊、內嵌序列）拖放至您的頻道。

   ![資產](assets/p_usecase3.png)


   >[!NOTE]
   >此範例中的&#x200B;**MainAdChannel**&#x200B;示範連續播放內容的序列頻道。

1. 建立&#x200B;**TakeOver**&#x200B;頻道，接管&#x200B;**MainAdChannel**&#x200B;中的內容，並將於每週三的下午2:00至4:00播放。

1. 選擇&#x200B;**TakeOver**，然後從操作欄中按一下&#x200B;**Edit**。 將一些資產拖放至您的渠道。 下列範例將展示新增至此頻道的單一區域影像。

   ![資產](assets/p_usecase4.png)

1. 設定頻道的位置和顯示。 例如，為此項目設定了以下位置&#x200B;**MainLobby**&#x200B;和顯示&#x200B;**MainLobbyDisplay**。

   ![資產](assets/p_usecase5.png)

**將頻道指派給顯示**

1. 從&#x200B;**Locations**&#x200B;資料夾選擇顯示&#x200B;**MainLobbyDisplay**。 按一下操作欄上的「分配通道」，開啟「通道分配」對話框。********

   >[!NOTE]
   >要瞭解如何為顯示器分配通道，請參閱&#x200B;**[通道分配](channel-assignment.md)**。

1. 從「渠道分配」對話框填入欄位（**渠道路徑**、**優先順序**&#x200B;和&#x200B;**支援的事件**），然後按一下&#x200B;**保存**&#x200B;分配&#x200B;**主要AdChannel**。****

   * **渠道路徑**:選擇MainAdChannel頻道的路 **** 徑
   * **優先順序**:將此渠道的優先順序設定為1。
   * **支援的事件**:選取「初始 **載入** 和閒置 **畫面」**。

   ![資產](assets/p_usecase6.png)

1. 從&#x200B;**Locations**&#x200B;資料夾選擇顯示&#x200B;**TakeOver**。 按一下操作欄中的&#x200B;**Assign Channel** ，以指定接管通道。

1. 要在計畫時間將&#x200B;**TakeOver**&#x200B;頻道指派給您的顯示器，並從&#x200B;**頻道指派**&#x200B;對話方塊填入下列欄位，然後按一下&#x200B;**儲存**:

   * **渠道路徑**:選取TakeOverchannel的路 **** 徑
   * **優先順序**:將此頻道的優先順序設定為大於 **MainAdChannel**。例如，此範例中的優先順序設定為8。
   * **支援的事件**:選擇「 **Idle** Screen and  **Timer」（空閒螢幕和計時器）**。
   * **排程**:輸入您希望此渠道執行顯示的排程文字。此範例中提及的&#x200B;**Schedule**&#x200B;文字為14:00後的星期三和16:00 *前的星期三。*

      >[!NOTE]
      >要瞭解有關可添加到&#x200B;**Schedule**&#x200B;中的表達式的更多資訊，請參閱下面的[示例表達式](#example-expressions)部分。
   * **活動自**:開始日期和時間。
   * **活動到**:結束日期和時間。

      例如，**Schedule**&#x200B;和&#x200B;**中從**&#x200B;和&#x200B;**活動到**&#x200B;日期和時間的文字允許內容在每週三從2:00 pm到4:00 pm之間播放。


      ![資產](assets/p_usecase7.png)

      從&#x200B;**TakeOver** —> **位置** —> **MainLobby** —> **MainLobbyDisplay**&#x200B;導覽至顯示屏，然後從操作欄按一下&#x200B;**Dashboard**&#x200B;以優先順序查看已分配的頻道如下所示。

      >[!NOTE]
      >必須將接管渠道的優先順序設定為最高。

      ![資產](assets/p_usecase8.png)
AssetNow,  **** TakeOverchannel將於下午2:00接管 **** MainAdChannel，持續兩小時，直到每週三下午4:00，並播放其內容，從2020年1月9日到2020年1月31日。

## 運算式範例{#example-expressions}

下表摘要了一些示例表達式，您可以在將渠道分配給顯示時將其添加到調度中。

| **運算式** | **解釋** |
|---|---|
| 早上8:00之前 | 頻道每天早上8點之前播放 |
| 下午2點多 | 頻道每天下午2點後播放 |
| 12:15後和12:45前 | 該頻道每天下午12:15後播放30分鐘 |
| 12:15之前，12:45之後 | 頻道每天在下午12:15之前播放，然後在下午12:45之後播放 |
| 1月1日下午2點多，也是1月2日，也是1月3日凌晨3點多 | 頻道從一月一號下午兩點開始播放，一月二號一天持續播放，直到一月三號凌晨三點 |
| 1月1-2日下午2:00後，也是1月2-3日凌晨3:00前 | 頻道播放器於1月1日下午2點後開始播放，持續播放至1月2日凌晨3點，然後於1月2日下午2點再次播放，直到1月3日凌晨3點為止 |

>[!NOTE]
>
>您也可以使用&#x200B;_軍事時間_&#x200B;符號（即14:00），而非&#x200B;*am/pm*&#x200B;符號（即2:00 pm）。

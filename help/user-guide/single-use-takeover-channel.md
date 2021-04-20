---
title: 單次使用TakeOver通道
seo-title: 單次使用TakeOver通道
description: 請依照此使用案例來建立單一使用TakeOver頻道。
seo-description: 請依照此使用案例來建立單一使用TakeOver頻道。
contentOwner: jsyal
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 1%

---


# 單次使用TakeOver Channel {#single-use-takeover-channel}

下頁展示了一個使用案例，重點說明如何設定專案，以建立在特定時間內只播放一次的Single TakeOver頻道。


## 使用案例說明{#use-case-description}

此使用案例說明如何建立&#x200B;*從正常播放的頻道接管*的頻道，以用於顯示或顯示群組。 接管僅在特定時間內發生一次。
例如，有一個Single TakeOver頻道會在星期五上午9點到上午10點播放。 在此期間，不應播放其他頻道。 在此之前和之後，「單次使用接管」渠道將不會播放。 以下範例展示建立單一接管渠道的功能，讓內容在12月31日12:00 am到12:01 am之前播放2分鐘。

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

1. 建立標題為&#x200B;**SingleUseTakeOver**&#x200B;的AEM Screens專案，如下所示。

   ![資產](assets/single-takeover1.png)

1. 在&#x200B;**Channels**&#x200B;資料夾中建立&#x200B;**MainAdChannel**。

   ![資產](assets/single-takeover2.png)

1. 選擇&#x200B;**MainAdChannel**，然後從操作欄中按一下&#x200B;**編輯**。 將部分資產（影像、視訊、內嵌序列）拖放至您的頻道。

   ![資產](assets/single-takeover2.png)


   >[!NOTE]
   >此範例中的&#x200B;**MainAdChannel**&#x200B;示範連續播放內容的序列頻道。

   ![資產](assets/single-takeover3.png)

1. 建立&#x200B;**TakeOver**&#x200B;頻道，以接管&#x200B;**MainAdChannel**&#x200B;中的內容，且僅會在特定日期和時間播放。

1. 選擇&#x200B;**TakeOver**，然後從操作欄中按一下&#x200B;**Edit**。 將一些資產拖放至您的渠道。 下列範例將展示新增至此頻道的單一區域影像。

   ![資產](assets/single-takeover4.png)

1. 設定頻道的位置和顯示。 例如，為此項目設定了以下位置&#x200B;**Lobby**&#x200B;和顯示&#x200B;**MainLobbyDisplay**。

   ![資產](assets/single-takeover5.png)

**將頻道指派給顯示**

1. 從&#x200B;**Locations**&#x200B;資料夾選擇顯示&#x200B;**MainLobbyDisplay**。 從操作欄按一下「分配通道」。****

   ![資產](assets/single-takeover6.png)

   >[!NOTE]
   >要瞭解如何為顯示器分配通道，請參閱&#x200B;**[通道分配](channel-assignment.md)**。

1. 從「渠道分配」對話框填入欄位（**渠道路徑**、**優先順序**&#x200B;和&#x200B;**支援的事件**），然後按一下&#x200B;**保存**。 ****&#x200B;您現在已將&#x200B;**MainAdChannel**&#x200B;指派給您的顯示器。

   ![資產](assets/single-takeover7.png)

1. 從&#x200B;**Locations**&#x200B;資料夾選擇顯示&#x200B;**TakeOver**。 按一下操作欄中的&#x200B;**Assign Channel** ，以指定單一使用接管渠道。

1. 要在計畫時間將&#x200B;**TakeOver**&#x200B;頻道指派給您的顯示器，並從&#x200B;**頻道指派**&#x200B;對話方塊填入下列欄位，然後按一下&#x200B;**儲存**:

   * **渠道路徑**:選取TakeOver頻道的路徑
   * **優先順序**:將此頻道的優先順序設定為大於 **MainAdChannel**。例如，此範例中的優先順序設定為8。

      >[!NOTE]
      >優先順序可以是高於正常播放頻道的優先順序值的任何值。
   * **支援的事件**:選擇「 **Idle** Screen and  **Timer」（空閒螢幕和計時器）**。
   * **排程**:輸入您希望此渠道執行顯示的排程文字。例如，此處的文字可讓內容在12月31日12:00 am之前播放2分鐘，直到12:01 am。
本例中提及的**Schedule**&#x200B;中的文字是&#x200B;*，是12月23日之後的31天，也是1月1日00.01*&#x200B;之前的一天。

      ![資產](assets/single-takeover8.png)

      從&#x200B;**SingleUseTakeOver** —> **Locations** —> **Lobby** —> **MainLobbyDisplay**&#x200B;導覽列導覽至顯示器，以檢視指派的頻道優先順序，如下所示。****

      >[!NOTE]
      >必須將接管渠道的優先順序設定為最高。

      ![資產](assets/single-takeover9.png)

>[!NOTE]
>
>在播放「單次使用TakeOver」頻道後，最佳做法是加以刪除。
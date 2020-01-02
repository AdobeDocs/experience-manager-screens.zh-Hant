---
title: 單次使用TakeOver通道
seo-title: 單次使用TakeOver通道
description: 請依照此使用案例來建立單一使用TakeOver頻道。
seo-description: 請依照此使用案例來建立單一使用TakeOver頻道。
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 58229f2ecbc098522d5d62972ba7f9362a538997

---


# 單次使用TakeOver通道 {#single-use-takeover-channel}

下頁說明了一個使用案例，重點說明如何設定專案，以建立只播放一次的接管渠道。

供審核。

## 使用案例說明 {#use-case-description}

此使用案例說明如何為顯示器 *或顯示器* 群組建立從正常播放的頻道接管的頻道。 接管僅在特定時間內發生一次。
例如，有一個Single TakeOver頻道會在星期五上午9點到上午10點播放。 在此期間，不應播放其他頻道。 在此之前和之後，「單次使用接管」渠道將不會播放。 以下範例展示建立單一接管渠道的功能，讓內容在12月31日12:00 am到12:01 am之前播放2分鐘。

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

1. 建立標題為 **TakeoverLoop的AEM Screens專案**，如下所示。

   ![資產](assets/single-takeover1.png)

1. 在「頻 **道」檔案夾中** ，建立 **MainAdChannel** 。

   ![資產](assets/single-takeover2.png)

1. 選取 **MainAdChannel** ，然後從動 **作列按一下「編輯** 」。 將部分資產（影像、視訊、內嵌序列）拖放至您的頻道。

   ![資產](assets/single-takeover2.png)

   >[!Note]
   > 此范 **例中的MainAdChannel** ，會示範連續播放內容的序列頻道。

   ![資產](assets/single-takeover3.png)

1. 建立 **TakeOver** 頻道，以接管 **MainAdChannel中的內容** ，且只會在特定日期和時間播放。

1. 選擇「 **TakeOver** 」，然後從操 **作欄中按一下「Edit** 」（編輯）。 將一些資產拖放至您的渠道。 下列範例將展示新增至此頻道的單一區域影像。

   ![資產](assets/single-takeover4.png)

1. 設定頻道的位置和顯示。 例如，會為此專案設 **定下列位置** 「Lobby」（大堂）和 **display mainLobby** Display。

   ![資產](assets/single-takeover5.png)

**將頻道指派給顯示**

1. 從「位置」 **資料夾中選取顯** 示MainLobbyDisplay **** (MainLobbyDisplay)。 從動 **作列按一下** 「指定渠道」。

   ![資產](assets/single-takeover6.png)

   >[!NOTE]
   >若要瞭解如何指派頻道至顯示器，請參閱頻道 **[指派](channel-assignment.md)**。

1. 從Channel AssignmentSave和&#x200B;**ClickChannel Assignment框中填入欄位(Channel Path**、Priority **和** Supported Events ************)，即Channel Assignment和ClickChinkSave對話框。 現在，您已將 **MainAdChannel指派給您** 的顯示畫面。

   ![資產](assets/single-takeover7.png)

1. 從「位置」 **資料夾中** ，選 **取顯示TakeOver** 。 從動 **作列按一下「指定渠道** 」，以指定單一使用接管渠道。

1. 若要在排 **程時將TakeOver** 頻道指派給您的顯示，並從「頻道指派」對話方塊填入下列欄位，然後按一下「儲 **存******」:

   * **渠道路徑**:選取TakeOver頻道的路徑
   * **優先順序**:將此頻道的優先順序設定為大於 **MainAdChannel**。 例如，此範例中的優先順序設定為8。
   * **支援的事件**:選擇「 **Idle Screen** (空閒屏 **幕)」和「Timer（計時器）**」。
   * **排程**:輸入您希望此渠道執行顯示的排程文字。 例如，此處的文字可讓內容在12月31日12:00 am之前播放2分鐘，直到12:01 am。
本例中提 **及的** 「排程」中的文字是 *12月31日之後的23:58，也是1月1日之後的00.01*。

      ![資產](assets/single-takeover8.png)

      >[!NOTE]
      >您可以提及不同使用案例的排程。 如需詳細資訊，請參閱永久使用案例。
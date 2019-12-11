---
title: 緊急通道
seo-title: 緊急通道
description: 請依照此使用案例範例，瞭解如何建立和管理緊急頻道，內容作者可在有前提的情況下從順序頻道切換。
seo-description: 請依照此使用案例範例，瞭解如何建立和管理緊急頻道，內容作者可在有前提的情況下從順序頻道切換。
uuid: 612917c9-a832-453b-970c-f4365f7b105d
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: dbb4fae6-f3fb-496a-9bd6-1151e2862b5b
docset: aem65
translation-type: tm+mt
source-git-commit: 2708464222321fd138c986f19d8572c71f1dae75

---


# 緊急通道 {#emergency-channel}

## 使用案例說明 {#use-case-description}

本節說明一個使用案例範例，其重點在於建立和管理緊急頻道，內容作者可在有先決條件的情況下從序列頻道切換該緊急頻道。

### 先決條件 {#preconditions}

開始此使用案例之前，請務必瞭解如何：

* **[建立和管理渠道](managing-channels.md)**
* **[建立和管理位置](managing-locations.md)**
* **[建立和管理計畫](managing-schedules.md)**
* **[裝置註冊](device-registration.md)**

### 主要操作者 {#primary-actors}

內容作者

## 基本流：設定專案 {#basic-flow-setting-up-the-project}

請依照下列步驟設定緊急通道：

1. 建立名為 **EmergencyChannel的AEM Screens專案**，如下所示。

   >[!NOTE]
   >
   >若要進一步瞭解如何在AEM畫面中建立和管理專案，請參閱「建立專案」。

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **建立序列渠道**

   1. 選取「 **Channels** 」檔案夾，然後按 **一下「建立** 」以開啟精靈以建立渠道。

   1. 從精 **靈中選取「順序渠道** 」，並建立標題為「 **MainAdChannel**」的渠道。
   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **新增內容至序列頻道**

   1. 選取渠道(**MainAdChannel**)。
   1. 從動 **作列按一下** 「編輯」以開啟編輯器。 將幾個資產拖放至您的渠道。
   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **建立緊急通道**

   1. 選取「頻 **道** 」檔案夾。
   1. 按一下「 **建立** 」以開啟精靈以建立渠道。
   1. 從向 **導中選擇Sequence Channel** ，然後建立名為 **EmergencyChannel的渠道**。
   >[!NOTE]
   >
   >通常，您的緊急通道會新增至您預先存在的生產專案。

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **新增內容至緊急通道**

   1. 選擇頻道(緊&#x200B;**急頻道)**。
   1. 從動 **作列按一下** 「編輯」以開啟編輯器。 將您要在緊急狀況期間執行的資產拖放至您的渠道。
   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **建立位置**

   1. 導覽至「位 **置** 」檔案夾。
   1. 按一 **下** 「從動作列建立」，並從精靈中建立名為「 **Store** 」的位置。
   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **在您的位置中建立顯示**

   導覽至您的位置(**商店**)，然後按一 **下動作列中的「建立** 」。 按照嚮導建立兩個標 **題為****StoreFront** 和 **StoreRear的顯示**。

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **建立排程**

   1. 導覽至您的「 **排程** 」檔案夾。
   1. 從動 **作列按一下** 「建立」。 請依照精靈建立名為 **StoreSchedule的排程**。
   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. 將「顯示」指派給您的排程並設定優先順序

   1. 選取排程( **StoreSchedule)** ，然後從動作列按 **一下「儀表板** 」。

   1. 從「已 **指派的頻道** 」面板按 **一下「+指派頻道** 」。

   1. 從「渠 **道分配** 」對話框：

      1. 選取MainAdChannel的路 **徑**
      1. 將優先 **順序** 設為2
      1. 將「支援的事件」設 **為「初始載** 入 **和空閒畫面**」。
      1. Click **Save**
      同樣地，您也必須再次執行相同的步驟，才能指派 **EmergencyChannel** 並設定 **優先順序**。
   >[!NOTE]
   >
   >優先順序用於在多個分配匹配播放條件時對分配進行排序。 值最高的一律優先於值較低的值。

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. 從「已 **指派的頻道** 」面板按 **一下「+指派頻道** 」。

1. 從「渠 **道分配** 」對話框：

   1. 選擇EmergencyChannel的路 **徑**
   1. 將優先 **順序** 設為1

   1. 將「支援的事件」設 **為「初始載入**」、「 **閒置畫面**」和「 **使用者互動」**

   1. Click **Save**
   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   您可從「商店排程」控制面板檢 **視指派的渠道** 。

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **將排程指派給每個顯示**

   1. 導覽至每個顯示器，例如 **Channel** —&gt; **Locations** —&gt; **Store** —&gt;**** StoreFront緊急處理。

   1. 從動 **作按一下** 「控制面板」，以開啟顯示控制面板。
   1. **按一**&#x200B;下……從「指 **派渠道與排程」面板** ，然後按一 **下+指派排程**。

   1. 選擇「計畫」的路徑(例如，此處 **EmergencyChannel** —&gt; **Schedules** —&gt;**StoreSchedule**)。

   1. 按一下&#x200B;**「儲存」**。
   您可以從「商店排程」控制面板檢視指派給顯示 **畫面的排程** 。
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **裝置註冊**

   完成裝置註冊程式，在您註冊後，就會在AEM Screens播放器上檢視下列輸出。

   ![new30](assets/new30.gif)

## 切換到緊急通道 {#switching-to-emergency-channel}

發生緊急情況時，請執行以下步驟：

1. 導航至 **EmergencyChannel** **Schedules** —&gt; **StoreSchedule** ，然後從操作欄 **** 中選擇DashboardSchedule。

   ![screen_shot_2019-02-25at10112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. 從「商店 **排程」控制面板選** 取「EmergencyChannel **」，然後按一下「** 編輯指派 ****」。

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. 將EmergencyChannel的 **優先順序** 從Channel Assignment Dialog **and** click Channel SaveChannel更新為3 ************。

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. 當頻道的優先順序更新後，所有AEM Screens播放器都會顯示 **EmergencyChannel** ，如下所示。

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### 結論 {#conclusion}

EmergencyChannel **** 將繼續顯示其內容，直到內容作者將「優先順序值」重設為1為止。

內容作者收到緊急狀況已清除的指示後，應更新 **MainAdChannel** ，以恢復正常播放。

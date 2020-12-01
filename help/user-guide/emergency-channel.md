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
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 0%

---


# 緊急通道{#emergency-channel}

## 使用案例說明{#use-case-description}

本節說明一個使用案例範例，其重點在於建立和管理緊急頻道，內容作者可在有先決條件的情況下從序列頻道切換該緊急頻道。

### 先決條件{#preconditions}

開始此使用案例之前，請務必瞭解如何：

* **[建立和管理渠道](managing-channels.md)**
* **[建立和管理位置](managing-locations.md)**
* **[建立和管理計畫](managing-schedules.md)**
* **[裝置註冊](device-registration.md)**

### 主要操作者{#primary-actors}

內容作者

## 基本流：設定項目{#basic-flow-setting-up-the-project}

請依照下列步驟設定緊急通道：

1. 建立名為&#x200B;**EmergencyChannel**&#x200B;的AEM Screens專案，如下所示。

   >[!NOTE]
   >若要進一步瞭解如何在AEM畫面中建立和管理專案，請參閱「建立專案」。

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **建立序列渠道**

   1. 選擇&#x200B;**頻道**&#x200B;資料夾，然後按一下&#x200B;**建立**&#x200B;以開啟精靈以建立頻道。

   1. 從嚮導中選擇「序列通道」，並建立名為「**MainAdChannel」的通道。******

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **新增內容至序列頻道**

   1. 選擇頻道(**MainAdChannel**)。
   1. 按一下操作欄中的&#x200B;**編輯**&#x200B;以開啟編輯器。 將幾個資產拖放至您的渠道。

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **建立緊急通道**

   1. 選擇&#x200B;**Channels**&#x200B;資料夾。
   1. 按一下&#x200B;**建立**&#x200B;以開啟嚮導以建立通道。
   1. 從嚮導中選擇「序列通道」，並建立名為「**EmergencyChannel」的通道。******

   >[!NOTE]
   >
   >通常，您的緊急通道會新增至您預先存在的生產專案。

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **新增內容至緊急通道**

   1. 選擇通道（**緊急通道）**。
   1. 按一下操作欄中的&#x200B;**編輯**&#x200B;以開啟編輯器。 將您要在緊急狀況期間執行的資產拖放至您的渠道。

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **建立位置**

   1. 導覽至&#x200B;**Locations**&#x200B;資料夾。
   1. 從動作列按一下「建立」，並從精靈建立名為「儲存」的&#x200B;**位置。******

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **在您的位置中建立顯示**

   導覽至您的位置(**Store**)，然後從動作列按一下「建立&#x200B;**a3/>」。**&#x200B;按照嚮導建立兩個&#x200B;**Displays**，標題為&#x200B;**StoreFront**&#x200B;和&#x200B;**StoreRear**。

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **建立排程**

   1. 導航至&#x200B;**Schedules**&#x200B;資料夾。
   1. 從操作欄按一下&#x200B;**建立**。 按照嚮導建立名為&#x200B;**StoreSchedule**&#x200B;的計畫。

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. 將「顯示」指派給您的排程並設定優先順序

   1. 選擇計畫&#x200B;**(StoreSchedule)**，然後從操作欄中按一下&#x200B;**儀表板**。

   1. 從&#x200B;**ASSIGNED CHANNELS**&#x200B;面板按一下&#x200B;**+ 「指定通道」。**

   1. 在&#x200B;**Channel Assignment**&#x200B;對話框中：

      1. 選擇&#x200B;**MainAdChannel**&#x200B;的路徑
      1. 將&#x200B;**Priority**&#x200B;設為2
      1. 將「支援的事件」設定為「初始負載&#x200B;**」和「空閒螢幕**」。****
      1. 按一下&#x200B;**保存**

      同樣地，您也必須再次執行相同的步驟，以指派&#x200B;**EmergencyChannel**&#x200B;並設定其&#x200B;**Priority**。
   >[!NOTE]
   >
   >優先順序用於在多個分配匹配播放條件時對分配進行排序。 值最高的一律優先於值較低的值。

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. 從&#x200B;**ASSIGNED CHANNELS**&#x200B;面板按一下&#x200B;**+ 「指定通道」。**

1. 在&#x200B;**Channel Assignment**&#x200B;對話框中：

   1. 選擇&#x200B;**EmergencyChannel**&#x200B;的路徑
   1. 將&#x200B;**Priority**&#x200B;設為1

   1. 將「支援的事件」設定為「初始負載&#x200B;**」、「空閒螢幕**」和「用戶交互&#x200B;**」******

   1. 按一下&#x200B;**保存**

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   您可以從&#x200B;**StoreSchedule**&#x200B;控制面板檢視指派的頻道。

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **將排程指派給每個顯示**

   1. 導覽至每個顯示器，例如&#x200B;**EmergencyChannel** —> **Locations** —> **Store** —>**StoreFront**。

   1. 按一下動作中的&#x200B;**儀表板**&#x200B;以開啟顯示控制面板。
   1. 按一下&#x200B;**...** ASSIGNED CHANNELS &amp; SCHEDULES **面板中的**，然後按一下&#x200B;**+Assign Schedule**。

   1. 選擇到「計畫」的路徑（例如，此處&#x200B;**EmergencyChannel** —> **Schedules** —>**StoreSchedule**）。

   1. 按一下&#x200B;**「儲存」**。

   您可以從&#x200B;**StoreSchedule**控制面板檢視指派給顯示的排程。
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **裝置註冊**

   完成裝置註冊程式，在您註冊後，就會在AEM Screens播放器上檢視下列輸出。

   ![new30](assets/new30.gif)

## 切換到緊急通道{#switching-to-emergency-channel}

發生緊急情況時，請執行以下步驟：

1. 導覽至&#x200B;**EmergencyChannel** —> **Schedules** —> **StoreSchedule**&#x200B;並從操作欄選擇&#x200B;**Dashboard**。

   ![screen_shot_2019-02-25at10112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. 從&#x200B;**StoreSchedule**&#x200B;儀表板選擇&#x200B;**EmergencyChannel** ，然後按一下&#x200B;**Edit Assignment**。

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. 將&#x200B;**EmergencyChannel**&#x200B;的&#x200B;**Priority**&#x200B;從&#x200B;**Channel Assignment**&#x200B;對話方塊更新為&#x200B;**3**，然後按一下&#x200B;**Save**。

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. 一旦頻道的優先順序更新，所有AEM Screens播放器都會顯示&#x200B;**EmergencyChannel**&#x200B;內容，如下所示。

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### 結論{#conclusion}

**EmergencyChannel**&#x200B;將繼續顯示其內容，直到內容作者將優先順序值重設為1。

內容作者收到緊急狀況已清除的指示後，應更新&#x200B;**MainAdChannel**&#x200B;的優先順序，以恢復正常播放。

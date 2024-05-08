---
title: 緊急通道
description: 瞭解如何建立和管理緊急頻道，內容作者可以在有先決條件時從順序頻道切換緊急頻道。
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d409ba46-b48a-44db-b305-27c392cd55de
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 0%

---

# 緊急通道 {#emergency-channel}

## 使用案例說明 {#use-case-description}

本節說明使用案例範例，著重於建立和管理緊急通道，如果存在先決條件，內容作者可從順序通道切換。

### 先決條件 {#preconditions}

開始此使用案例前，請確定您瞭解如何：

* **[建立和管理頻道](managing-channels.md)**
* **[建立和管理位置](managing-locations.md)**
* **[建立和管理時程表](managing-schedules.md)**
* **[裝置註冊](device-registration.md)**

### 主要執行者 {#primary-actors}

內容作者

## 基本流程：設定專案 {#basic-flow-setting-up-the-project}

請依照下列步驟設定緊急通道：

1. 建立名為的AEM Screens專案 **緊急通道**，如下所示。

   >[!NOTE]
   >若要進一步瞭解如何在AEM Screens中建立和管理專案，請參閱建立專案。

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **建立順序頻道**

   1. 按一下 **頻道** 資料夾並按一下 **建立**.

   1. 按一下 **順序頻道** 並從精靈建立標題為 **MainAdChannel**.

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **新增內容至順序頻道**

   1. 按一下通道(**MainAdChannel**)。
   1. 按一下 **編輯** 從動作列移除。
   1. 將一些資產拖放至您的頻道。

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **建立緊急通道**

   1. 按一下 **頻道** 資料夾。
   1. 按一下&#x200B;**建立**。
   1. 按一下 **順序頻道** 並從精靈建立標題為 **緊急通道**.

   >[!NOTE]
   >
   >一般而言，您的緊急通道會新增至您既有的生產專案。

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **新增內容至緊急通道**

   1. 按一下通道(**緊急通道)**.
   1. 按一下 **編輯** 從動作列移除。
   1. 將您要在緊急情況下執行的資產拖放到您的頻道。

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **建立位置**

   1. 瀏覽至 **位置** 資料夾。
   1. 按一下 **建立** 並從動作列建立標題為的位置 **儲存** 從精靈中。

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **在您的位置中建立顯示區**

   導覽至您的位置(**儲存**)並按一下 **建立** 從動作列移除。 依照精靈建立兩個 **顯示區** 標題為 **StoreFront** 和 **StoreRear**.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **建立排程**

   1. 導覽至 **時程表** 資料夾。
   1. 按一下 **建立** 從動作列移除。
   1. 依照精靈，建立標題為的排程 **StoreSchedule**.

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. 將兩個顯示指定給排程並設定優先順序

   1. 按一下排程 **（存放區排程）** 並按一下 **儀表板** 從動作列移除。

   1. 按一下 **+指派管道** 從 **已指派的管道** 面板。

   1. 從 **頻道指定任務** 對話方塊：

      1. 按一下 **MainAdChannel**
      1. 設定 **優先順序** as 2
      1. 將支援的事件設為 **初始載入** 和 **閒置畫面**.
      1. 按一下 **儲存**

      同樣地，請再次遵循相同的步驟來指派 **緊急通道** 並設定其 **優先順序**.

   >[!NOTE]
   >
   >當有多個指派符合播放條件時，優先順序可用於排序指派。 值最高的總是優先於較低的值。

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. 按一下 **+指派管道** 從 **已指派的管道** 面板。

1. 從 **頻道指定任務** 對話方塊：

   1. 按一下 **緊急通道**
   1. 設定 **優先順序** as 1

   1. 將支援的事件設為 **初始載入**， **閒置畫面**、和 **使用者互動**

   1. 按一下 **儲存**

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   您可從「 」檢視指派的色版 **StoreSchedule** 儀表板。

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **指派排程給每個顯示器**

   1. 導覽至每個顯示畫面，例如 **緊急通道** > **位置** > **儲存** >**StoreFront**.

   1. 按一下 **儀表板** 從動作列移除。
   1. 按一下 **...** 從 **已指派的頻道與排程** 面板，然後按一下 **+指派排程**.

   1. 按一下排程的路徑(例如， **緊急通道** > **時程表** >**StoreSchedule**)。

   1. 按一下「**儲存**」。

   您可以從以下位置檢視指派給顯示的排程： **StoreSchedule** 儀表板。
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **裝置註冊**

   完成裝置註冊程式。 註冊後，您可以在AEM Screens Player上檢視以下輸出。

   ![new30](assets/new30.gif)

## 切換到緊急頻道 {#switching-to-emergency-channel}

如果發生緊急狀況，請執行下列步驟：

1. 瀏覽至 **緊急通道** > **時程表** > **StoreSchedule** 並按一下 **儀表板** 從動作列移除。

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. 按一下 **緊急通道** 從 **StoreSchedule** 儀表板並按一下 **編輯指派**.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. 更新 **優先順序** 的 **緊急通道** 至 **3** 從 **頻道指定任務** 對話方塊並按一下 **儲存**.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. 當管道的優先順序更新時，所有AEM Screens Player都會顯示 **緊急通道** 內容。

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### 結論 {#conclusion}

此 **緊急通道** 會持續顯示其內容，直到內容作者將優先順序值重設為1為止。

當內容作者收到緊急狀況已清除的指示時，他們應更新的 **MainAdChannel** 這會使正常播放繼續。

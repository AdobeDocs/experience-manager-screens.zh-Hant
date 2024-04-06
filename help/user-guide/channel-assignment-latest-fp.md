---
title: 頻道指定任務 — 最新FP
seo-title: Channel Assignment - Latest FP
description: 請依照本頁所述來瞭解「頻道指定任務」和「日時段分割」。
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '1476'
ht-degree: 2%

---

# 頻道指定任務 {#channel-assignment}

>[!IMPORTANT]
>
>本節重點說明AEM 6.5.5 Screens Feature Pack及更新版本的頻道指定與頻道排程。

設定顯示後，您必須將頻道指派給顯示以檢視您的內容。

此頁面顯示指派管道給您的顯示器、瞭解管道屬性和DayParting。

>[!NOTE]
>
>您可以將多個色版指派給顯示器。


## 指派管道 {#assign-a-channel-new-release}

請依照下列章節建立AEM Screens專案，並將頻道指派給顯示區。

### 建立AEM Screens專案和管道 {#creating-project}

請依照下列步驟設定專案和管道：

1. 建立標題為的AEM Screens專案 **DemoScreens**.

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >請參閱 [建立和管理專案](creating-a-screens-project.md) 以瞭解如何建立AEM Screens專案。

1. 建立標題為的順序頻道 **自助餐廳** 在 **頻道** 資料夾。

1. 選取管道並按一下 **編輯** 以新增內容至您的頻道。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   例如， **自助餐廳** 色版現在會顯示下列影像：

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. 建立標題為的位置 **SanJose** 和顯示為 **大廳**.

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### 將頻道指派到顯示器 {#assigning-channel-to-display}

專案設定完成後，您必須將頻道指派給顯示以檢視內容。

1. 導覽至所需的顯示畫面，例如， **DemoScreens** > **位置** > **SanJose** > **大廳**.

1. 點選/按一下 **指派頻道** 從動作列移除。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   或，

   點選/按一下 **儀表板** ，然後按一下 **+指派頻道** 從 **已指派的頻道與排程** 面板。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. 此 **頻道指定任務** 對話方塊開啟。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. 從 **設定** 選項，您可以選擇通道 **依路徑** 或 **依名稱**，輸入 **頻道角色**， **優先順序**， **支援的事件**、和 **中斷方法**. 此外，您也可以從此對話方塊啟用有趣的工具提示。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >請參閱 [頻道屬性](#channel-properties) 區段，以進一步瞭解管道指派屬性。

1. 從 **排程** 選項選取 **啟用期間** 和 **遞回排程**.
   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >請參閱 [頻道屬性](#channel-properties) 區段，以進一步瞭解管道指派屬性。

1. 按一下 **儲存** 設定您的偏好設定後。

### 在Chrome播放器中檢視內容 {#viewing-content-output}

此範例會在Chrome播放器上展示輸出。 將頻道指派給顯示區後，您必須將裝置註冊給播放器。

請參閱 [裝置註冊](device-registration.md) 以瞭解如何在AEM Screens播放器上註冊裝置。

您將在選擇的播放器上檢視下列輸出：

![new1](assets/channel-assignment/channel-assign-output.gif)

## 時間表檢視 {#timeline-view}

將管道指派給顯示並設定遞回排程表後，您就可以從 **已指派的頻道與排程** 面板。

請依照下列步驟導覽至時間表檢視：

1. 導覽至所需的顯示畫面，例如， **DemoScreens** > **位置** > **SanJose** > **大廳**.

1. 點選/按一下 **指派頻道** 從動作列移除。

   或，

   點選/按一下 **儀表板** 並按一下 **時間表** 從 **已指派的頻道與排程** 面板。

   ![影像](/help/user-guide/assets/channel-assignment/timeline-1.png)

## 透過頻道指定任務對話方塊瞭解頻道屬性 {#channel-properties}

下列屬性是從 **設定** 中的選項 **頻道指定任務** 對話方塊。

![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### 選取頻道 {#select-channel}

選取管道可讓您依管道名稱或管道路徑，提供所需管道的參考。

* **依路徑**：您可以使用管道的絕對路徑提供明確參照。

* **依名稱**：輸入將依內容解析為實際頻道的頻道名稱。 此功能可讓您建立管道的本機版本，以動態解析特定於位置的內容。 例如，具有名稱的管道 *每日交易*，實際內容在兩個城市中可能有所不同，但您在所有顯示器上仍擁有健全的頻道角色。

### 頻道角色 {#role-channel}

頻道角色定義顯示的內容。 角色是各種動作的鎖定目標，與履行角色的實際管道無關。

### 優先順序 {#priority-channel}

當有多個指派符合播放條件時，優先順序可用於排序指派。 值最高的總是優先於較低的值。 例如，如果有兩個管道A和B。A的優先順序為1，而B的優先順序為2，則會顯示管道B，因為其優先順序高於A。

>[!NOTE]
>
>頻道的優先順序在中設定為數字（最小為1） **頻道指定任務** 對話方塊，如上所述。 此外，指派的管道會根據遞減優先順序排序。

### 支援的事件 {#supported-events-channel}

* **初始載入**：在播放器啟動時載入頻道。 可與排程結合指派給多個管道
* **閒置畫面**：在畫面閒置時載入。 可與排程結合指派給多個管道
* **計時器**：提供排程時需要設定
* **使用者互動**：如果閒置頻道的熒幕上有使用者互動（觸控），播放器會切換至指定的頻道，並在觸控熒幕時載入

### 中斷方法 {#interruption-method-channel}

>[!IMPORTANT]
> 此選項僅適用於AEM 6.4 Feature Pack 8或AEM 6.5 Feature Pack 4。

作為內容作者，您應該能夠指定頻道何時中斷，以便能夠選擇剪下非關鍵內容，但可以選擇讓重要內容完全播放，然後再因排程而剪下播放。

從下列選項中選取，這些選項可用於設定中斷方法： **頻道指定任務** 對話方塊：

* **立即**：每當排程啟動或收到更新時，您可以切斷播放並立即重新整理或播放新內容
* **在目前專案結束時**：當新的排程啟動或收到更新時，您可以選擇等待序列中的目前專案完成播放，之後您才會重新整理或播放新內容

  >[!NOTE]
  >依預設，會選取此選項。

* **在序列結束時**：當新的排程啟動或收到更新時，您可以選擇等待整個序列到達其結尾，然後在所需的序列之前，您回圈回到第一個元素，重新整理或播放新內容

  >[!NOTE]
  >使用第二個或第三個選項可能會導致指派上定義的排程時間稍微延遲，因為播放器會等待專案或序列的結尾（在指定的時間後）再重新整理。 延遲將取決於專案的播放持續時間。

下列屬性是從 **排程** 中的選項 **頻道指定任務** 對話方塊。

![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### 啟用時間 {#activation-window}

「啟動視窗」可讓您選取 **開始日期** 和 **結束日期** 以顯示您的內容。

### 週期排程 {#recurrence-schedule}

週期性排程表可讓您設定內容的週期性排程表。 按一下 **+新增排程** 以新增週期排程至您的頻道。

>[!NOTE]
>您可以將多個週期性排程新增到您的頻道。
>週期時程表引入 *日時段分割*，這可讓您設定在一天中的特定時間執行多個管道的全域排程，並一次重複使用該設定來顯示所有顯示器。

您可以設定下列選項：

* **名稱**：您的遞回排程表的標題。
* **重複**：選擇排程是否執行 **每日**， **每週**， **每月**，或 **每年**.
* **開始**：排程的開始時間。
* **結束**：排程的結束時間。 您可以依時間或持續時間設定時間。
   * **時間**：排程將在指定時間結束。
   * **持續時間**：排程會以小時或分鐘為單位在特定期間內執行。

### 日時段分割 {#dayparting}

DayParting是指將一天分割為時段，並指定在所需時間播放哪些內容。 AEM Screens可讓您視需求，依照「日時段分割」的方式，將管道排程在一天、一週或一個月內。

下列範例說明在三種不同情境下，管道中的DayParting：

#### 在單一日期播放內容，分為多個時段 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

這個範例說明餐廳如何使用DayParting來展示每天的早餐、午餐和晚餐選單。

在此，我們將每天劃分為不同的時段，以便頻道內容能在一天中的指定時間播放。 針對此使用案例設定您頻道的週期性排程的下列屬性，以播放內容。

| **名稱** | **重複** | **啟動** | **結束** |
|---|---|---|---|
| 早餐 | 每日 | 上午6:00 | 上午11:00 |
| 午餐 | 每日 | 上午11:00 | 下午3點 |
| 晚餐 | 每日 | 下午3點 | 下午8:00 |

#### 在一週中的特定日播放內容 {#playing-content-on-a-particular-day-of-the-week}

此範例說明在賭場中實作的DayParting，其中現場活動在每週末從晚上8:00到晚上10:00進行，並且可在晚上10:00到凌晨1:00的晚餐功能表提供特殊優惠

| **名稱** | **重複** | **啟動** | **結束** |
|---|---|---|---|
| 週末 | 每週：星期六、星期日 | 下午8:00 | 下午10:00 |
| 特殊優惠 | 每日：星期一至星期五 | 下午10:00 | 上午1:00 |

>[!NOTE]
>
>此外，您也可以定義 ***優先順序*** 每個色版。 例如，如果為同一天和時間或同一月設定兩個管道，則優先順序較高的管道會先播放。 優先順序的最小值可以設為0。

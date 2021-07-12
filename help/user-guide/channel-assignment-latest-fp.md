---
title: 通道分配 — 最新FP
seo-title: 通道分配 — 最新FP
description: 請詳閱本頁，了解管道指派和DayParting。
feature: 製作螢幕，通道分配
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1475'
ht-degree: 2%

---

# 頻道指定任務 {#channel-assignment}

>[!IMPORTANT]
>
>本節重點說明AEM 6.5.5 Screens Feature Pack及更新版本的頻道指派和排程。

設定顯示器後，您必須指派頻道給顯示器以檢視您的內容。

本頁面顯示如何指派管道給您的顯示器、了解管道屬性，以及DayParting。

>[!NOTE]
>
>您可以指派多個管道給一個顯示器。


## 指派管道 {#assign-a-channel-new-release}

請依照以下各節建立AEM Screens專案，並指派管道給顯示器。

### 建立AEM Screens專案和管道 {#creating-project}

請依照下列步驟來設定專案和管道：

1. 建立標題為&#x200B;**DemoScreens**&#x200B;的AEM Screens專案。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >請參閱[建立和管理專案](creating-a-screens-project.md)以了解如何建立AEM Screens專案。

1. 在&#x200B;**Channels**&#x200B;資料夾中建立名為&#x200B;**Cafetera**&#x200B;的序列通道。

1. 選取頻道，然後按一下動作列中的「**編輯**」 ，將內容新增至您的頻道。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   例如，**自助餐廳**&#x200B;頻道現在會顯示下列影像：

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. 建立標題為&#x200B;**SanJose**&#x200B;的位置，並建立名為&#x200B;**Lobby**&#x200B;的顯示。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### 為顯示指定通道 {#assigning-channel-to-display}

專案設定完成後，您必須將頻道指派給顯示器以檢視內容。

1. 導覽至所需的顯示，例如&#x200B;**DemoScreens** —> **Locations** —> **SanJose** —> **Lobby**。

1. 從動作列點選/按一下「**指派管道**」。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   或,

   從動作列點選/按一下「**控制面板**」，然後從「**已指派管道與排程」面板按一下「**+指派管道&#x200B;**」。**

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. **通道分配**&#x200B;對話框開啟。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. 從&#x200B;**設定**&#x200B;選項中，可以按名稱&#x200B;**選擇通道**&#x200B;或&#x200B;**，輸入**&#x200B;通道角色&#x200B;**、**&#x200B;優先順序&#x200B;**、**&#x200B;支援的事件&#x200B;**和**&#x200B;中斷方法&#x200B;**。**&#x200B;此外，您也可以從此對話框啟用吸引工具提示。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >請參閱[通道屬性](#channel-properties)一節，深入了解通道指派屬性。

1. 從&#x200B;**Schedule**&#x200B;選項中，選擇&#x200B;**Activation Window**&#x200B;和&#x200B;**Recurre Schedule**。
   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >請參閱[通道屬性](#channel-properties)一節，深入了解通道指派屬性。

1. 在配置首選項後，按一下&#x200B;**保存**。

### 在Chrome Player中檢視內容 {#viewing-content-output}

此範例將展示Chrome播放器的輸出。 將頻道指派給顯示器後，您必須將裝置註冊至播放器。

請參考[裝置註冊](device-registration.md)，了解如何在AEM Screens播放器上註冊裝置。

在您選擇的播放器上，將檢視下列輸出：

![new1](assets/channel-assignment/channel-assign-output.gif)

## 時間軸檢視 {#timeline-view}

將通道分配給顯示並設定重複計畫後，您可以從&#x200B;**ASSIGNED CHANNELS &amp; SCHEDULES**&#x200B;面板查看時間軸。

請依照下列步驟導覽至時間軸檢視：

1. 導覽至所需的顯示，例如&#x200B;**DemoScreens** —> **Locations** —> **SanJose** —> **Lobby**。

1. 從動作列點選/按一下「**指派管道**」。

   或,

   點選/按一下&#x200B;**控制面板**，然後從&#x200B;**指派的頻道與排程**&#x200B;面板按一下&#x200B;**時間軸**。

   ![影像](/help/user-guide/assets/channel-assignment/timeline-1.png)

## 從通道分配對話框了解通道屬性 {#channel-properties}

從&#x200B;**通道分配**&#x200B;對話框的&#x200B;**設定**&#x200B;選項設定以下屬性。

![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### 選取頻道 {#select-channel}

選取管道可讓您根據管道名稱或管道路徑提供所需管道的參考。

* **依路徑**:使用通道的絕對路徑提供顯式引用。

* **依名稱**:輸入將依內容解析為實際管道的管道名稱。此功能可讓您建立頻道的本機版本，以動態解析特定位置的內容。 例如，名稱為&#x200B;*的管道會處理當天的*，其中實際內容在兩個城市中會不同，但您在所有顯示器上仍有合理的管道角色。

### 頻道角色 {#role-channel}

管道角色定義顯示內容。 該角色由各種行動定位，且與實現該角色的實際渠道無關。

### 優先順序 {#priority-channel}

優先順序可用來排序指派，以備多個指派符合播放條件時使用。 值最高的一律優先於值較低的。 例如，如果有兩個管道A和B。A的優先順序為1,B的優先順序為2，則顯示管道B，因為其優先順序高於A。

>[!NOTE]
>
>在&#x200B;**通道分配**&#x200B;對話框中，通道的優先順序被設定為數字（最小為1），如上所述。 此外，所分配的通道也根據降序優先順序排序。

### 支援的事件 {#supported-events-channel}

* **初始載入**:在播放器啟動時載入通道。可與排程結合，指派給多個管道
* **空閒螢幕**:當畫面閒置時載入。可與排程結合，指派給多個管道
* **計時器**:需要在提供排程時設定
* **使用者互動**:如果螢幕上有使用者互動（觸控式）位於空閒通道，播放器將切換至指定通道，並在接觸螢幕時載入

### 中斷方法 {#interruption-method-channel}

>[!IMPORTANT]
> 此選項僅適用於AEM 6.4 Feature Pack 8或AEM 6.5 Feature Pack 4。

身為內容作者，您應該可以指定管道中斷的時間，以便選擇切斷非關鍵內容，但可選擇在因排程而切斷播放之前，讓重要內容完全播放。

從&#x200B;**通道分配**&#x200B;對話框中選擇以下可用於設定中斷方法的選項之一：

* **立即**:每當排程啟動或收到更新時，您都可以切斷播放並立即重新整理或播放新內容
* **在目前項目的結尾**:當激活新計畫或收到更新時，您可以選擇等待序列中的當前項目完成播放，並且僅在刷新或播放新內容之後

   >[!NOTE]
   >預設會選取此選項。

* **在序列結尾**:當啟用新排程或收到更新時，您可以選擇等待整個序列到達其結尾，而在所需序列之前，您會回圈到第1個元素，然後重新整理或播放新內容

   >[!NOTE]
   >使用第二個或第三個選項可能會導致分配上定義的排程時間稍微延遲，因為播放器在重新整理之前會等待項目或序列的結尾（在指定的時間之後）。 延遲取決於項目的播放持續時間。

從&#x200B;**通道分配**&#x200B;對話框的&#x200B;**調度**&#x200B;選項設定以下屬性。

![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### 啟用時間 {#activation-window}

「啟動」視窗可讓您選取&#x200B;**開始日期**&#x200B;和&#x200B;**結束日期**&#x200B;來顯示您的內容。

### 週期排程 {#recurrence-schedule}

「重複排程」可讓您設定內容的重複排程。 按一下&#x200B;**+新增排程** ，將週期排程新增至通道。

>[!NOTE]
>您可以新增多個循環排程至管道。
>週期排程引進了&#x200B;*DayParting*，可讓您設定一個全域排程，並在一天中的特定時間執行多個管道，然後一次對所有顯示器重複使用該設定。

您可以設定下列選項：

* **名稱**:定期排程的標題。
* **重複**:選擇排程是 **以每日**、 **每週**、每 **月**&#x200B;或每 **年**&#x200B;執行。
* **開始**:排程的開始時間。
* **結束**:排程的結束時間。您可以依時間或持續時間來設定。
   * **時間**:排程將在指定時間結束。
   * **持續時間**:排程會以小時或分鐘為單位，執行特定時段。

### 日劃分 {#dayparting}

DayParting指的是將某天分割為時段，並指定在需要的時間播放哪些內容。 AEM Screens可讓您依需求在一天、一週或一個月內，依日劃分管道。

下列範例說明在三種不同情況下管道中的DayParting:

#### 在分為多個時段的單日播放內容 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

此範例說明餐廳如何使用DayParting來展示其每日早餐、午餐和晚餐菜單。

在此，我們會將每天劃分為不同的時段，讓頻道內容在一天的指定時間內播放。 根據此使用案例，設定您的頻道播放內容的「重複排程」的下列屬性。

| **名稱** | **重複** | **啟動** | **結束** |
|---|---|---|---|
| 早餐 | 每日 | 6:00 AM | 11:00 AM |
| 午餐 | 每日 | 11:00 AM | 3:00 PM |
| 晚餐 | 每日 | 3:00 PM | 8:00 PM |

#### 在一週中的特定日期播放內容 {#playing-content-on-a-particular-day-of-the-week}

此範例顯示在賭場中實作的DayParting，該賭場每週末從晚8:00至晚10:00舉行即時活動，晚上10:00至下午1:00則提供晚餐菜單的特惠。

| **名稱** | **重複** | **啟動** | **結束** |
|---|---|---|---|
| 週末 | 每週：星期六，星期日 | 8:00 PM | 晚上10:00 |
| 特惠 | 每日：星期一 — 星期五 | 晚上10:00 | 1:00 AM |

>[!NOTE]
>
>此外，您可以為每個通道定義&#x200B;***優先順序***。 例如，若將兩個管道設為同一日期和時間，或設為同一月，則會先播放優先順序較高的管道。 優先順序的最小值可以設定為0。

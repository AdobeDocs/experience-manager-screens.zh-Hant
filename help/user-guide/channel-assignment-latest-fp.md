---
title: 渠道分配 — 最新FP
seo-title: Channel Assignment - Latest FP
description: 按照本頁瞭解「渠道分配」和「日分型」。
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1467'
ht-degree: 3%

---

# 頻道指定任務 {#channel-assignment}

>[!IMPORTANT]
>
>本節將重點介紹Screens Feature Pack及更AEM高版本的頻道分配和頻道計畫。

設定顯示後，必須為顯示器分配頻道才能查看內容。

此頁顯示為顯示器分配通道、瞭解通道屬性和DayParting。

>[!NOTE]
>
>可以為顯示器指定多個通道。


## 分配通道 {#assign-a-channel-new-release}

按照下面的部分建立AEM Screens項目並為顯示器分配通道。

### 建立AEM Screens項目和渠道 {#creating-project}

按照以下步驟設定項目和渠道：

1. 建立標題為的AEM Screens項目 **演示螢幕**。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >請參閱 [建立和管理項目](creating-a-screens-project.md) 學習如何建立AEM Screens項目。

1. 建立名為 **食堂** 的 **頻道** 的子菜單。

1. 選擇頻道並按一下 **編輯** 的子菜單。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   例如， **食堂** channel現在顯示以下影像：

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. 建立標題為 **聖何塞** 顯示為 **大堂**。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### 將頻道指派到顯示器 {#assigning-channel-to-display}

項目設定完成後，必須將頻道分配給顯示器才能查看內容。

1. 導航到所需的顯示，例如， **演示螢幕** —> **位置** —> **聖何塞** —> **大堂**。

1. 點擊/按一下 **分配通道** 按鈕。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   或,

   點擊/按一下 **儀表板** 按一下 **+分配通道** 從 **分配的渠道和計畫** 的子菜單。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. 的 **渠道分配** 對話框。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. 從 **設定** 選項，可以選擇 **按路徑** 或 **按名稱**，輸入 **渠道角色**。 **優先順序**。 **支援的事件**, **中斷方法**。 此外，還可以從此對話框啟用引用工具提示。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >請參閱 [通道屬性](#channel-properties) 的子菜單。

1. 從 **計畫** 選項 **激活窗口** 和 **定期計畫**。
   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >請參閱 [通道屬性](#channel-properties) 的子菜單。

1. 按一下 **保存** 配置首選項後。

### 在Chrome Player中查看內容 {#viewing-content-output}

此示例顯示Chrome播放器的輸出。 將頻道分配給顯示器後，必須將設備註冊到播放器。

請參閱 [設備註冊](device-registration.md) 學習如何在AEM Screens玩家上註冊設備。

您將在選擇播放器時查看以下輸出：

![new1](assets/channel-assignment/channel-assign-output.gif)

## 時間軸視圖 {#timeline-view}

在為顯示器分配了頻道並設定了重複計畫後，可以從 **分配的渠道和計畫** 的子菜單。

按照以下步驟導航到時間軸視圖：

1. 導航到所需的顯示，例如， **演示螢幕** —> **位置** —> **聖何塞** —> **大堂**。

1. 點擊/按一下 **分配通道** 按鈕。

   或,

   點擊/按一下 **儀表板** 按一下 **時間軸** 從 **分配的渠道和計畫** 的子菜單。

   ![影像](/help/user-guide/assets/channel-assignment/timeline-1.png)

## 從「通道分配」對話框瞭解通道屬性 {#channel-properties}

以下屬性是 **設定** 的上界 **渠道分配** 對話框。

![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### 選取頻道 {#select-channel}

通過選擇頻道，可以按頻道名稱或頻道路徑提供對所需頻道的引用。

* **按路徑**:使用通道的絕對路徑提供顯式參照。

* **按名稱**:輸入將按上下文解析為實際通道的通道名稱。 此功能允許您建立頻道的本地版本，以便動態解析特定於位置的內容。 例如，具有名稱的通道 *當天的交易*&#x200B;在這裡，實際內容在兩個城市會有所不同，但在所有顯示器上，您仍具有神智的頻道角色。

### 頻道角色 {#role-channel}

通道角色定義顯示的上下文。 該角色被各種操作所針對，並且與實現該角色的實際渠道無關。

### 優先順序 {#priority-channel}

優先順序用於在多個分配匹配播放條件時對分配進行排序。 值最高的值總是優先於值較低的值。 例如，如果有兩個通道A和B。A的優先順序為1,B的優先順序為2，然後顯示通道B，因為它的優先順序高於A。

>[!NOTE]
>
>通道的優先順序被設定為數字（最小為1） **渠道分配** 對話框。 另外，基於降序優先順序對所分配的通道進行排序。

### 支援的事件 {#supported-events-channel}

* **初始載入**:在播放器啟動時載入頻道。 它可以與調度組合分配給多個通道
* **空閒螢幕**:當螢幕空閒時載入。 它可以與調度組合分配給多個通道
* **計時器**:需要在提供計畫時設定
* **用戶交互**:播放器將切換到指定的頻道，如果螢幕上的用戶交互（觸摸）處於空閒頻道，則在觸摸螢幕時載入

### 中斷方法 {#interruption-method-channel}

>[!IMPORTANT]
> 此選項僅適AEM用於6.4功能包8或AEM6.5功能包4。

作為內容作者，您應該能夠指定頻道中斷的時間，以便您可以選擇切斷非關鍵內容，但可以選擇在因計畫而切斷播放之前讓重要內容充分播放。

從以下可用選項中選擇一個，以從 **渠道分配** 對話框：

* **立即**:無論何時激活計畫或收到更新，您都可以切斷播放並立即刷新或播放新內容
* **在當前項的末尾**:激活新計畫或接收到更新時，您可以選擇等待序列中的當前項目完成播放，並且僅當刷新或播放新內容之後

   >[!NOTE]
   >預設情況下，此選項處於選中狀態。

* **在序列末尾**:當激活新計畫或接收到更新時，您可以選擇等待整個序列到達其結束，並且在所需序列之前，您回到第1個元素，刷新或播放新內容

   >[!NOTE]
   >使用第二個或第三個選項可能導致分配上定義的調度時間稍微延遲，因為玩家將等待項目或序列的結束（在指定時間後）再刷新。 延遲取決於項目的播放持續時間。

以下屬性是 **計畫** 的上界 **渠道分配** 對話框。

![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### 啟用時間 {#activation-window}

激活窗口允許您選擇 **開始日期** 和 **結束日期** 顯示內容。

### 週期排程 {#recurrence-schedule}

「定期計畫」允許您為內容設定定期計畫。 按一下 **+添加計畫** 將定期計畫添加到渠道。

>[!NOTE]
>您可以向您的渠道添加多個循環計畫。
>定期計畫引入 *日分*，它允許您設定一個全局調度，其中多個通道在一天中的特定時間運行，並同時為所有顯示重新使用該設定。

可以設定以下選項：

* **名稱**:定期計畫的標題。
* **重複**:選擇計畫是否運行 **每日**。 **每週**。 **每月**&#x200B;或 **每年**。
* **開始**:計畫的開始時間。
* **結束**:計畫的結束時間。 可以按時間或持續時間設定。
   * **時間**:計畫將在指定時間結束。
   * **持續時間**:計畫以小時或分鐘為特定持續時間運行。

### 日分 {#dayparting}

DayParting是指將一天拆分為多個時段，並指定在所需時間播放哪些內容。 AEM Screens允許您根據要求在一天、一週或月內按DayParting方式安排渠道。

以下示例說明了三種不同情形中的通道中的DayParting:

#### 在分成多個時隙的單日播放內容 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

此示例說明餐廳如何使用DayParting每天展示其早餐、午餐和晚餐菜單。

在此，我們將每天劃分為不同的時隙，以便頻道內容按一天中指定的時間播放。 根據此使用情形，設定頻道播放內容的重複計畫的以下屬性。

| **名稱** | **重複** | **啟動** | **結束** |
|---|---|---|---|
| 早餐 | 每日 | 6:00 AM | 上午11:00 |
| 午餐 | 每日 | 上午11:00 | 下午3:00 |
| 晚餐 | 每日 | 下午3:00 | 晚8:00 |

#### 在一週中的某一天播放內容 {#playing-content-on-a-particular-day-of-the-week}

此示例顯示在賭場中實施的DayParting，該賭場每週末從晚上8:00至晚上10:00進行現場活動，並在晚上10:00至凌晨1:00之後提供晚餐菜單的特惠。

| **名稱** | **重複** | **啟動** | **結束** |
|---|---|---|---|
| 週末 | 每週：星期六，星期日 | 晚8:00 | 晚上10:00 |
| 特別計畫 | 每日：星期一至星期五 | 晚上10:00 | 1:00 AM |

>[!NOTE]
>
>此外，您還可以 ***優先順序*** 每個頻道。 例如，如果為同一日期和時間或同一月設定兩個頻道，則優先順序較高的頻道將首先播放。 優先順序的最小值可以設定為0。

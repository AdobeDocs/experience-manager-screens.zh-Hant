---
title: 頻道指定任務
seo-title: 頻道指定任務
description: 請詳閱本頁，了解管道指派和日劃分。
feature: 製作螢幕，通道分配
role: Administrator, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '1219'
ht-degree: 4%

---

# 頻道指定任務 {#channel-assignment}

>[!IMPORTANT]
>本節重點說明AEM 6.5.5 Screens版本以前的Feature Pack的頻道指派和排程。

設定顯示器後，您必須指派頻道給顯示器以檢視您的內容。

此頁面顯示如何指派管道給顯示器。

>[!NOTE]
>您可以指派多個管道給一個顯示器。

## 分配通道{#assign-a-channel}

請依照下列步驟，將管道指派給顯示器：

1. 導覽至所需的顯示，例如&#x200B;**DemoProject** —> **Locations** —> **SanJose** —> **StoreDisplay**。

   ![影像](assets/screen_shot_2018-08-23at25359pm.png)

1. 點選/按一下動作列中的「指定管道&#x200B;**」**

   或,

   點選/按一下&#x200B;**Dashboard**，然後從&#x200B;**ASSIGNED CHANNELS**&#x200B;面板按一下&#x200B;**+Assign Channel**&#x200B;以開啟&#x200B;**Channel Assignment**&#x200B;對話方塊。

   ![影像](/help/user-guide/assets/channel-assign1.png)

   您可以從以下部分的&#x200B;**通道分配**&#x200B;對話框配置屬性。 請參閱[通道屬性](#channel-properties)區段，深入了解通道屬性。


## 從通道分配{#channel-properties}了解通道屬性

### 參考通道{#ref-channel}

參考通道可讓您根據通道名稱或通道路徑提供對所需通道的參考。

* **依路徑**:使用通道的絕對路徑提供顯式引用。

* **依名稱**:輸入將依內容解析為實際管道的管道名稱。此功能可讓您建立頻道的本機版本，以動態解析特定位置的內容。 例如，名稱為&#x200B;*的管道會處理當天的*，其中實際內容在兩個城市中會不同，但您在所有顯示器上仍有合理的管道角色。

### 頻道角色 {#role-channel}

管道角色定義顯示內容。 該角色由各種行動定位，且與實現該角色的實際渠道無關。

### 優先順序 {#priority-channel}

優先順序可用來排序指派，以備多個指派符合播放條件時使用。 值最高的一律優先於值較低的。 例如，如果有兩個管道A和B。A的優先順序為1,B的優先順序為2，則顯示管道B，因為其優先順序高於A。

>[!NOTE]
>在&#x200B;**通道分配**&#x200B;對話框中，通道的優先順序被設定為數字（最小為1），如上所述。 此外，所分配的通道也根據降序優先順序排序。

### 支援的事件 {#supported-events-channel}

* **初始載入**:在播放器啟動時載入通道。可與排程結合，指派給多個管道
* **空閒螢幕**:當畫面閒置時載入。可與排程結合，指派給多個管道
* **計時器**:需要在提供排程時設定
* **使用者互動**:如果螢幕上有使用者互動（觸控式）位於空閒通道，播放器將切換至指定通道，並在接觸螢幕時載入

### 中斷方法 {#interruption-method-channel}

>[!IMPORTANT]
>
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

### 計劃 {#schedule-channel}

排程可讓您在應出現管道時以文字提供說明。 這也可讓您定義要顯示之頻道的開始日期（**作用中自**）和結束日期（**作用中至**）。

**顯示有趣的工具提示**:

顯示吸引工具提示會定義在管道執行期間是否必須顯示吸引工具提示(&quot;*Touch anywhere to begin*&quot;)。

### 日劃分 {#dayparting}

與&#x200B;**DayParting**&#x200B;結合時的排程可讓您設定一個全域排程，並在一天中的特定時間執行多個管道，並一次對所有顯示器重複使用該設定。

DayParting指的是將一天分割為時段，並指定在需要的時間播放哪些內容。 AEM Screens可讓您依需求在一天、一週或月內依日劃分管道。

下列範例說明三種不同情況下管道中的日分段：

#### 在分成多個時段的單日播放內容{#playing-content-on-a-single-day-divided-into-multiple-time-slots}

此範例說明餐廳如何使用日分時段來展示其早餐、午餐和晚餐菜單。

在此，我們會將每天劃分為三個不同的時段，讓頻道內容按照一天中的指定時間播放：

| **頻道** | **角色** | **優先順序** | **計劃** |
|---|---|---|---|
| 菜單_A | 早餐 |  | 6:00 過後和 11:00 之前 |
| 菜單(_B) | 午餐 |  | 11:00 過後和 15:00 之前 |
| 菜單(_C) | 晚餐 |  | 15:00 過後和 20:00 之前 |

#### 在一週的特定日播放內容{#playing-content-on-a-particular-day-of-the-week}

此範例顯示在賭場中達到的dayParting，該賭場每週末從晚8:00至晚10:00進行即時活動，晚上10:00至下午1:00之間晚餐菜單提供特惠。

<table>
 <tbody>
  <tr>
   <td><strong>頻道</strong></td>
   <td><strong>角色</strong></td>
   <td><strong>優先順序</strong></td>
   <td><strong>計劃</strong></td>
  </tr>
  <tr>
   <td>LiveConcert</td>
   <td>週末</td>
   <td> </td>
   <td>2017年10月21日 — 2017年10月22日<br />後20:00前22:00</td>
  </tr>
  <tr>
   <td>特惠晚餐</td>
   <td>週末</td>
   <td> </td>
   <td>2017年10月21日 — 2017年10月22日<br />後22:00前1:00</td>
  </tr>
 </tbody>
</table>

#### 播放特定月份/月的內容{#playing-content-for-a-particular-month-months}

此範例顯示商店的DayParting，該商店顯示其從6月到8月的夏季系列，以及從9月到10月底的秋季系列。

在此，您將建立每個月的日劃分，讓管道內容按照一年中指定的月份播放。

| **頻道** | **角色** | **優先順序** | **計劃** |
|---|---|---|---|
| SummerCollection | 夏天 |  | 2017年6月01日至2017年8月31日 |
| FallCollection | 秋季 |  | 2017年9月01日至2017年10月30日 |

>[!NOTE]
>
>此外，您可以為每個通道定義&#x200B;***優先順序***。 例如，若將兩個管道設為同一日期和時間，或設為同一月，則會先播放優先順序較高的管道。 優先順序的最小值可以設定為0。

#### 播放優先順序相同之頻道的內容{#playing-content-for-channels-with-same-priority}

此範例顯示某個商店的DayParting，該商店在12月的月份中以相同的排程顯示其冬季系列。 但由於B頻道的優先順序設為2，因此在那周；管道B會播放其內容，而非管道A。

| **頻道** | **角色** | **優先順序** | **計劃** |
|---|---|---|---|
| A | 冬季 | 1 | 2017年12月01日至2017年12月31日 |
| B | 聖誕節 | 2 | 2017年12月24日至2017年12月31日 |


>[!NOTE]
>
> 若要進一步了解DayParting，請參閱以下各節：
>
>* [處理資產中的週期](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling.html#handling-recurrence-in-assets)
>* [處理管道中資產的週期](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation.html#handling-recurrence-in-assets)


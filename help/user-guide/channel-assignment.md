---
title: 頻道指定任務
seo-title: 頻道指定任務
description: 請依照本頁瞭解渠道指派和日分割。
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '1215'
ht-degree: 4%

---


# 頻道指定任務 {#channel-assignment}

>[!IMPORTANT]
>本節重點說明AEM 6.5.5版以前的功能套件頻道指派和排程。

設定顯示後，您必須指派頻道給顯示，才能檢視您的內容。

此頁面顯示如何指派渠道給您的顯示。

>[!NOTE]
>您可以指派多個頻道至顯示器。

## 分配通道{#assign-a-channel}

請遵循下列步驟，將頻道指派給顯示器：

1. 導覽至所需的顯示畫面，例如&#x200B;**DemoProject** —> **Locations** —> **SanJose** —> **StoreDisplay**。

   ![影像](assets/screen_shot_2018-08-23at25359pm.png)

1. 點選／按一下動作列中的「指定頻道&#x200B;**」**

   或,

   點選／按一下&#x200B;**Dashboard**，然後從&#x200B;**ASSIGNED CHANNELS**&#x200B;面板按一下&#x200B;**+Assign Channel**，以開啟&#x200B;**Channel Assignment**&#x200B;對話方塊。

   ![影像](/help/user-guide/assets/channel-assign1.png)

   您可以從以下部分配置&#x200B;**Channel Assignment**&#x200B;對話框中的屬性。 請參閱[頻道屬性](#channel-properties)一節，以進一步瞭解頻道屬性。


## 從渠道分配瞭解渠道屬性{#channel-properties}

### 參考通道{#ref-channel}

參考渠道允許您根據渠道名稱或渠道路徑提供對所需渠道的參考。

* **依路徑**:您可使用渠道的絕對路徑提供明確的參照。

* **按名稱**:您可以輸入渠道的名稱，該名稱將依據上下文解析為實際渠道。此功能可讓您建立頻道的本機版本，以動態解析特定位置的內容。 例如，名稱為&#x200B;*的頻道會處理day*，其中實際內容在兩個城市中會有所不同，但您在所有顯示器上仍具有正常的頻道角色。

### 頻道角色 {#role-channel}

渠道角色定義顯示的上下文。 角色由各種動作定位，且與實際執行角色的通道無關。

### 優先順序 {#priority-channel}

優先順序用於在多個分配匹配播放條件時對分配進行排序。 值最高的一律優先於值較低的值。 例如，如果有兩個渠道A和B。A的優先順序為1,B的優先順序為2，然後顯示通道B，因為它的優先順序高於A。

>[!NOTE]
>如上所述，在&#x200B;**頻道分配**&#x200B;對話方塊中，頻道的優先順序設為數字（最低為1）。 此外，根據遞減優先順序對所分配的頻道進行排序。

### 支援的事件 {#supported-events-channel}

* **初始載入**:在播放器啟動時載入頻道。它可與排程組合指派給多個渠道
* **空閒螢幕**:當畫面閒置時載入。它可與排程組合指派給多個渠道
* **計時器**:需要在提供計畫時進行設定
* **使用者互動**:如果螢幕上有使用者互動（觸控）在閒置頻道中，播放器會切換至指定頻道，並會在觸碰螢幕時載入

### 中斷方法 {#interruption-method-channel}

>[!IMPORTANT]
>
> 此選項僅適用於AEM 6.4 Feature Pack 8或AEM 6.5 Feature Pack 4。

身為內容作者，您應該可以指定頻道中斷的時間，以便選擇切斷非關鍵內容，但可以選擇在由於排程而中斷播放之前，先讓重要內容完全播放。

從&#x200B;**通道分配**&#x200B;對話框中選擇以下用於設定中斷方法的選項之一：

* **立即**:每當排程啟動或收到更新時，您就可以切斷播放並立即重新整理或播放新內容
* **在目前項目的結尾**:當啟動新排程或收到更新時，您可以選擇等候序列中的目前項目結束播放，且必須等到您重新整理或播放新內容後
   >[!NOTE]
   >預設會選取此選項。
* **在序列結尾**:當啟動新排程或收到更新時，您可以選擇等待整個序列到達其結束，而在所需序列之前，您會回圈到第1個元素，您會重新整理或播放新內容

   >[!NOTE]
   >使用第二個或第三個選項可能導致指派上定義的排程時間稍微延遲，因為播放器會等候項目或序列結束（在指定時間之後）再重新整理。 延遲將視項目的播放持續時間而定。

### 計劃 {#schedule-channel}

排程可讓您在頻道應該出現時，在文字中提供說明。 您也可以定義開始日期（**從**&#x200B;開始作用）和結束日期（**開始作用直到**），以便顯示頻道。

**顯示有趣的工具提示**:

顯示吸引工具提示會定義在頻道執行時是否必須顯示吸引工具提示(&quot;*Touch anywhere to begin*&quot;)。

### DayParting {#dayparting}

與&#x200B;**DayParting**&#x200B;結合時的排程，可讓您設定在一天中特定時間執行多個頻道的全域排程，並一次將該設定重新用於所有顯示。

DayParting是指將一天分割為時段，並指定在所需時間播放的內容。 AEM Screens可讓您依需求，在一天、一週或月內排程日分割的渠道。

下列範例說明三種不同情況下渠道中的日分割：

#### 在分成多個時段的單日播放內容{#playing-content-on-a-single-day-divided-into-multiple-time-slots}

此範例說明餐廳如何使用日分割功能來展示其早餐、午餐和晚餐選單。

在此，我們將每天分為3個不同的時段，讓頻道內容依一天中的指定時間播放：

| **頻道** | **角色** | **優先順序** | **計劃** |
|---|---|---|---|
| 菜單A | 早餐 |  | 6:00 過後和 11:00 之前 |
| 菜單B | 午餐 |  | 11:00 過後和 15:00 之前 |
| 菜單C | 晚餐 |  | 15:00 過後和 20:00 之前 |

#### 在一週中的某一天播放內容{#playing-content-on-a-particular-day-of-the-week}

此範例顯示賭場中的dayParting：從每個週末的8:00 pm到10:00 pm之間發生即時活動，晚上10:00到1:00 am之間晚餐選單提供特惠。

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
   <td>2017年10月21日- 2017年10月22日<br /> 20:00之後22:00</td>
  </tr>
  <tr>
   <td>特惠晚餐</td>
   <td>週末</td>
   <td> </td>
   <td>2017年10月21日- 2017年10月22日<br /> 22:00後1:00</td>
  </tr>
 </tbody>
</table>

#### 播放特定月份／月份的內容{#playing-content-for-a-particular-month-months}

此範例顯示商店的DayParting，該商店顯示其夏季系列（從6月到8月）和秋季系列（從9月到10月底）。

在這裡，您將依月份建立日分割，讓頻道內容依年度指定月份播放。

| **頻道** | **角色** | **優先順序** | **計劃** |
|---|---|---|---|
| SummerCollection | 夏天 |  | 2017年6月01日至2017年8月31日 |
| FallCollection | 秋季 |  | 2017年9月01日至2017年10月30日 |

>[!NOTE]
>
>此外，您可以為每個通道定義&#x200B;***Priority***。 例如，如果針對同一天和時間或同一月設定了兩個頻道，則會先播放優先順序較高的頻道。 優先順序的最小值可以設定為0。

#### 播放相同優先順序{#playing-content-for-channels-with-same-priority}頻道的內容

此範例顯示商店的DayParting，該商店在12月的月份會以相同的排程顯示其冬季系列。 但由於B頻道的優先順序設定為2，所以在那一週；頻道B會播放其內容，而非頻道A。

| **頻道** | **角色** | **優先順序** | **計劃** |
|---|---|---|---|
| A | 冬季 | 1 | 2017年12月1日至2017年12月31日 |
| B | 聖誕節 | 2 | 2017年12月24日至2017年12月31日 |


>[!NOTE]
>
> 若要進一步瞭解DayParting，請參閱以下章節：
>
>* [處理資產中的定期](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling.html#handling-recurrence-in-assets)
>* [處理渠道中資產的週期](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation.html#handling-recurrence-in-assets)



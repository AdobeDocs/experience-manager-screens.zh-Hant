---
title: 頻道指定任務
seo-title: Channel Assignment
description: 請依照本頁所述操作，瞭解頻道指定和時段分割。
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 3%

---

# 頻道指定任務 {#channel-assignment}

>[!IMPORTANT]
>本節重點說明AEM 6.5.5 Screens版本之前Feature Pack的管道指派和排程。

設定顯示後，您必須將頻道指派給顯示以檢視您的內容。

此頁面顯示指派管道給顯示器。

>[!NOTE]
>您可以將多個色版指派給顯示器。

## 指派管道 {#assign-a-channel}

請依照下列步驟，將頻道指派給顯示器：

1. 導覽至所需的顯示畫面，例如， **示範專案** > **位置** > **SanJose** > **StoreDisplay**.

   ![影像](assets/screen_shot_2018-08-23at25359pm.png)

1. 點選/按一下 **指派頻道** 在動作列中

   或，

   點選/按一下 **儀表板** 並按一下 **+指派頻道** 從 **已指派的管道** 面板以開啟 **頻道指定任務** 對話方塊。

   ![影像](/help/user-guide/assets/channel-assign1.png)

   您可以從以下位置設定屬性： **頻道指定任務** 對話方塊。 請參閱 [頻道屬性](#channel-properties) 區段，以進一步瞭解管道屬性。


## 透過頻道指定任務瞭解頻道屬性 {#channel-properties}

### 引用頻道 {#ref-channel}

參考管道可讓您依管道名稱或管道路徑，提供所需管道的參考。

* **依路徑**：您可以使用管道的絕對路徑提供明確參照。

* **依名稱**：輸入將依內容解析為實際頻道的頻道名稱。 此功能可讓您建立管道的本機版本，以動態解析特定於位置的內容。 例如，具有名稱的管道 *每日交易*，實際內容在兩個城市中可能有所不同，但您在所有顯示器上仍擁有健全的頻道角色。

### 頻道角色 {#role-channel}

頻道角色定義顯示的內容。 角色是各種動作的鎖定目標，與履行角色的實際管道無關。

### 優先順序 {#priority-channel}

當有多個指派符合播放條件時，優先順序可用於排序指派。 值最高的總是優先於較低的值。 例如，如果有兩個管道A和B。A的優先順序為1，而B的優先順序為2，則會顯示管道B，因為其優先順序高於A。

>[!NOTE]
>頻道的優先順序在中設定為數字（最小為1） **頻道指定任務** 對話方塊，如上所述。 此外，指派的管道會根據遞減優先順序排序。

### 支援的事件 {#supported-events-channel}

* **初始載入**：在播放器啟動時載入頻道。 可與排程結合指派給多個管道
* **閒置畫面**：在畫面閒置時載入。 可與排程結合指派給多個管道
* **計時器**：提供排程時需要設定
* **使用者互動**：如果閒置頻道的熒幕上有使用者互動（觸控），播放器會切換至指定的頻道，並在觸控熒幕時載入

### 中斷方法 {#interruption-method-channel}

>[!IMPORTANT]
>
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

### 計劃 {#schedule-channel}

排程可讓您在頻道出現時以文字提供說明。 也可讓您定義開始日期(**啟用開始日期**)和結束日期(**啟用結束日期：**)以顯示管道。

**顯示有趣的工具提示**：

顯示有趣的工具提示會定義有趣的工具提示(&quot;*隨處觸控即可開始*「)是否必須在頻道執行時顯示。

### 日時段分割 {#dayparting}

與結合時的排程 **日時段分割**，可讓您設定在一天中的特定時間執行多個管道的全域排程，並一次重複使用該設定來顯示所有顯示器。

DayParting是指將一天分割為時段，並指定在所需時間播放哪些內容。 AEM Screens可讓您視需求，以一天、一週或一個月內的時段分割來排程管道。

下列範例說明在三種不同情境下，管道中的日時段分割：

#### 在單一日期播放內容，分為多個時段 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

這個範例說明餐廳如何使用日時段來展示其早餐、午餐和晚餐選單。

在此，我們將每天分成三個不同的時段，以便頻道內容能在一天中的指定時間播放：

| **頻道** | **角色** | **優先順序** | **排程** |
|---|---|---|---|
| Menu_A | 早餐 |  | 6:00 過後和 上午 11:00 之前 |
| Menu_B | 午餐 |  | 上午 11:00 過後和 下午 03:00 之前 |
| Menu_C | 晚餐 |  | 下午 03:00 過後和 下午 08:00 之前 |

#### 在一週中的特定日播放內容 {#playing-content-on-a-particular-day-of-the-week}

此範例說明在賭場中達成的dayParting，即每個週末從8:00 pm到10:00 pm進行現場活動，10:00 pm之後到1:00 am的晚餐功能表可提供特別優惠

<table>
 <tbody>
  <tr>
   <td><strong>管道</strong></td>
   <td><strong>角色</strong></td>
   <td><strong>優先順序</strong></td>
   <td><strong>計劃</strong></td>
  </tr>
  <tr>
   <td>LiveConcert</td>
   <td>週末</td>
   <td> </td>
   <td>2017年10月21日至2017年10月22日 <br /> 20:00之後22:00之前</td>
  </tr>
  <tr>
   <td>特殊餐點</td>
   <td>週末</td>
   <td> </td>
   <td>2017年10月21日至2017年10月22日 <br /> 22:00之後1:00之前</td>
  </tr>
 </tbody>
</table>

#### 播放特定月/月的內容 {#playing-content-for-a-particular-month-months}

此範例顯示商店的DayParting，該商店會顯示其從6月到8月的夏季系列以及從9月到10月的秋季系列。

在這裡，您將建立依月份劃分的日時段，以便頻道內容能依指定的月份播放。

| **頻道** | **角色** | **優先順序** | **排程** |
|---|---|---|---|
| SummerCollection | Summer |  | 2017年6月01日至2017年8月31日 |
| FallCollection | 秋季 |  | 2017年9月01日至2017年10月30日 |

>[!NOTE]
>
>此外，您也可以定義 ***優先順序*** 每個色版。 例如，如果為同一天和時間或同一月設定兩個管道，則優先順序較高的管道會先播放。 優先順序的最小值可以設為0。

#### 為具有相同優先順序的頻道播放內容 {#playing-content-for-channels-with-same-priority}

此範例顯示以12月份相同排程顯示冬季系列之商店的DayParting。 但由於頻道B的優先順序已設定為2，在該周內，頻道B會播放其內容而非頻道A。

| **頻道** | **角色** | **優先順序** | **排程** |
|---|---|---|---|
| A | Winter | 1 | 2017年12月01日至2017年12月31日 |
| B | 聖誕節 | 2 | 2017年12月24日至2017年12月31日 |


>[!NOTE]
>
> 若要深入瞭解DayParting，請參閱下列章節：
>
>* [處理資產中的週期性](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling.html#handling-recurrence-in-assets)
>* [處理頻道中資產的週期](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation.html#handling-recurrence-in-assets)

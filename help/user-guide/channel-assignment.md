---
title: 頻道指定任務
seo-title: 頻道指定任務
description: 請依照本頁來瞭解渠道指派和日分割。
seo-description: 請依照本頁來瞭解渠道指派和日分割。
uuid: fe429485-dcc9-4507-864c-b04393cedeee
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 212adcd1-835b-453d-9d3e-775366abf181
docset: aem65
translation-type: tm+mt
source-git-commit: f6ee043e41e46690e057758266f9adc5323001d2

---


# 頻道指定任務 {#channel-assignment}

本節涵蓋下列主題：

* **指派渠道**
* **瞭解渠道分配對話框的屬性**
* **日分割**

定義顯示後，您需要將頻道指派給顯示。

此頁面顯示如何指派渠道給您的顯示。

**先決條件**:

* [設定和部署畫面](configuring-screens-introduction.md)
* [建立和管理畫面專案](creating-a-screens-project.md)
* [建立和管理渠道](managing-channels.md)
* [建立和管理位置](managing-locations.md)
* [建立和管理顯示](managing-displays.md)

## 指派渠道 {#assign-a-channel}

請遵循下列步驟，將頻道指派給顯示器：

1. 導覽至所需的顯示，例如 **DemoProject** —&gt; **Locations** —&gt; **SanJose** —&gt; **** StoreDisplayDisplay。

   ![screen_shot_2018-08-23at25359pm](assets/screen_shot_2018-08-23at25359pm.png)

1. 點選／按一下動作列中的**指派頻道**

   或,

   點選／按一 **下「儀表板** 」，然後從「已分配渠道」面板按一 **下+「分配渠道」，以開啟「已分配渠道」********** 的「Channel Assignment Jognment」對話方塊。

   ![screen_shot_2018-08-23at25938pm](assets/screen_shot_2018-08-23at25938pm.png)

   可以從「渠道分配」對話框 **配置以下屬** 性：

   **頻道角色**:

   渠道角色定義顯示的上下文。 角色由各種動作定位，且與實際執行角色的通道無關。

   **參考渠道**:

   參考渠道允許您根據渠道名稱或渠道路徑提供對所需渠道的參考。

   * **依路徑**:您可使用渠道的絕對路徑提供明確的參照。
   * **按名稱**:您可以輸入渠道的名稱，該名稱將依據上下文解析為實際渠道。 此功能可讓您建立頻道的本機版本，以動態解析特定位置的內容。 例如，某個頻道的名 *稱是當天的交易*，實際內容在兩個城市中會有所不同，但您在所有顯示器上仍具有理智的頻道角色。
   **優先順序:**

   優先順序用於在多個分配匹配播放條件時對分配進行排序。 值最高的一律優先於值較低的值。 例如，如果有兩個渠道A和B。A的優先順序為1,B的優先順序為2，然後顯示通道B，因為它的優先順序高於A。

   如上所述，**「頻道分配**」對話框中的頻道優先順序設定為數字（最低為1）。 另外，根據遞減優先順序對所分配的通道進行排序。

   **支援的事件**:

   * **初始載入**:在播放器啟動時載入頻道。 它可與排程組合指派給多個渠道
   * **空閒螢幕**:當畫面閒置時載入。 它可與排程組合指派給多個渠道
   * **計時器**:需要在提供計畫時進行設定
   * **使用者互動**:如果螢幕上有使用者互動（觸控）在閒置頻道中，播放器會切換至指定頻道，並會在觸碰螢幕時載入
   **計劃**:

   排程可讓您在頻道應該出現時，在文字中提供說明。 另外，我們也讓您為要顯示的渠道定義開始日&#x200B;**期**(活動自&#x200B;**)和結束日期(**&#x200B;活動至)。 排程運算式的語法是以later.js的文字和cron語法為基礎：

   * [https://bunkat.github.io/later/parsers.html#text](https://bunkat.github.io/later/parsers.html#text)
   * [https://bunkat.github.io/later/parsers.html#cron](https://bunkat.github.io/later/parsers.html#cron)
   **顯示有趣的工具提示**:

   顯示吸引工具提示會定義吸引工具提示(「*Touch anywhere to begin*」)是否必須在頻道執行時顯示。

1. 按一 **下「儲存** 」，將建立的頻道指派給顯示。

### 日分割 {#dayparting}

與 **Dayparting**&#x200B;結合時的排程，可讓您設定具有在一天中特定時間執行之多個渠道的全域排程，並一次將該設定重新用於所有顯示。

DayParting是指將一天分割為時段，並指定在所需時間播放的內容。 AEM Screens可讓您依需求，在一天、一週或月內排程日分割的渠道。

下列範例說明三種不同情況下渠道中的分日：

#### 在分成多個時段的一天中播放內容 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

此範例說明餐廳如何使用日分割來展示其早餐、午餐和晚餐選單。

在此，我們將每天分為3個不同的時段，讓頻道內容依一天中的指定時間播放：

| **頻道** | **角色** | **優先順序** | **計劃** |
|---|---|---|---|
| 菜單A | 早餐 |  | 6:00 過後和 11:00 之前 |
| 菜單B | 午餐 |  | 11:00 過後和 15:00 之前 |
| 菜單C | 晚餐 |  | 15:00 過後和 20:00 之前 |

#### 在一週中的某一天播放內容 {#playing-content-on-a-particular-day-of-the-week}

此範例顯示在賭場中進行的日分時，每個週末從8:00 pm到10:00 pm都會進行即時活動，而晚餐選單在10:00 pm到1:00 am提供特惠。

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
   <td>2017年10月21日- 2017年10月22 <br /> 日22:00前20:00</td>
  </tr>
  <tr>
   <td>特惠晚餐</td>
   <td>週末</td>
   <td> </td>
   <td>2017年10月21日- 2017年10月22 <br /> 日1點前22點</td>
  </tr>
 </tbody>
</table>

#### 播放特定月份／月的內容 {#playing-content-for-a-particular-month-months}

此範例顯示商店的日分界，該商店顯示其夏季系列，從6月到8月，從9月到10月底。

在這裡，您會依月份建立分日，讓頻道內容依年度指定月份播放。

| **頻道** | **角色** | **優先順序** | **計劃** |
|---|---|---|---|
| SummerCollection | 夏天 |  | 2017年6月01日至2017年8月31日 |
| FallCollection | 秋季 |  | 2017年9月01日至2017年10月30日 |

>[!NOTE]
>
>此外，您可以為每 ***個頻道*** 定義「優先順序」。 例如，如果針對同一天和時間或同一月設定了兩個頻道，則會先播放優先順序較高的頻道。 優先順序的最小值可以設定為0。

#### 播放具有相同優先順序的頻道內容 {#playing-content-for-channels-with-same-priority}

此範例顯示商店的日分時間，該商店在12月的月份會以相同的排程顯示其冬季系列。 但由於B頻道的優先順序設定為2，所以在那一週；頻道B會播放其內容，而非頻道A。

| **頻道** | **角色** | **優先順序** | **計劃** |
|---|---|---|---|
| A | 冬季 | 1 | 2017年12月1日至2017年12月31日 |
| B | 聖誕節 | 2 | 2017年12月24日至2017年12月31日 |


---
title: 頻道指定任務
seo-title: 頻道指定任務
description: 請依照本頁瞭解渠道指派和日分割。
translation-type: tm+mt
source-git-commit: 081db31efda17ac12cdc88f79ed2f4e1fbfc7edf
workflow-type: tm+mt
source-wordcount: '1333'
ht-degree: 3%

---


# 頻道指定任務 {#channel-assignment}

定義顯示後，您需要將頻道指派給顯示。

此頁面顯示如何指派渠道給您的顯示。

>[!NOTE]
>您可以指派多個頻道至顯示器。

## 指派渠道 {#assign-a-channel}

請遵循下列步驟，將頻道指派給顯示器：

>[!IMPORTANT]
>
>下列Adobe Experience 6.5.5 Screens Feature Pack版本及更高版本的頻道指派對話方塊不同。 如需詳細 [資訊，請參閱渠道](/help/user-guide/channel-assignment.md#assign-a-channel-new-release) 指派。

1. 導覽至所需的顯示，例如 **DemoProject** —> **Locations** —> **SanJose** —> **** StoreDisplayDisplay。

   ![screen_shot_2018-08-23at25359pm](assets/screen_shot_2018-08-23at25359pm.png)

1. 點選／按一 **下動作列中的** 「指定頻道」

   或,

   點選／按一 **下「儀表板** 」，然後從「已分配渠道」面板按一 **下+「分配渠道」，以開啟「已分配渠道」********** 的「Channel Assignment Jognment」對話方塊。

   ![影像](/help/user-guide/assets/channel-assign1.png)

   您可以從以下部分的「渠 **道分配** 」對話框配置屬性。 請參閱 [渠道屬性](#channel-properties) ，以進一步瞭解渠道屬性。

## 為AEM 6.5.5螢幕功能套件版本指派頻道 {#assign-a-channel-new-release}

請遵循下列步驟，將頻道指派給顯示器：

1. 導覽至所需的顯示，例如 **DemoProject** —> **Locations** —> **SanJose** —> **** StoreDisplayDisplay。


1. 從動作列點選/ **按一下** 「指派頻道」

   或,

   點選／按一下「儀表板 **」，然後從「已分配渠道和計畫」面板中按一下「指定渠道** 」(+ Assign Channel **)，以開啟「渠道分配」(Channel Assignment)********** 對話框。

1. 從「設定」選項中，您可以依路徑或依名稱選擇渠道，輸入渠道角色、優先順序、支援的事件。

   >[!NOTE]
   >請參閱 [渠道屬性](#channel-properties) ，以進一步瞭解渠道屬性。

1. 從「計 **划** 」選項中，選擇「參考時區 **」、「**&#x200B;激活窗口 **」和「******&#x200B;重複計畫」。

1. 設定好 **偏好設定後** ，按一下「儲存」。

### 從渠道分配瞭解渠道屬性 {#channel-properties}

#### Reference Channel {#ref-channel}

參考渠道允許您根據渠道名稱或渠道路徑提供對所需渠道的參考。

* **依路徑**:您可使用渠道的絕對路徑提供明確的參照。

* **按名稱**:您可以輸入渠道的名稱，該名稱將依據上下文解析為實際渠道。 此功能可讓您建立頻道的本機版本，以動態解析特定位置的內容。 例如，某個頻道的名 *稱是當天的交易*，實際內容在兩個城市中會有所不同，但您在所有顯示器上仍具有理智的頻道角色。

#### 頻道角色 {#role-channel}

渠道角色定義顯示的上下文。 角色由各種動作定位，且與實際執行角色的通道無關。

#### 優先順序 {#priority-channel}

優先順序用於在多個分配匹配播放條件時對分配進行排序。 值最高的一律優先於值較低的值。 例如，如果有兩個渠道A和B。A的優先順序為1,B的優先順序為2，然後顯示通道B，因為它的優先順序高於A。

>[!NOTE]
>如上所述，在「渠道分配」對話框中，渠道的優先順序設 **置為數字** （最低為1）。 此外，根據遞減優先順序對所分配的頻道進行排序。

#### 支援的事件 {#supported-events-channel}

* **初始載入**:在播放器啟動時載入頻道。 它可與排程組合指派給多個渠道
* **空閒螢幕**:當畫面閒置時載入。 它可與排程組合指派給多個渠道
* **計時器**:需要在提供計畫時進行設定
* **使用者互動**:如果螢幕上有使用者互動（觸控）在閒置頻道中，播放器會切換至指定頻道，並會在觸碰螢幕時載入

#### 中斷方法 {#interruption-method-channel}

>[!IMPORTANT]
>
> 此選項僅適用於AEM 6.4 Feature Pack 8或AEM 6.5 Feature Pack 4。

身為內容作者，您應該可以指定頻道中斷的時間，以便選擇切斷非關鍵內容，但可以選擇在由於排程而中斷播放之前，先讓重要內容完全播放。

從「頻道分配」對話框中選擇以下選項之一，以設定中 **斷方法** :

* **立即**:每當排程啟動或收到更新時，您就可以切斷播放並立即重新整理或播放新內容
* **在目前項目的結尾**:當啟動新排程或收到更新時，您可以選擇等候序列中的目前項目結束播放，且必須等到您重新整理或播放新內容後
   >[!NOTE]
   >預設會選取此選項。
* **在序列結尾**:當啟動新排程或收到更新時，您可以選擇等待整個序列到達其結束，而在所需序列之前，您會回圈到第1個元素，您會重新整理或播放新內容

   >[!NOTE]
   >使用第二個或第三個選項可能導致指派上定義的排程時間稍微延遲，因為播放器會等候項目或序列結束（在指定時間之後）再重新整理。 延遲將視項目的播放持續時間而定。

#### 計劃 {#schedule-channel}

排程可讓您在頻道應該出現時，在文字中提供說明。 另外，我們也讓您為要顯示的渠道定義開始日&#x200B;**期**(活動自&#x200B;**)和結束日期(**&#x200B;活動至)。

**顯示有趣的工具提示**:

顯示吸引工具提示會定義吸引工具提示(「*Touch anywhere to begin*」)是否必須在頻道執行時顯示。

### 日分割 {#dayparting}

排程與日分 **割結合**，可讓您設定具有在一天中特定時間執行之多個渠道的全域排程，並一次對所有顯示重複使用該設定。

DayParting是指將一天分割為時段，並指定在所需時間播放的內容。 AEM Screens可讓您依需求，在一天、一週或月內排程日分割的渠道。

下列範例說明三種不同情況下渠道中的日分割：

#### 在分成多個時段的一天中播放內容 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

此範例說明餐廳如何使用日分割功能來展示其早餐、午餐和晚餐選單。

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

此範例顯示商店的日分割，該商店會顯示其6月到8月的夏季系列，以及9月到10月底的秋季系列。

在這裡，您將依月份建立日分割，讓頻道內容依年度指定月份播放。

| **頻道** | **角色** | **優先順序** | **計劃** |
|---|---|---|---|
| SummerCollection | 夏天 |  | 2017年6月01日至2017年8月31日 |
| FallCollection | 秋季 |  | 2017年9月01日至2017年10月30日 |

>[!NOTE]
>
>此外，您可以為每 ***個頻道*** 定義「優先順序」。 例如，如果針對同一天和時間或同一月設定了兩個頻道，則會先播放優先順序較高的頻道。 優先順序的最小值可以設定為0。

#### 播放具有相同優先順序的頻道內容 {#playing-content-for-channels-with-same-priority}

此範例顯示商店的日分割，該商店在12月的月份會以相同的排程顯示其冬季系列。 但由於B頻道的優先順序設定為2，所以在那一週；頻道B會播放其內容，而非頻道A。

| **頻道** | **角色** | **優先順序** | **計劃** |
|---|---|---|---|
| A | 冬季 | 1 | 2017年12月1日至2017年12月31日 |
| B | 聖誕節 | 2 | 2017年12月24日至2017年12月31日 |


>[!IMPORTANT]
>
> 若要進一步瞭解日分割，請參閱以下章節：
>
>* [處理資產中的定期](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling.html#handling-recurrence-in-assets)
>* [處理渠道中資產的週期](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation.html#handling-recurrence-in-assets)



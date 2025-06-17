---
title: 頻道指定任務
description: 瞭解頻道指定任務與時段分割。
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 2%

---

# 頻道指定任務 {#channel-assignment}

>[!IMPORTANT]
>本節重點說明AEM 6.5.5 Screens版本之前Feature Pack的管道指派和排程。

設定顯示後，將頻道指派給顯示以檢視您的內容。

此頁面顯示指派管道給顯示器。

>[!NOTE]
>您可以將多個色版指派給顯示器。

## 指派管道 {#assign-a-channel}

請依照下列步驟，將頻道指派給顯示器：

1. 導覽至所需的顯示區，例如，**DemoProject** > **位置** > **SanJose** > **StoreDisplay**。

   ![影像](assets/screen_shot_2018-08-23at25359pm.png)

1. 按一下動作列中的&#x200B;**指派頻道**。

   或，

   按一下&#x200B;**儀表板**，然後從&#x200B;**指派的管道**&#x200B;面板按一下&#x200B;**+指派管道**，以便您可以開啟&#x200B;**管道指派**&#x200B;對話方塊。

   ![影像](/help/user-guide/assets/channel-assign1.png)

   您可以從下節的&#x200B;**頻道指定任務**&#x200B;對話方塊設定屬性。 請參閱[管道屬性](#channel-properties)區段，以取得有關管道屬性的詳細資訊。

## 透過頻道指定任務瞭解頻道屬性 {#channel-properties}

### 引用頻道 {#ref-channel}

參考管道可讓您透過管道名稱或管道路徑，提供所需管道的參考。

* **依路徑** — 您使用管道的絕對路徑提供明確參照。

* **依名稱** — 您輸入依內容解析為實際管道的管道名稱。 此功能可讓您建立管道的本機版本，以便動態解析特定於位置的內容。 例如，名稱為&#x200B;*每日交易*&#x200B;的管道，實際內容在兩個城市中可能不同，但您在所有顯示器上仍擁有健全的管道角色。

### 頻道角色 {#role-channel}

頻道角色定義顯示的內容。 角色以各種動作為目標，與履行角色的實際管道無關。

### 優先順序 {#priority-channel}

當有多個指派符合播放條件時，優先順序可用於排序指派。 值最高的總是優先於較低的值。 例如，如果有兩個管道A和B。A的優先順序為1，而B的優先順序為2，則會顯示管道B，因為其優先順序高於A。

>[!NOTE]
>如上所述，在&#x200B;**頻道指定任務**&#x200B;對話方塊中，頻道的優先順序設定為數字（最小值為1）。 此外，指派的管道會根據遞減優先順序排序。

### 支援的事件 {#supported-events-channel}

* **初始載入** — 在播放器啟動時載入頻道。 可透過排程將其指派給多個管道。
* **閒置畫面** — 當畫面閒置時載入。 可透過排程將其指派給多個管道。
* **計時器** — 提供排程時必須設定。
* **使用者互動** — 如果使用者在閒置頻道的熒幕上進行互動（觸控），則播放器會切換至指定的頻道，並在觸碰熒幕時載入。

### 中斷方法 {#interruption-method-channel}

>[!IMPORTANT]
>
> 此選項僅適用於<!--AEM 6.4 Feature Pack 8 or -->AEM 6.5 Feature Pack 4。

作為內容作者，請指定頻道何時中斷。 這麼做可讓您視需要剪下非關鍵內容，但因排程而剪下播放內容之前，可選擇性讓重要內容播放。

按一下下列其中一個選項，這些選項可用於從&#x200B;**頻道指定任務**&#x200B;對話方塊設定中斷方法：

* **立即** — 每當排程啟動或收到更新時，您可以中斷播放並立即重新整理或播放新內容。
* **在目前專案結尾** — 當新的排程啟動或收到更新時，您可以選擇等待序列中的目前專案完成播放。 之後才能重新整理或播放新內容。

  >[!NOTE]
  >依預設，會選取此選項。
* **在順序結尾** — 當新的排程啟動或收到更新時，您可以選擇等待整個順序結束。 接著，您可以在所要的序列之前，回圈回到第一個元素、重新整理或播放新內容。

  >[!NOTE]
  >使用第二個或第三個選項可能會導致指派上定義的排程時間稍微延遲。 原因是因為播放器會等待專案或序列的結尾（在指定的時間後），再重新整理。 延遲取決於專案的播放持續時間。

### 排程 {#schedule-channel}

排程可讓您在頻道應出現的時間，以文字提供說明。 它也可讓您定義要顯示的管道的開始日期（**啟用從**）和結束日期（**啟用到**）。

**顯示有趣的工具提示**

顯示有趣的工具提示定義是否必須在頻道執行時顯示有趣的工具提示（&quot;*隨處觸控以開始*&quot;）。

### 日時段分割 {#dayparting}

與&#x200B;**DayParting**&#x200B;結合使用時，排程可讓您設定在一天中的特定時間執行多個管道的全域排程，並重複使用針對所有顯示設定好的排程。

DayParting是指將一天分割為時段，並指定在所需時間播放哪些內容。 AEM Screens可讓您視需求，依照「日時段分割」的方式，在一天、一週或一個月內排程管道。

以下範例說明在三種不同情境下，管道中的「日」劃分：

#### 在單一日期播放內容，分為多個時段 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

此範例說明餐廳如何使用DayParting來展示其早餐、午餐和晚餐功能表。

在此，您可以將每天分成三個不同的時段，以便頻道內容能在一天中的指定時間播放：

| **頻道** | **角色** | **優先順序** | **排程** |
|---|---|---|---|
| Menu_A | 早餐 |  | 6:00之後及11:00之前 |
| Menu_B | 午餐 |  | 11:00之後及15:00之前 |
| Menu_C | 晚餐 |  | 15:00之後及20:00之前 |

#### 在一週中的特定日播放內容 {#playing-content-on-a-particular-day-of-the-week}

此範例說明在賭場中達成的dayParting，即每個週末從晚上8:00到晚上10:00都舉行現場活動，並且晚餐功能表在下午10:00到凌晨1:00都提供特別優惠。

<table>
 <tbody>
  <tr>
   <td><strong>管道</strong></td>
   <td><strong>角色</strong></td>
   <td><strong>優先順序</strong></td>
   <td><strong>排程</strong></td>
  </tr>
  <tr>
   <td>LiveConcert</td>
   <td>週末</td>
   <td> </td>
   <td>2017年10月21日至2017年10月22日20:00之後22:00之前<br /></td>
  </tr>
  <tr>
   <td>特殊餐點</td>
   <td>週末</td>
   <td> </td>
   <td>2017年10月21日至2017年10月22日22:00後1:00前<br /></td>
  </tr>
 </tbody>
</table>

#### 播放特定月/月的內容 {#playing-content-for-a-particular-month-months}

此範例顯示商店的DayParting，該商店會顯示其從6月到8月的夏季系列以及從9月到10月的秋季系列。

在此，您可建立每月的DayParting，以便頻道內容能按照一年中的指定月份播放。

| **頻道** | **角色** | **優先順序** | **排程** |
|---|---|---|---|
| SummerCollection | Summer |  | 2017年6月01日至2017年8月31日 |
| FallCollection | 秋季 |  | 2017年9月1日至2017年10月30日 |

>[!NOTE]
>
>此外，您也可以為每個管道定義&#x200B;***優先順序***。 例如，如果為同一天和時間或同一月設定兩個管道，則優先順序較高的管道會先播放。 優先順序的最小值可以設為0。

#### 為具有相同優先順序的頻道播放內容 {#playing-content-for-channels-with-same-priority}

此範例顯示商店的DayParting，該商店在12月份以相同的排程顯示其冬季系列。 但由於頻道B的優先順序已設定為2，在該周內，頻道B會播放其內容而非頻道A。

| **頻道** | **角色** | **優先順序** | **排程** |
|---|---|---|---|
| A | Winter | 1 | 2017年12月01日至2017年12月31日 |
| B | 聖誕節 | 2 | 2017年12月24日至2017年12月31日 |


>[!NOTE]
>
> 若要深入瞭解DayParting，請參閱下列章節：
>
>* [在Assets中處理週期](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling)
>* [在頻道中處理Assets的週期](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation)

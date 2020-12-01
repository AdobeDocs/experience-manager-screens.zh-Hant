---
title: 頻道分配——最新的FP
seo-title: 頻道分配——最新的FP
description: 請依照本頁來瞭解渠道指派和DayParting。
translation-type: tm+mt
source-git-commit: 9b54b153676852742859b704ac9aedf908fceecf
workflow-type: tm+mt
source-wordcount: '1471'
ht-degree: 2%

---


# 頻道指定任務 {#channel-assignment}

>[!IMPORTANT]
>
>本節重點說明AEM 6.5.5 Screens Feature Pack及更新版本的頻道指派與排程。

設定顯示後，您必須指派頻道給顯示，才能檢視您的內容。

本頁顯示如何指派渠道給您的顯示、瞭解渠道屬性和DayParting。

>[!NOTE]
>
>您可以指派多個頻道至顯示器。


## 分配通道{#assign-a-channel-new-release}

請依照下列章節建立AEM Screens專案，並指派頻道至顯示器。

### 建立AEM Screens專案和頻道{#creating-project}

請依照下列步驟來設定專案和渠道：

1. 建立標題為&#x200B;**DemoScreens**&#x200B;的AEM Screens專案。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >請參閱[建立和管理專案](creating-a-screens-project.md)以瞭解如何建立AEM Screens專案。

1. 在&#x200B;**Channels**&#x200B;資料夾中建立名為&#x200B;**Cafeteria**&#x200B;的序列頻道。

1. 選擇頻道，然後從動作列按一下「編輯」，將內容新增至頻道。****

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   例如，**Cafeteria**&#x200B;頻道現在會顯示下列影像：

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. 建立標題為&#x200B;**SanJose**&#x200B;的位置，並建立標題為&#x200B;**Lobby**&#x200B;的顯示。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### 為顯示指定頻道{#assigning-channel-to-display}

專案設定完成後，您必須將頻道指派給顯示器，才能檢視內容。

1. 導覽至所需的顯示畫面，例如&#x200B;**DemoScreens** —> **Locations** —> **SanJose** —> **Lobby**。

1. 從動作列點選／按一下「指定頻道&#x200B;**」。**

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   或,

   從動作列點選／按一下「**儀表板**」，然後從「已指派的頻道與排程」面板按一下「**+指定頻道**」。****

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. 將開啟&#x200B;**通道分配**&#x200B;對話框。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. 從&#x200B;**Settings**&#x200B;選項中，可以按路徑&#x200B;**或**&#x200B;按名稱&#x200B;**選擇渠道**，輸入「渠道角色&#x200B;**、** Priority **、**&#x200B;支援的事件&#x200B;**和**&#x200B;中斷方法&#x200B;**。**&#x200B;此外，您也可以從此對話方塊啟用吸引工具提示。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >請參閱[頻道屬性](#channel-properties)一節，以進一步瞭解頻道指派屬性。

1. 從&#x200B;**Schedule**&#x200B;選項中，選擇&#x200B;**激活窗口**&#x200B;和&#x200B;**Recurreance Schedule**。
   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >請參閱[頻道屬性](#channel-properties)一節，以進一步瞭解頻道指派屬性。

1. 在配置首選項後，按一下「保存」。****

### 在Chrome Player中檢視內容{#viewing-content-output}

此範例將展示Chrome Player的輸出。 將頻道指派給顯示器後，您必須將裝置註冊到播放器。

請參閱[裝置註冊](device-registration.md)以瞭解如何在AEM Screens播放器上註冊裝置。

在您選擇的播放器上，您將檢視下列輸出：

![new1](assets/channel-assignment/channel-assign-output.gif)

## 時間軸檢視{#timeline-view}

在將頻道指派給顯示器並設定定期排程後，您就可以從&#x200B;**ASSIGNED CHANNELS &amp; SCHEDULES**&#x200B;面板檢視時間軸。

請依照下列步驟導覽至時間軸檢視：

1. 導覽至所需的顯示畫面，例如&#x200B;**DemoScreens** —> **Locations** —> **SanJose** —> **Lobby**。

1. 從動作列點選／按一下「指定頻道&#x200B;**」。**

   或,

   點選／按一下「**儀表板**」，然後從「已指派頻道與排程」面板按一下「**時間軸**」。****

   ![影像](/help/user-guide/assets/channel-assignment/timeline-1.png)

## 瞭解渠道分配對話框中的渠道屬性{#channel-properties}

從&#x200B;**渠道分配**&#x200B;對話框中的&#x200B;**設定**&#x200B;選項設定以下屬性。

![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### 選取頻道 {#select-channel}

選擇渠道可讓您根據渠道名稱或渠道路徑提供所需渠道的參考。

* **依路徑**:您可使用渠道的絕對路徑提供明確的參照。

* **按名稱**:您可以輸入渠道的名稱，該名稱將依據上下文解析為實際渠道。此功能可讓您建立頻道的本機版本，以動態解析特定位置的內容。 例如，名稱為&#x200B;*的頻道會處理day*，其中實際內容在兩個城市中會有所不同，但您在所有顯示器上仍具有正常的頻道角色。

### 頻道角色 {#role-channel}

渠道角色定義顯示的上下文。 角色由各種動作定位，且與實際執行角色的通道無關。

### 優先順序 {#priority-channel}

優先順序用於在多個分配匹配播放條件時對分配進行排序。 值最高的一律優先於值較低的值。 例如，如果有兩個渠道A和B。A的優先順序為1,B的優先順序為2，然後顯示通道B，因為它的優先順序高於A。

>[!NOTE]
>
>如上所述，在&#x200B;**頻道分配**&#x200B;對話方塊中，頻道的優先順序設為數字（最低為1）。 此外，根據遞減優先順序對所分配的頻道進行排序。

### 支援的事件 {#supported-events-channel}

* **初始載入**:在播放器啟動時載入頻道。它可與排程組合指派給多個渠道
* **空閒螢幕**:當畫面閒置時載入。它可與排程組合指派給多個渠道
* **計時器**:需要在提供計畫時進行設定
* **使用者互動**:如果螢幕上有使用者互動（觸控）在閒置頻道中，播放器會切換至指定頻道，並會在觸碰螢幕時載入

### 中斷方法 {#interruption-method-channel}

>[!IMPORTANT]
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

從&#x200B;**渠道分配**&#x200B;對話框中的&#x200B;**計畫**&#x200B;選項設定以下屬性。

![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### 啟用時間 {#activation-window}

「啟動」視窗可讓您選擇&#x200B;**開始日期**&#x200B;和&#x200B;**結束日期**&#x200B;來顯示您的內容。

### 週期排程 {#recurrence-schedule}

「定期排程」可讓您設定內容的循環排程。 按一下&#x200B;**+新增排程**，將定期排程新增至您的頻道。

>[!NOTE]
>您可以新增多個循環計畫至渠道。
>定期排程引入&#x200B;*DayParting*，可讓您設定在一天中特定時間執行多個頻道的全域排程，並一次將該設定重新用於所有顯示。

您可以設定下列選項：

* **名稱**:定期排程的標題。
* **重複**:選擇計畫是運行 **Daily**、 **Weekly**、 **Monthly** ****&#x200B;還是Yearly Really Really。
* **開始**:排程的開始時間。
* **結束**:排程的結束時間。您可以依時間或持續時間來設定。
   * **時間**:排程將在指定時間結束。
   * **持續時間**:排程會以小時或分鐘為單位，在特定時段內執行。

### DayParting {#dayparting}

DayParting是指將一天分割為時段，並指定在所需時間播放的內容。 AEM Screens可讓您根據需求，在一天、一週或月內排程DayParting的渠道。

下列範例說明在三種不同情況下的渠道中的DayParting:

#### 在分成多個時段的單日播放內容{#playing-content-on-a-single-day-divided-into-multiple-time-slots}

此範例說明餐廳如何使用DayParting來展示其每日的早餐、午餐和晚餐菜單。

在此，我們將每天分割為不同的時段，讓頻道內容在一天中的指定時間播放。 根據此使用案例，為渠道設定下列「定期排程」屬性以播放內容。

| **名稱** | **重複** | **啟動** | **結束** |
|---|---|---|---|
| 早餐 | 每日 | 6:00 AM | 11:00 AM |
| 午餐 | 每日 | 11:00 AM | 3:00 PM |
| 晚餐 | 每日 | 3:00 PM | 8:00 PM |

#### 在一週中的某一天播放內容{#playing-content-on-a-particular-day-of-the-week}

此範例顯示在賭場中實作的DayParting，該賭場每週末從8:00 pm到10:00 pm都會進行即時活動，而且晚上10:00到1:00 am之後，晚餐功能表會提供特惠。

| **名稱** | **重複** | **啟動** | **結束** |
|---|---|---|---|
| 週末 | 每週：星期六，星期日 | 8:00 PM | 10:00 PM |
| 特惠 | 每日：星期一至星期五 | 10:00 PM | 1:00 AM |

>[!NOTE]
>
>此外，您可以為每個通道定義&#x200B;***Priority***。 例如，如果針對同一天和時間或同一月設定了兩個頻道，則會先播放優先順序較高的頻道。 優先順序的最小值可以設定為0。

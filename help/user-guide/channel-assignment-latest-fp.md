---
title: 頻道分配——最新的FP
seo-title: 頻道分配——最新的FP
description: 請依照本頁瞭解渠道指派和日分割。
translation-type: tm+mt
source-git-commit: 1c6a7342288a5d78dbea91d29ff8e5d6c8fec486
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 2%

---


# 頻道指定任務 {#channel-assignment}

>[!IMPORTANT]
>本節重點說明AEM 6.5.5 Screens Feature Pack及更新版本的頻道指派與排程。

設定顯示後，您必須指派頻道給顯示，才能檢視您的內容。

此頁面顯示如何指派渠道給您的顯示。

>[!NOTE]
>您可以指派多個頻道至顯示器。


## 指派渠道 {#assign-a-channel-new-release}

請依照下列章節建立AEM Screens專案，並指派頻道至顯示器。

### 建立AEM畫面專案和頻道 {#creating-project}

請依照下列步驟來設定專案和渠道：

1. 建立標題為「 **DemoScreens」的AEM Screens專案**。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >請參閱「 [建立和管理專案](creating-a-screens-project.md) 」以瞭解如何建立AEM Screens專案。

1. 在「頻道」資料夾中建立名 **為** 「食堂」 **的序列頻道** 。

1. 選取頻道，然後從動 **作列按一下** 「編輯」，將內容新增至頻道。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   例如， **Cafeteria** 頻道現在會顯示下列影像：

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. 建立標題為 **SanJose** 的位置，以及顯示為 **Lobby**。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### 將頻道指派給顯示 {#assigning-channel-to-display}

完成專案設定後，您必須將頻道指派給顯示器，才能檢視內容。

1. 導覽至所需的顯示畫面，例如 **Screens** —> **Locations** —> **Jose** — **** Lobby Demo。

1. 從動作列點選/ **按一下** 「指派渠道」。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   或,

   點選／按一 **下「控制面板** 」，然後從「已指派的頻道與排程 **」面板按一下「** +指派頻道 **** 」。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. 「渠 **道分配** 」對話框開啟。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. 從「設 **定** 」選項中，您可以依路徑或依名稱選擇渠道，輸入渠道角色、優先順序、支援的事件和中斷方法。 此外，您也可以從此對話方塊啟用吸引工具提示選項。

   ![影像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >請參閱 [渠道屬性](#channel-properties) ，以進一步瞭解渠道屬性。

1. 從「計 **划** 」選項中，選擇「參考時區 **」、「**&#x200B;激活窗口 **」和「******&#x200B;重複計畫」。

1. 設定好 **偏好設定後** ，按一下「儲存」。

### 在Chrome Player中檢視內容 {#viewing-content-output}

### 從渠道分配瞭解渠道屬性 {#channel-properties}

### Reference Channel {#ref-channel}

參考渠道允許您根據渠道名稱或渠道路徑提供對所需渠道的參考。

* **依路徑**:您可使用渠道的絕對路徑提供明確的參照。

* **按名稱**:您可以輸入渠道的名稱，該名稱將依據上下文解析為實際渠道。 此功能可讓您建立頻道的本機版本，以動態解析特定位置的內容。 例如，某個頻道的名 *稱是當天的交易*，實際內容在兩個城市中會有所不同，但您在所有顯示器上仍具有理智的頻道角色。

### 頻道角色 {#role-channel}

渠道角色定義顯示的上下文。 角色由各種動作定位，且與實際執行角色的通道無關。

### 優先順序 {#priority-channel}

優先順序用於在多個分配匹配播放條件時對分配進行排序。 值最高的一律優先於值較低的值。 例如，如果有兩個渠道A和B。A的優先順序為1,B的優先順序為2，然後顯示通道B，因為它的優先順序高於A。

>[!NOTE]
>如上所述，在「渠道分配」對話框中，渠道的優先順序設 **置為數字** （最低為1）。 此外，根據遞減優先順序對所分配的頻道進行排序。

### 支援的事件 {#supported-events-channel}

* **初始載入**:在播放器啟動時載入頻道。 它可與排程組合指派給多個渠道
* **空閒螢幕**:當畫面閒置時載入。 它可與排程組合指派給多個渠道
* **計時器**:需要在提供計畫時進行設定
* **使用者互動**:如果螢幕上有使用者互動（觸控）在閒置頻道中，播放器會切換至指定頻道，並會在觸碰螢幕時載入

### 中斷方法 {#interruption-method-channel}

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
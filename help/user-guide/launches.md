---
title: 使用螢幕啟動更新內容
seo-title: Content Update using Screens Launch
description: 內容作者可以建立頻道的未來版本，即「啟動」，並進一步設定此發佈的即時日期，允許內容在設備或播放器中即時。
seo-description: Content authors can create future version of the channel(s), known as Launch and further setting live date for this launch allows content to be live in devices or players.
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
feature: Authoring Screens, Launches
role: Admin, Developer
level: Intermediate
exl-id: b610e5dd-e0c6-45e6-bf9b-27be2054bc8f
source-git-commit: 2cc613454d0d20a42871858e3d754e1b0e161dc3
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 0%

---

# 使用螢幕啟動更新內容 {#launches}

內容作者可以建立頻道的未來版本，即 **螢幕啟動** 並進一步確定這次發射的即時日期。 這允許內容在指定的即時日期在設備或播放器中即時。

在我的幫助下 ***螢幕啟動***，作者可以預覽啟動中的每個頻道，並且應該能夠啟動審閱請求。 批准者組將獲取通知，並可以批准或拒絕請求。 當到達即時日期時，內容在設備中播放。

例如，如果作者要建立c1、c2（渠道）的未來版本，則會建立啟動並設定即時日期（例如，11月10日上午8:00）。 內容中的任何進一步更新都將發送出去以供審閱。

一旦獲得批准並進入即時日期（11月10日上午8:00），此產品發佈將在設備或玩家上播放內容。

## 要求 {#requirements}

在開始利用之前 *螢幕啟動* 在AEM Screens項目中，確保您瞭解寬限期的概念及其相關性。

在玩家的設定即時日期運行體驗涉及：

* 推廣發射（通常需要幾秒鐘）

* 發佈資源以發佈實例（通常需要幾分鐘時間，取決於需要發佈的渠道或資產的大小）

* 更新離線內容完成所花的時間（通常需要幾分鐘）

* 玩家從發佈實例下載內容所花的時間（通常需要幾分鐘，具體取決於需要下載的資產的頻寬和大小）

* 伺服器和播放器的任何時間差

### 瞭解寬限期 {#understanding-grace-period}

為了讓玩家能夠在設定的即時日期開始播放內容，我們需要在即時日期之前開始前面的活動。

如果即時日期為 *11月24日上午9點* 寬限期 *24小時*，則上述操作序列將從（即時日期 — 寬限期）開始，即11月23日上午9:00伺服器時間。 這給了24小時時間完成上述所有動作，內容將送達玩家。 玩家將瞭解這是一個發佈內容，因此內容不會立即播放，但玩家將將此內容儲存為未來版本，並將在玩家的時區的設定實況日期正確開始播放。

例如，假設伺服器在PST中，設備在EST中，最大時間差為3小時，在這種情況下，假定從作者處進行發佈需要1分鐘，而從作者處進行發佈需要10分鐘，播放器通常可以在10-15分鐘內下載資源。 然後寬限期=時間差（3小時）+推廣發射的時間（1分鐘）+發佈發射的時間（10分鐘）+在播放器（10-15分鐘）+緩衝區（要安全，例如30分鐘）= 3小時56分鐘= 14160秒。

因此，無論何時我們安排任何發佈活動，促銷都將以此偏移量提前開始。 在上述等式中，大多數項目不需要太多時間，只要我們知道伺服器與任何玩家之間的最大時間差，就可以對此偏移量使用適當的猜測。

>[!NOTE]
>
>出廠時，螢幕啟動的寬限期設定為24小時，這意味著當我們為以下資源的任何啟動設定了即時日期 */內容/螢幕*，升級將以此偏移開始。

### 更新開箱即用寬限期 {#updating-out-of-the-box-grace-period}

本節介紹如何將現成的寬限期更新為10分鐘。

1. 導航到CRXDE Lite，然後導航到 `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`。
2. 按一下右鍵並複製檔案。
3. 導航到 `/apps/system/config` 並按一下右鍵並貼上。
4. 按兩下 `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` 在編輯器中以CRXDE Lite開啟檔案。 它必須顯示路徑的寬限期 */content/screens/* 如 **86400**。 將該值更改為 **600**。

現在，文本檔案中的內容應類似於：

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

由於您在上例中將寬限期設定為10分鐘，因此，當您為以下資源的任何啟動設定有效日期時 */內容/螢幕*，升級將以此偏移開始。

例如，如果即時日期設定為11月24日上午9:00，寬限期為600秒，則促銷作業將於11月24日上午8:50開始。

## 使用螢幕啟動 {#using-launches}

本節演示如何在您的AEM Screens項目中實施螢幕啟動。

### 建立螢幕啟動 {#creating-a-launch}

按照以下步驟將螢幕啟動功能實施到您的AEM Screens項目：

1. 在您的AEM Screens項目中建立序列通道，例如 **啟動演示** —> **頻道** —> **未來發佈**，如下所示。

   >[!CAUTION]
   >
   >您必須從您的AEM Screens項目中預先存在的渠道建立啟動。

   ![影像](/help/user-guide/assets/launches-images/launches-11.png)

1. 選擇頻道 **未來發佈** 按一下 **建立啟動** 按鈕。

   ![影像](/help/user-guide/assets/launches-images/launches-12.png)

1. 的 **建立啟動** 的子菜單。 您可以選擇在嚮導中已經可見的通道，或按一下 **+添加通道** 添加要為其建立啟動的通道。

1. 按一下 **下一個** 從 **建立啟動** 的子菜單。 的 **包括子頁** 選項。

   ![影像](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >您可以使用 **+添加通道** 選項，以添加要為其建立啟動的其他通道。

   要使用 **添加通道** 選項，導航到要為其建立啟動的通道，然後按一下 **選擇**。

   的 **選擇** 如果嘗試選擇多個通道或資料夾來添加啟動，則將禁用此選項。

   ![影像](/help/user-guide/assets/launches-images/launches-14.png)

   選擇頻道/頻道後，按一下 **下一個**。


1. 輸入 **啟動標題** 如 **夏季促銷** 而你不需要 **啟動日期**，如下圖所示。 按一下&#x200B;**建立**。

   >[!NOTE]
   >
   >*啟用或檢查* 選項 **繼承源頁即時資料** 允許在啟動中將頻道建立為即時副本。 如果在原始通道中進行了任何更改，則這些更改將自動應用於啟動通道。
   >
   >
   >*禁用或取消檢查* **繼承源頁即時資料** 允許在啟動時複製頻道，而不需要任何即時關係。 因此，如果對原始頻道進行了任何更改，這些更改不會應用於啟動頻道。

   ![影像](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >您可以在此步驟中設定即時啟動日期，也可以在建立啟動後編輯啟動的屬性時稍後設定它。

   **瞭解啟動促銷範圍**

   * **促進全面啟動**:啟動的所有頻道都在設定的即時日期進行升級。
   * **升級修改的頁面**:將只升級修改的啟動資源。 建議在不需要啟動審閱時使用此選項。
   * **升級已批准的頁面**:此選項要求啟動批准工作流在啟動渠道上運行。 在設定的即時日期僅升級已批准的頁面。

      >[!CAUTION]
      >
      >啟動即時日期尊重播放器/設備的時區，而不是伺服器。

1. 您將看到您的啟動已建立。 可以按一下 **開啟** 在編輯器中查看頁面，或按一下 **完成** 導航回項目。

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   按一下 **完成** 允許您導航回 **未來發佈** 頻道。

   ![影像](/help/user-guide/assets/launches-images/launches-16.png)


### 編輯啟動屬性以設定即時日期和範圍 {#editing-the-launch-properties-to-set-the-live-date-and-scope}

建立啟動後，您可以使用 **啟動屬性**。

* **啟動日期**，指即時日期，即根據播放器的時區在螢幕播放器中播放內容的日期或時間。
* **生產就緒**，允許在升級這些頻道後發佈頻道，啟用現成功能，因此無需更改。
* **範圍**，決定在發佈促銷期間要推廣哪些渠道。


按照以下步驟編輯啟動屬性：

1. 導航到通道 **未來發佈**。 *（即待發射）* 並選擇通道，如下圖所示。

   ![影像](/help/user-guide/assets/launches-images/launches-17.png)

1. 按一下 **儀表板** 從動作欄中，您會看到 **掛起的啟動** 的子菜單。

   ![影像](/help/user-guide/assets/launches-images/launches-18.png)

1. 選擇啟動並按一下 **啟動屬性** 從 **掛起的啟動** 的子菜單。

   ![影像](/help/user-guide/assets/launches-images/launches-19.png)

### 編輯螢幕啟動以添加或刪除通道  {#editing-the-screens-launch-to-add-or-remove-channels}

建立啟動後，可以使用 **編輯啟動** 的雙曲餘切值。

完成後，按一下 **保存** 導航回 **未來發佈** 頻道。

### 手動升級螢幕啟動{#promote-the-screens-launch-manually}

您可以使用 **升級啟動** 的 **掛起的啟動** 的子菜單。

您可以選擇要升級的資源，作為此手動升級的一部分。 **啟動升級嚮導**。

![影像](/help/user-guide/assets/launches-images/launches-e.png)

1. 您可以啟用或禁用在生產後刪除啟動的選項。
1. 可以設定 **範圍** 選項：
   1. **促進全面啟動**:啟動的所有頻道都在設定的即時日期進行升級。
   1. **升級修改的頁面**:將只升級修改的啟動資源。 建議在不需要啟動審閱時使用此選項。
   1. **升級已批准的頁面**:此選項要求啟動批准工作流在啟動渠道上運行。 在設定的即時日期僅升級已批准的頁面。
   1. **提升當前頁面**:此選項要求啟動審批工作流僅為當前頁面運行。
1. 按一下 **下一個** 的 **升級啟動** 的子菜單。
1. 按一下 **提升** 來推動發射。

### 刪除螢幕啟動 {#deleting-the-screens-launch}

您可以使用 **刪除啟動** 的 **掛起的啟動** 的子菜單。

>[!CAUTION]
>
>此操作還將刪除所有子體（嵌套啟動）。

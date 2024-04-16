---
title: 使用Screens啟動項更新內容
description: 瞭解如何建立未來版本的管道（稱為Launch），並設定啟動專案的上線日期，讓內容在裝置或播放器上線。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Launches
role: Admin, Developer
level: Intermediate
exl-id: b610e5dd-e0c6-45e6-bf9b-27be2054bc8f
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '1556'
ht-degree: 0%

---

# 使用Screens啟動項更新內容 {#launches}

內容作者可建立管道的未來版本，稱為 **畫面啟動** 並進一步設定此啟動的上線日期。 這可讓內容在指定的上線日期在裝置或播放器中上線。

在的協助下 ***畫面啟動***，作者可預覽啟動項中的每個管道，且應能起始檢閱請求。 核准者群組取得通知，可以核准或拒絕要求。 當到達上線日期時，內容會在裝置播放。

例如，如果作者想要建立未來版本的c1、c2 （管道），則會建立啟動並設定上線日期（例如11月10日上午8:00）。 內容中的任何其他更新都會寄出以供檢閱。

在核准後並在上線日期（11月10日上午8:00）上，此啟動會在裝置或播放器上播放內容。

## 要求 {#requirements}

開始使用之前 *畫面啟動* 在AEM Screens專案中，請務必瞭解寬限期的概念及其相關性。

在設定的上線日期在播放器上執行體驗涉及：

* 啟動項促銷活動（通常需要幾秒鐘）。

* 發佈資源到發佈執行個體（通常需要幾分鐘的時間，視必須發佈的管道或資產大小而定）。

* 更新離線內容完成所花費的時間（通常需要幾分鐘）。

* 播放器從發佈例項下載內容所花的時間（通常需要幾分鐘的時間，視必須下載的資產頻寬和大小而定）。

* 伺服器和播放器的任何時間差異。

### 瞭解寬限期 {#understanding-grace-period}

為了讓播放器能夠在設定的上線日期開始播放內容，請在上線日期之前開始進行先前的活動。

如果上線日期為 *11月24日，上午9點* 寬限期為 *24小時*，則上述動作順序將於（上線日期 — 寬限期）開始，即11月23日伺服器時間上午9:00。 這可讓內容24小時完成上述所有動作，以便連絡播放器。 播放器瞭解這是啟動內容。 因此，內容不會立即播放，但播放器可將此內容儲存為未來版本，並讓內容在播放器時區的設定上線日期完全開始播放。

例如，伺服器位於PST，而裝置位於EST。 在此案例中，最大時間差異為3小時，並假設促銷活動需要1分鐘，且從作者發佈到發佈需要10分鐘，播放器通常可在10至15分鐘內下載資源。 然後寬限期=時間差異（三個小時）：

* 加上提升啟動項的時間（1分鐘）
* 加上發佈啟動項的時間（10分鐘）
* 加上在播放器下載的時間（10-15分鐘）
* 加上緩衝（30分鐘）

等於3小時56分鐘(14160秒)。

因此，每當您排程任何即時啟動時，促銷活動都會在此位移處提早開始。 在上述方程式中，大多數專案不會花費太多時間。 知道伺服器和任何播放器之間的最大時間差異時，您可以針對此位移使用適當的猜測。

>[!NOTE]
>
>現成可用的Screens Launch寬限期設為24小時。 這表示當您為底下的資源設定任何啟動專案的上線日期時 */content/screens*，促銷活動會從此位移開始。

### 更新立即可用的寬限期 {#updating-out-of-the-box-grace-period}

本節說明如何將現成可用的寬限期更新為10分鐘。

1. 導覽至「CRXDE Lite」，然後導覽至 `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
1. 按一下滑鼠右鍵並複製檔案。
1. 瀏覽至 `/apps/system/config` 然後按一下右鍵並貼上。
1. 按兩下 `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` 以便您在編輯器中以CRXDE Lite開啟檔案。 它必須顯示路徑的寬限期 */content/screens/* 作為 **86400**. 將該值變更為 **600**.

現在，文字檔案中的內容看起來應該類似於：

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

由於您在上一個範例中將寬限期設為10分鐘，因此當您為下的資源設定任何啟動的上線日期時， */content/screens*，促銷活動會從此位移開始。

例如，如果上線日期設為11月24日上午9:00，而寬限期為600秒，則促銷工作會於11月24日上午8:50開始。

## 使用Screens啟動項 {#using-launches}

本節示範如何在AEM Screens專案中實施Screens Launch。

### 建立畫面啟動項 {#creating-a-launch}

請依照下列步驟，將Screens Launch功能實施至您的AEM Screens專案：

1. 例如，在您的AEM Screens專案中建立順序頻道 **LaunchDemo** > **頻道** > **Futurelaunch**，如下所示。

   >[!CAUTION]
   >
   >從您AEM Screens專案中現有的頻道建立啟動。

   ![影像](/help/user-guide/assets/launches-images/launches-11.png)

1. 按一下頻道 **Futurelaunch** 並按一下 **建立啟動項** 從動作列移除。

   ![影像](/help/user-guide/assets/launches-images/launches-12.png)

1. 此 **建立啟動項** 精靈開啟。 您可以按一下已在精靈中顯示的管道，或按一下 **+新增頻道** ，以新增您要建立啟動項的管道。

1. 按一下 **下一個** 從 **建立啟動項** 精靈。 此 **包含子頁面** 選項預設為選取。

   ![影像](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >您可以使用 **+新增頻道** 用於新增另一個要為其建立啟動項的管道的選項。

   使用 **新增頻道** 選項，導覽至您要建立啟動項的頻道，然後按一下 **選取**.

   此 **選取** 如果您嘗試按一下多個管道或資料夾以新增啟動項，選項會停用。

   ![影像](/help/user-guide/assets/launches-images/launches-14.png)

   按一下通道/通道後，按一下 **下一個**.


1. 輸入 **啟動項標題** 作為 **SummerPromotions** 而且您不需要設定 **啟動日期**，如下圖所示。 按一下&#x200B;**建立**。

   >[!NOTE]
   >
   >*啟用或檢查* 選項 **繼承來源頁面即時資料** 允許將頻道建立為啟動項中的即時副本。 如果在原始頻道中進行了任何變更，這些變更會自動套用至啟動頻道。
   >
   >
   >*停用或取消核取* **繼承來源頁面即時資料** 允許複製管道，而啟動項中沒有任何即時關係。 因此，如果對原始頻道進行任何變更，這些變更不會套用至啟動頻道。

   ![影像](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >您可以在此步驟中設定即時啟動日期，也可以在稍後編輯啟動項的屬性時，在建立啟動項後進行設定。

   **瞭解啟動項促銷活動範圍**

   * **提升完整啟動項**  — 啟動項的所有管道會在設定的上線日期提升。
   * **提升已修改的頁面**  — 只會提升已修改的啟動資源。 在不需要啟動檢閱時使用此選項。
   * **推廣已核准的頁面**  — 此選項需要在啟動管道上執行啟動核准工作流程。 只有核准的頁面會在設定的上線日期提升。

     >[!CAUTION]
     >
     >啟動的上線日期依照播放器/裝置的時區，而非伺服器的時區。

1. 請注意，您的啟動項已建立。 您可以按一下 **開啟** 在編輯器中檢視頁面，或按一下 **完成** 以導覽回您的專案。

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   選取 **完成** 可讓您導覽回 **Futurelaunch** 頻道。

   ![影像](/help/user-guide/assets/launches-images/launches-16.png)


### 編輯啟動項屬性以設定上線日期和範圍 {#editing-the-launch-properties-to-set-the-live-date-and-scope}

建立啟動後，您可以使用更新屬性，例如上線日期、啟動標題和促銷活動範圍 **啟動項屬性**.

* **啟動日期**  — 上線日期，也就是內容根據播放器的時區在Screens播放器中播放的日期或時間。
* **生產就緒**  — 允許在提升管道後發佈管道，這會立即啟用，因此不需要變更。
* **範圍**  — 決定在啟動項促銷活動期間促銷哪些管道。

請依照下列步驟編輯啟動項屬性：

1. 導覽至該管道 **Futurelaunch** *（啟動項等待處理中）*，然後按一下頻道，如下圖所示。

   ![影像](/help/user-guide/assets/launches-images/launches-17.png)

1. 按一下 **儀表板** 從動作列中，您會看到 **啟動專案等待處理中** 面板進行修改。

   ![影像](/help/user-guide/assets/launches-images/launches-18.png)

1. 按一下啟動，然後按一下 **啟動項屬性** 從 **啟動專案等待處理中** 面板。

   ![影像](/help/user-guide/assets/launches-images/launches-19.png)

### 編輯畫面啟動以新增或移除頻道  {#editing-the-screens-launch-to-add-or-remove-channels}

建立啟動後，您可以使用將管道新增或移除至現有的啟動 **編輯啟動項** 選項。

完成後，按一下 **儲存** 以導覽回 **Futurelaunch** 頻道。

### 手動提升畫面啟動{#promote-the-screens-launch-manually}

您可以使用手動提升啟動 **`Promote Launch`** 選項來自 **啟動專案等待處理中** 面板。

您可以選擇要促銷的資源，作為此手動促銷的一部分，位於 **啟動項提升精靈**.

![影像](/help/user-guide/assets/launches-images/launches-e.png)

1. 您可以啟用或停用在生產後刪除啟動項的選項。
1. 您可以設定 **範圍** ，並提供下列選項：
   * **提升完整啟動項**  — 啟動項的所有管道會在設定的上線日期提升。
   * **提升已修改的頁面**  — 只會提升已修改的啟動資源。 在不需要啟動檢閱時使用此選項。
   * **推廣已核准的頁面**  — 此選項需要在啟動管道上執行啟動核准工作流程。 只有核准的頁面會在設定的上線日期提升。
   * **提升目前頁面**  — 此選項會要求啟動核准工作流程只對目前頁面執行。
1. 按一下 **下一個** 在 **提升啟動** 精靈。
1. 按一下 **提升** 以提升啟動。

### 刪除畫面啟動項

您可以使用以下方式刪除啟動 **刪除啟動項** 選項來自 **啟動專案等待處理中** 面板。

>[!CAUTION]
>
>此動作也會刪除所有下階（巢狀啟動）。

---
title: 使用Screens Launch更新內容
seo-title: 使用Screens Launch更新內容
description: 內容作者可建立未來版本的頻道（稱為Launch），並進一步設定此次啟動的上線日期，讓內容可在裝置或播放器中上線。
seo-description: 內容作者可建立未來版本的頻道（稱為Launch），並進一步設定此次啟動的上線日期，讓內容可在裝置或播放器中上線。
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
feature: 製作畫面、啟動
role: Admin, Developer
level: Intermediate
exl-id: b610e5dd-e0c6-45e6-bf9b-27be2054bc8f
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1619'
ht-degree: 0%

---

# 使用Screens Launch更新內容 {#launches}

內容作者可建立未來版本的頻道，稱為&#x200B;**Screens Launch**，並進一步設定此次啟動的上線日期。 這可讓內容在指定上線日期的裝置或播放器中上線。

在&#x200B;***Screens Launch***&#x200B;的協助下，作者可以預覽啟動中的每個管道，並應能起始要求檢閱的請求。 批准者組將獲得通知，並可以批准或拒絕請求。 達到即時日期時，內容會在裝置中播放。

例如，如果作者想要建立c1、c2（管道）的未來版本，則會建立啟動並設定即時日期（例如，上午11月10日8:00）。 內容中的任何進一步更新都會寄出以供審核。

核准後且在上線日期（11月10日上午8:00），此次啟動會在裝置或播放器上播放內容。

## 需求 {#requirements}

開始在AEM Screens專案中運用&#x200B;*Screens Launch*&#x200B;之前，請務必了解寬限期的概念及其相關性。

在播放器上以設定的上線日期執行體驗，包括：

* 促銷啟動（通常需要幾秒鐘）

* 發佈資源以發佈例項（通常需要幾分鐘，視需要發佈的管道或資產大小而定）

* 更新離線內容完成所花的時間（通常需要幾分鐘）

* 播放器從發佈執行個體下載內容所花費的時間（通常需要數分鐘，視需要下載的資產頻寬和大小而定）

* 伺服器和播放器的任何時間差異

### 了解寬限期 {#understanding-grace-period}

為了讓播放器能夠在設定的即時日期開始播放內容，我們必須在即時日期之前開始先前的活動。

如果上線日期為&#x200B;*11月24日，上午9:00(a1/)，寬限期為* 24小時&#x200B;*，則上述動作順序將從（上線日期 — 寬限期）開始，即11月23日，上午9:00（伺服器時間）。*&#x200B;這可提供24小時的時間來完成上述所有動作，而內容將可送達播放器。 播放器會了解這是啟動內容，因此內容不會立即播放，但播放器會將此內容儲存為未來版本，並會在播放器時區的設定即時日期完全開始播放。

例如，假設伺服器位於PST中而裝置位於EST中，在此情況下，最大時差為3小時，並假設從作者進行促銷需要1分鐘，而從作者進行發佈發佈需要10分鐘，而播放器通常可在10-15分鐘內下載資源。 然後寬限期=時差（3小時）+促銷啟動的時間（1分鐘）+發佈啟動的時間（10分鐘）+在播放器下載的時間（10-15分鐘）+緩衝區（安全起見，假設30分鐘）= 3小時56分鐘=14160秒。

因此，每當我們排程任何上線啟動時，促銷活動都會在此偏移處提前開始。 在上述方程式中，大部分項目不需要太多時間，只要知道伺服器與任何播放器之間的最大時間差，我們就可以對此偏移使用適當的猜測。

>[!NOTE]
>
>現成可用的Screens Launch寬限期設為24小時，這表示當我們為&#x200B;*/content/screens*&#x200B;下的資源設定任何啟動的上線日期時，促銷活動將從此位移開始。

### 更新現成的寬限期 {#updating-out-of-the-box-grace-period}

本節說明如何將現成可用的寬限期更新至10分鐘。

1. 導覽至CRXDE Lite，然後導覽至`/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`。
2. 以滑鼠右鍵按一下並複製檔案。
3. 導覽至`/apps/system/config`，然後按一下滑鼠右鍵並貼上。
4. 按兩下`/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`以在CRXDE Lite的編輯器中開啟檔案。 它必須將路徑&#x200B;*/content/screens/*&#x200B;的寬限期顯示為&#x200B;**86400**。 將該值變更為&#x200B;**600**。

現在，文字檔案中的內容看起來應該類似：

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

由於您已在上個範例中將寬限期設為10分鐘，因此當您為&#x200B;*/content/screens*&#x200B;下的資源設定任何啟動的上線日期時，促銷將會以此位移開始。

例如，如果上線日期設為11月24日，上午9:00，寬限期為600秒，則促銷工作將於11月24日上午8:50開始。

## 使用Screens Launch {#using-launches}

本節示範如何在您的AEM Screens專案中實作Screens Launch。

### 建立Screens Launch {#creating-a-launch}

請依照下列步驟，將Screens Launch功能實施至您的AEM Screens專案：

1. 在您的AEM Screens專案中建立序列管道，例如&#x200B;**LaunchesDemo** —> **Channels** —> **FutureLaunch**，如下所示。

   >[!CAUTION]
   >
   >您必須從AEM Screens專案中預先存在的管道建立啟動。

   ![影像](/help/user-guide/assets/launches-images/launches-11.png)

1. 選取通道&#x200B;**FutureLaunch**，然後從動作列按一下&#x200B;**Create Launch**。

   ![影像](/help/user-guide/assets/launches-images/launches-12.png)

1. 將開啟&#x200B;**建立啟動**&#x200B;精靈。 您可以選取精靈中已顯示的通道，或按一下「**+新增通道**」以新增您要建立啟動的通道。

1. 從&#x200B;**建立Launch**&#x200B;精靈中按一下&#x200B;**Next**。 預設會選取&#x200B;**包含子頁面**&#x200B;選項。

   ![影像](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >您可以使用&#x200B;**+新增管道**&#x200B;選項，新增您要為其建立啟動的其他管道。

   若要使用&#x200B;**新增頻道**&#x200B;選項，請導覽至您要為其建立啟動的頻道，然後按一下&#x200B;**選取**。

   如果您嘗試選取多個頻道或資料夾以新增啟動，則會停用&#x200B;**選取**&#x200B;選項。

   ![影像](/help/user-guide/assets/launches-images/launches-14.png)

   選取通道/通道後，按一下「**Next**」。


1. 輸入&#x200B;**Launch Title**&#x200B;作為&#x200B;**SummerPromotions**，您不需要設定&#x200B;**Launch Date**，如下圖所示。 按一下&#x200B;**建立**。

   >[!NOTE]
   >
   >*啟用或* 勾選「繼 **承來源頁面即時** 資料」選項，即可在啟動中將管道建立為即時副本。如果在原始管道中進行任何變更，這些變更會自動套用至啟動管道。
   >
   >
   >*禁用或* **取消勾選Inherit源頁** 面即時資料允許在啟動中複製通道，而不與任何即時關係。因此，如果對原始管道進行任何變更，這些變更不會套用至啟動管道。

   ![影像](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >您可以在此步驟中設定即時啟動日期，或稍後在編輯啟動的屬性（一旦建立）時進行設定。

   **了解Launch促銷範圍**

   * **促銷完整啟動**:啟動的所有管道都會在設定的上線日期升級。
   * **提升修改的頁面**:只會升級已修改的啟動資源。若不需要啟動審核，建議您使用此選項。
   * **提升已核准的頁面**:此選項需要在啟動管道上執行啟動核准工作流程。只有已核准的頁面才會在設定的上線日期升級。

      >[!CAUTION]
      >
      >啟動上線日期會遵循播放器/裝置的時區，而非伺服器的時區。

1. 您會看到啟動已建立。 您可以按一下&#x200B;**開啟**&#x200B;以檢視編輯器中的頁面，或按一下&#x200B;**完成**&#x200B;以導覽回您的專案。

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   按一下&#x200B;**Done**&#x200B;可讓您導覽回&#x200B;**FutureLaunch**&#x200B;頻道。

   ![影像](/help/user-guide/assets/launches-images/launches-16.png)


### 編輯啟動屬性以設定上線日期和範圍 {#editing-the-launch-properties-to-set-the-live-date-and-scope}

建立啟動後，您可以使用&#x200B;**Launch屬性**&#x200B;更新即時日期、啟動標題和促銷範圍等屬性。

* **啟動日期**，是指上線日期，即內容在Screens播放器中播放的日期或時間（根據播放器的時區）。
* **生產就緒**，可讓管道在促銷這些已啟用的現成可用功能後發佈，因此不需要變更。
* **範圍**，決定在啟動促銷期間要促銷的管道。


請依照下列步驟編輯啟動屬性：

1. 導覽至通道&#x200B;**FutureLaunch**、*（即待定啟動）*&#x200B;並選取通道，如下圖所示。

   ![影像](/help/user-guide/assets/launches-images/launches-17.png)

1. 按一下動作列中的&#x200B;**控制面板**，您會從通道控制面板看到&#x200B;**待定啟動**&#x200B;面板。

   ![影像](/help/user-guide/assets/launches-images/launches-18.png)

1. 選取啟動，然後從&#x200B;**待定啟動**&#x200B;面板按一下&#x200B;**啟動屬性**。

   ![影像](/help/user-guide/assets/launches-images/launches-19.png)

### 編輯畫面Launch以新增或移除頻道  {#editing-the-screens-launch-to-add-or-remove-channels}

建立啟動後，您可以使用&#x200B;**編輯啟動**&#x200B;選項，將通道新增或移除至現有啟動。

完成後，按一下&#x200B;**Save**&#x200B;以導覽回&#x200B;**FutureLaunch**&#x200B;頻道。

### 手動提升Screens Launch{#promote-the-screens-launch-manually}

您可以使用&#x200B;**待定啟動**&#x200B;面板中的&#x200B;**促銷啟動**&#x200B;選項，手動促銷啟動。

您可以在&#x200B;**啟動促銷精靈**&#x200B;中，選擇要促銷的資源，作為此手動促銷的一部分。

![影像](/help/user-guide/assets/launches-images/launches-e.png)

1. 您可以啟用或停用在生產後刪除啟動的選項。
1. 您可以使用下列選項設定啟動的&#x200B;**範圍**:
   1. **促銷完整啟動**:啟動的所有管道都會在設定的上線日期升級。
   1. **提升修改的頁面**:只會升級已修改的啟動資源。若不需要啟動審核，建議您使用此選項。
   1. **提升已核准的頁面**:此選項需要在啟動管道上執行啟動核准工作流程。只有已核准的頁面才會在設定的上線日期升級。
   1. **提升目前頁面**:此選項需要啟動核准工作流程才能針對目前頁面執行。
1. 在&#x200B;**Promote Launch**&#x200B;精靈中，按一下&#x200B;**Next**。
1. 按一下&#x200B;**Promote**&#x200B;以促銷啟動。

### 刪除Screens Launch {#deleting-the-screens-launch}

您可以使用&#x200B;**刪除啟動**&#x200B;選項，從&#x200B;**待定啟動**&#x200B;面板中刪除啟動。

>[!CAUTION]
>
>此動作也會刪除所有子系（巢狀啟動）。

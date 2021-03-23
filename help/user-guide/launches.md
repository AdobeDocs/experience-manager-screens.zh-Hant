---
title: 使用畫面啟動來更新內容
seo-title: 使用畫面啟動來更新內容
description: 內容作者可建立頻道的未來版本，稱為「啟動」，並進一步設定此次啟動的即時日期，讓內容可在裝置或播放器中即時顯示。
seo-description: 內容作者可建立頻道的未來版本，稱為「啟動」，並進一步設定此次啟動的即時日期，讓內容可在裝置或播放器中即時顯示。
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
feature: 編寫螢幕、啟動
role: 管理員、開發人員
level: 中級
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1622'
ht-degree: 0%

---


# 使用畫面啟動{#launches}進行內容更新

內容作者可建立頻道的未來版本，稱為&#x200B;**Screens Launch**，並進一步設定此次啟動的即時日期。 這可讓內容在指定的即時日期在裝置或播放器中即時顯示。

在&#x200B;***Screens Launch***&#x200B;的協助下，作者可以預覽啟動中的每個頻道，並可以開始要求檢閱。 批准者群組會收到通知，並可核准或拒絕請求。 到達即時日期時，內容會在裝置中播放。

例如，如果作者想要建立c1、c2（頻道）的未來版本，則會建立啟動並設定即時日期（例如，11月10日上午8:00）。 內容中的任何更新都會送出供您檢閱。

核准後即可上線（11月10日上午8:00），此次啟動會在裝置或播放器上播放內容。

## 要求{#requirements}

在您開始在AEM Screens專案中運用&#x200B;*Screens Launch*&#x200B;之前，請務必瞭解寬限期的概念及其相關性。

在播放器的設定即時日期上執行體驗，包括：

* 啟動的促銷（通常需要幾秒鐘）

* 發佈資源以發佈例項（通常需要幾分鐘的時間，視需要發佈的頻道或資產大小而定）

* 更新離線內容完成所花的時間（通常需要幾分鐘）

* 播放器從發佈例項下載內容所花的時間（通常需要幾分鐘的時間，視需要下載的資產頻寬和大小而定）

* 伺服器與播放器的任何時間差異

### 瞭解寬限期{#understanding-grace-period}

為了讓播放器能夠在設定的即時日期開始播放內容，我們需要在即時日期之前開始前述活動。

如果即時日期為&#x200B;*11月24日，9:00 AM*，寬限期為&#x200B;*24小時*，則上述動作順序將從（即時日期——寬限期）開始，即11月23日9:00 AM伺服器時間。 這可讓24小時時間完成上述所有動作，而內容將傳達給播放器。 播放器會瞭解這是啟動內容，因此內容不會立即播放，但播放器會將此內容儲存為未來版本，並會在播放器時區的設定即時日期開始播放。

例如，假設伺服器在PST中，裝置在EST中，此時最大時差為3小時，並假設促銷需要1分鐘，而從作者發佈需要10分鐘，而播放器通常可在10-15分鐘內下載資源。 然後寬限期=時間差（3小時）+提升啟動（1分鐘）的時間+發佈啟動（10分鐘）的時間+在播放器下載（10-15分鐘）+緩衝區（安全，例如30分鐘）= 3小時56分鐘= 14160秒。

因此，每當我們排程任何即時啟動時，促銷活動都會以此偏移提前開始。 在上述等式中，大部分項目不需要太多時間，只要我們知道伺服器與任何播放器之間的最大時間差，我們就可對此偏移量使用適當的猜測。

>[!NOTE]
>
>現成可用，「畫面啟動」的寬限期會設為24小時，這表示當我們在&#x200B;*/content/screens*&#x200B;下設定資源啟動的即時日期時，促銷會從此偏移開始。

### 更新現成可用的寬限期{#updating-out-of-the-box-grace-period}

本節說明如何將現成可用的寬限期更新為10分鐘。

1. 導覽至CRXDE Lite，然後導覽至`/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`。
2. 按一下右鍵並複製檔案。
3. 導覽至`/apps/system/config`，然後按一下滑鼠右鍵並貼上。
4. 連按兩下`/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`，在CRXDE Lite的編輯器中開啟檔案。 它必須將路徑&#x200B;*/content/screens/*&#x200B;的寬限期顯示為&#x200B;**86400**。 將該值更改為&#x200B;**600**。

現在，文字檔案中的內容看起來應該類似：

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

由於您已在上例中將寬限期設為10分鐘，因此當您在&#x200B;*/content/screens*&#x200B;下為資源的任何啟動設定即時日期時，促銷將以此偏移開始。

例如，如果即時日期設為11月24日、9:00 AM且寬限期為600秒，促銷工作將於11月24日上午8:50開始。

## 使用畫面啟動{#using-launches}

本節將示範如何在您的AEM Screens專案中實作畫面啟動。

### 建立畫面啟動{#creating-a-launch}

請依照下列步驟，將Screens Launch功能實作至您的AEM Screens專案：

1. 在您的AEM Screens專案中建立序列頻道，例如&#x200B;**LaunchesDemo** —> **Channels** —> **FutureLaunch**，如下所示。

   >[!CAUTION]
   >
   >您必須在AEM Screens專案中從預先存在的渠道建立啟動。

   ![影像](/help/user-guide/assets/launches-images/launches-11.png)

1. 選取頻道&#x200B;**FutureLaunch**，然後從動作列按一下「建立啟動&#x200B;**」。**

   ![影像](/help/user-guide/assets/launches-images/launches-12.png)

1. 將開啟&#x200B;**建立啟動**&#x200B;嚮導。 您可以選取精靈中已顯示的頻道，或按一下「新增頻道」**+以新增您要建立啟動的頻道。**

1. 從&#x200B;**建立啟動精靈按一下** Next **。**&#x200B;預設會選取「包含子頁面&#x200B;**」選項。**

   ![影像](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >您可以使用&#x200B;**+ 「新增頻道」**&#x200B;選項來新增另一個您要為其建立啟動的頻道。

   要使用&#x200B;**添加渠道**&#x200B;選項，請導航到要為其建立啟動的渠道，然後按一下&#x200B;**選擇**。

   如果您嘗試選取多個頻道或資料夾以新增啟動，**Select**&#x200B;選項將會停用。

   ![影像](/help/user-guide/assets/launches-images/launches-14.png)

   選擇通道／通道後，按一下&#x200B;**Next**。


1. 將&#x200B;**啟動標題**&#x200B;輸入為&#x200B;**SummerPromotions**，而您不需要設定&#x200B;**啟動日期**，如下圖所示。 按一下&#x200B;**建立**。

   >[!NOTE]
   >
   >*啟用或* 勾選「繼 **承來源頁面即時** 資料」選項，可讓頻道在啟動中建立為即時副本。如果在原始渠道中進行任何變更，這些變更會自動套用至啟動渠道。
   >
   >
   >*停用或* **取消勾選繼承來源頁** 面即時資料可讓頻道在啟動時複製，而不需任何即時關係。因此，如果對原始渠道進行任何變更，這些變更不會套用至啟動渠道。

   ![影像](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >您可以在此步驟中設定即時啟動日期，或在啟動建立後編輯其屬性時稍後加以設定。

   **瞭解啟動促銷範圍**

   * **促銷完整啟動**:啟動的所有頻道都會在設定的即時日期進行促銷。
   * **升級修改的頁面**:只會升級已修改的啟動資源。建議在不需要啟動檢視時使用此選項。
   * **促銷已核准的頁面**:此選項需要啟動核准工作流程才能在啟動渠道上執行。只有已核准的頁面才會在設定的即時日期升級。

      >[!CAUTION]
      >
      >啟動即時日期會遵循播放器／裝置的時區，而非伺服器的時區。

1. 您會看到啟動已建立。 您可以按一下&#x200B;**Open**&#x200B;在編輯器中檢視頁面，或按一下&#x200B;**Done**&#x200B;返回專案。

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   按一下&#x200B;**Done**&#x200B;可讓您返回至&#x200B;**FutureLaunch**&#x200B;頻道。

   ![影像](/help/user-guide/assets/launches-images/launches-16.png)


### 編輯啟動屬性以設定即時日期和範圍{#editing-the-launch-properties-to-set-the-live-date-and-scope}

在建立啟動後，您可以使用&#x200B;**啟動屬性**&#x200B;來更新屬性，例如即時日期、啟動標題和促銷範圍。

* **啟動日期**，是指即時日期，即內容將依播放器時區在螢幕播放器中播放的日期或時間。
* **Production Ready**，可讓頻道在促銷這些已啟用的現成可用功能後發佈，因此不需要變更。
* **範圍**，決定在啟動促銷期間要推廣哪些渠道。


請依照下列步驟編輯啟動屬性：

1. 導覽至渠道&#x200B;**FutureLaunch**、*（即待定啟動）*&#x200B;並選取渠道，如下圖所示。

   ![影像](/help/user-guide/assets/launches-images/launches-17.png)

1. 按一下動作列中的&#x200B;**Dashboard**，您就會看到頻道控制面板中的&#x200B;**PENDING LAUNCHES**&#x200B;面板。

   ![影像](/help/user-guide/assets/launches-images/launches-18.png)

1. 選擇啟動，然後從&#x200B;**待定啟動**&#x200B;面板按一下&#x200B;**啟動屬性**。

   ![影像](/help/user-guide/assets/launches-images/launches-19.png)

### 編輯畫面啟動以新增或移除頻道{#editing-the-screens-launch-to-add-or-remove-channels}

建立啟動後，您可使用&#x200B;**編輯啟動**&#x200B;選項，將頻道新增或移除至現有的啟動。

完成後，按一下&#x200B;**Save**&#x200B;返回&#x200B;**FutureLaunch**&#x200B;頻道。

### 手動升級畫面啟動{#promote-the-screens-launch-manually}

您可以使用&#x200B;**待定啟動**&#x200B;面板中的&#x200B;**提升啟動**&#x200B;選項手動提升啟動。

在&#x200B;**啟動升級嚮導**&#x200B;中選擇要升級的資源，作為此手動升級的一部分。

![影像](/help/user-guide/assets/launches-images/launches-e.png)

1. 您可以啟用或停用在生產後刪除啟動的選項。
1. 您可以使用下列選項來設定啟動的&#x200B;**Scope**:
   1. **促銷完整啟動**:啟動的所有頻道都會在設定的即時日期進行促銷。
   1. **升級修改的頁面**:只會升級已修改的啟動資源。建議在不需要啟動檢視時使用此選項。
   1. **促銷已核准的頁面**:此選項需要啟動核准工作流程才能在啟動渠道上執行。只有已核准的頁面才會在設定的即時日期升級。
   1. **提升目前頁面**:此選項需要啟動核准工作流程才能執行至目前頁面。
1. 在&#x200B;**升級啟動嚮導中按一下** Next **。**
1. 按一下&#x200B;**Promote**&#x200B;以提升啟動。

### 刪除畫面啟動{#deleting-the-screens-launch}

您可以使用&#x200B;**從**&#x200B;待定啟動&#x200B;**面板中的「刪除啟動**」選項來刪除啟動。

>[!CAUTION]
>
>此動作也會刪除所有子系（巢狀啟動）。


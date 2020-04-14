---
title: 文字重疊
seo-title: 文字重疊
description: 「文字覆蓋」是AEM Screens中提供的功能，可讓您在「序列頻道」中提供覆蓋在影像上方的標題或描述，以建立引人入勝的體驗。 請依本頁瞭解詳細資訊。
seo-description: 「文字覆蓋」是AEM Screens中提供的功能，可讓您在「序列頻道」中提供覆蓋在影像上方的標題或描述，以建立引人入勝的體驗。 請依本頁瞭解詳細資訊。
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
translation-type: tm+mt
source-git-commit: 651627223e1b9bd0f650b010d2b92f004b9e2ea2

---


# 文字重疊 {#text-overlay}

本節涵蓋下列主題：

* **概覽**
* **使用文字覆蓋**
* **瞭解文字覆蓋屬性**
* **在文字覆蓋中使用ContextHub值**

>[!CAUTION]
>
>只有在 **您已安裝AEM 6.3 Feature Pack 5或AEM 6.4 Feature Pack 3時，「文字覆蓋** 」功能才可用。

## 概覽 {#overview}

「文字覆蓋」是AEM Screens中提供的功能，可讓您在「序列頻道」中提供覆蓋在影像上方的標題或描述，以建立引人入勝的體驗。

若要瞭解如何建立您自己的自訂元件，請參閱「 **擴充AEM畫面元件」**。

本節僅展示如何在AEM Screens專案中使用和運用海報元件，並將它當做序列頻道中的文字覆蓋。

## 使用文字覆蓋 {#using-text-overlay}

下節說明在AEM Screens專案中使用文字覆蓋的情形。

**必備條件**

開始實作此功能之前，請確定您已將專案設定為開始實作文字覆蓋的先決條件。 例如，

* 建立AEM Screens專案(在此範例中為 **TextOverlayDemo**)

* 在「頻道」檔案夾下建立名為 **TextSample** 的序 **列頻道** 。

* 將內容新增至 **TextSample** Channel

下圖顯示TextOverlayDemo專 **案，其中** TextSample頻道位於「頻道」資 **料夾中****** 。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

請依照下列步驟，在AEM Screens頻道中使用文字覆蓋：

1. 導覽至 **TextOverlayDemo** —> **Channels** —> **TextSample** ，然後按一下 **** EditExt從動作列開啟編輯器。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 選取影像，然後按一下「 **設定** （扳手圖示）」以開啟屬性對話方塊。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 從對話 **方塊的導覽列中選取「文字覆蓋** 」選項，如下圖所示。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 瞭解文字覆蓋屬性 {#understanding-text-overlay-properties}

使用「文字覆蓋」屬性，您可以將文字新增至「畫面」專案中的任何元件。 下節提供「文字覆蓋」中可用屬性的概述：

![文字](assets/text.gif)

您可以在文字方塊中新增文字，並新增排版強調，例如粗體、斜體、底線等。

**顏色變異** ：此選項允許文字為「深色」（黑色文字）或「淺色」（白色文字）。

**調整大小和定位** ：此選項可讓使用者水準或垂直對齊文字，或另外使用精細的工具來對齊文字。

>[!NOTE]
>
>若要正確使用精密的工具，請務必使用(px)做為字尾，例如200px，以像素為單位識別正確的位置。 此運算式的結果是從起點開始200像素。

## 在文字覆蓋中使用ContextHub值 {#using-text-overlay-context-hub}

下節說明資料儲存區中值的使用，例如文字覆蓋元件中的google工作表。

**必備條件**

您必須為AEM Screens專案設定ContextHub組態。

若要瞭解如何使用資料存放區來設定及管理資料導向的資產變更，請參閱「在AEM畫 [面中設定ContextHub](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/developing/configuring-context-hub.html)」。

在您設定專案所需的設定後，請依照下列步驟，使用google工作表中的值：

1. 導覽至 **TextOverlayDemo** —> **Channels** —> **Sample** text並從動作列 **** 按一下Properties。

1. 選擇「個 **人化** 」標籤以設定ContextHub組態。

   1. 選擇ContextHub路徑 **,** 作為libs **>** settings **> Default Settings** > Default Zetings ****************> Configurations Journations CloudSelectLoudLouds。

   1. 選擇Path **conf** (路徑 **)** >螢幕設定 **>** Settings（設定）> Wcm ****************> Lick Select Select的選段和LickLickSelect。

   1. 按一 **下儲存並關閉**。

      >[!NOTE]
      >
      >使用ContextHub和區段路徑，您最初在此儲存上下文中心組態和區段。

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 導覽至 **TextOverlayDemo** —> **Channels** —> **TextSample** ，然後按一下 **** EditExt從動作列開啟編輯器。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 如本頁「使用文字覆蓋」區段所述，將影像和文字覆蓋 [元件新增至影像](/help/user-guide/text-overlay.md#using-text-overlay) 。

1. 按一下「 **設定** （扳手圖示）」以開啟「 **影像** 」對話方塊。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 從「影像 **」對話方塊** ，導覽至 **ContextHub標籤** 。 按一下&#x200B;**「新增」**。

   >[!NOTE]
   >如果您尚未設定ContextHub組態，則專案的此選項將會停用。

1. 在 **Placeholder** 欄位中輸入Value **，在** Google Variable ************（本例中，從行2和列1中檢索值）中選擇要從Google工作表中獲取值的行，然後輸入Google Sheet中的Default Value Chandign Hub（如下圖所示）。 完成後，按一下複選標籤。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >以下影像會展示從google工作表擷取的值，供您參考：

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 從「影像」對 **話方塊導覽回「文字覆蓋」索引標籤，並新增「目前溫度{值****}」文字，如下圖所示。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 按一下「 **預覽** 」以檢視所要的輸出。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
















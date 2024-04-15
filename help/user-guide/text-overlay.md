---
title: 文字重疊
description: 瞭解AEM Screens中的文字覆蓋，其可讓您透過提供覆蓋在影像上的標題或說明，在序列頻道中建立引人入勝的體驗。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 1%

---

# 文字重疊 {#text-overlay}

本節涵蓋下列主題：

* **概觀**
* **使用文字覆蓋**
* **瞭解文字覆蓋屬性**
* **在文字覆蓋中使用ContextHub值**

>[!CAUTION]
>
>此 **文字覆蓋** 功能僅在您已安裝AEM 6.3 Feature Pack 5或AEM 6.4 Feature Pack 3時才可用。

## 概觀 {#overview}

文字覆蓋是AEM Screens中提供的功能，可讓您在序列頻道中提供覆蓋在影像上的標題或說明，以建立引人入勝的體驗。

若要瞭解如何建立自己的自訂元件，請參閱 **擴充AEM Screens元件**.

本節僅說明如何在AEM Screens專案中使用和套用海報元件，並在其中一個序列頻道中作為文字覆蓋使用。

## 使用文字覆蓋 {#using-text-overlay}

下節將說明如何在AEM Screens專案中使用文字覆蓋。

**必備條件**

在實作此功能之前，請確定您已設定專案作為開始實作文字覆蓋的先決條件。 例如，

* 建立AEM Screens專案(在此範例中， **TextOverlayDemo**)

* 建立標題為的順序頻道 **文字範例** 在 **頻道** 資料夾

* 將內容新增至 **文字範例** 頻道

下圖顯示 **TextOverlayDemo** 專案與 **文字範例** 中的頻道 **頻道** 資料夾。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

請依照下列步驟，在AEM Screens頻道中使用文字覆蓋：

1. 瀏覽至 **TextOverlayDemo** > **頻道** > **文字範例** 並選取 **編輯** 從動作列移除。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 選取影像並選取 **設定** （扳手圖示）以開啟「屬性」對話方塊。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 選取 **文字覆蓋** 對話方塊之導覽列中的選項，如下圖所示。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 瞭解文字覆蓋屬性 {#understanding-text-overlay-properties}

使用「文字覆蓋」屬性，您可以將文字新增至畫面專案中的任何元件。 下節會提供文字覆蓋中可用屬性的概觀：

![文字](assets/text.gif)

您可以將文字新增至文字方塊，並新增印刷強調文字，例如粗體、斜體和底線。

**顏色變體** 此選項允許文字為深色（黑色文字）或淺色（白色文字）。

**大小調整與定位** 此選項可讓使用者水平或垂直對齊文字，或是使用微調工具對齊文字。

>[!NOTE]
>
>若要正確使用微調工具，請務必以(px)做為尾碼來識別正確的畫素位置，例如200畫素。 此運算式的結果是從起點算起為200畫素。

## 在文字覆蓋中使用ContextHub值 {#using-text-overlay-context-hub}

下節將說明資料存放區中值的用法，例如，文字覆蓋元件中的Google工作表。

**必備條件**

為您的AEM Screens專案設定ContextHub設定。

若要瞭解如何使用資料存放區來設定和管理資料導向資產變更，請參閱 [在AEM Screens中設定ContextHub](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/configuring-context-hub).

在您設定專案所需的設定後，請依照下列步驟使用Google工作表中的值：

1. 瀏覽至 **TextOverlayDemo** > **頻道** > **文字範例** 並選取 **屬性** 從動作列移除。

1. 選取 **個人化** 標籤，讓您能夠設定ContextHub設定。

   1. 選取 **ContextHub路徑** 作為 **程式庫** > **設定** > **雲端設定** > **預設** > **ContextHub設定** 並選取 **選取**.

   1. 選取 **區段路徑** 作為 **conf** > **畫面** > **設定** > **wcm** > **區段** 並選取 **選取**.

   1. 選取「**儲存並關閉**」。

      >[!NOTE]
      >
      >使用ContextHub和區段路徑，您最初會在此儲存您的ContextHub設定和區段。

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 瀏覽至 **TextOverlayDemo** > **頻道** > **文字範例** 並選取 **編輯** 從動作列移除。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 將影像和文字覆蓋元件新增至您的影像，如所述 [使用文字覆蓋](/help/user-guide/text-overlay.md#using-text-overlay) 的區段。

1. 選擇於 **設定** （扳手圖示）開啟 **影像** 對話方塊。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 導覽至 **ContextHub** 標籤從 **影像** 對話方塊。 選取「**新增**」。

   >[!NOTE]
   >如果您尚未設定ContextHub組態，則會停用專案的此選項。

1. 輸入 **值** 在 **預留位置** 欄位。 選取您要從Google工作表取得值的列 **contexthub變數**. 在此情況下，值會從Google工作表中擷取自列2和欄1。 現在輸入 **預設值** 作為 **20**，如下圖所示。 完成後，選取核取記號。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >以下影像示範從Google工作表擷取的值，以供您參考：

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 導覽回 **文字覆蓋** 從「影像」對話方塊中選取索引標籤並新增文字 *目前溫度 {Value}*，如下圖所示。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 選取 **預覽**.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)

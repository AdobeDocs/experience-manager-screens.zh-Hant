---
title: 文字重疊
seo-title: Text Overlay
description: 文字覆蓋是AEM Screens提供的功能，可讓您提供覆蓋在影像上方的標題或說明，以在序列管道中建立引人入勝的體驗。 請詳閱本頁以了解更多。
seo-description: Text Overlay is a feature available in AEM Screens that allows you to create a compelling experience in a Sequence Channel by providing a title or a description overlaid on top of an image. Follow this page to learn more.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 2%

---

# 文字重疊 {#text-overlay}

本節涵蓋下列主題：

* **概覽**
* **使用文字覆蓋**
* **了解文字覆蓋屬性**
* **在文字覆蓋中使用ContextHub值**

>[!CAUTION]
>
>此 **文字覆蓋** 只有在您已安裝AEM 6.3 Feature Pack 5或AEM 6.4 Feature Pack 3時，才能使用。

## 總覽 {#overview}

文字覆蓋是AEM Screens提供的功能，可讓您提供覆蓋在影像上方的標題或說明，以在序列管道中建立引人入勝的體驗。

若要了解如何建立自己的自訂元件，請參閱 **擴充AEM Screens元件**.

本節只會展示如何在AEM Screens專案中使用和套用海報元件，以及在其中一個序列管道中作為文字覆蓋使用。

## 使用文字覆蓋 {#using-text-overlay}

下節說明在AEM Screens專案中使用文字覆蓋的方式。

**必備條件**

開始實作此功能之前，請務必先將專案設定為開始實作文字覆蓋的先決條件。 例如，

* 建立AEM Screens專案(在此範例中， **TextOverlayDemo**)

* 建立以為標題的序列管道 **TextSample** 在 **管道** 資料夾

* 將內容新增至 **TextSample** 管道

下圖顯示 **TextOverlayDemo** 專案 **TextSample** 頻道 **管道** 檔案夾。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

請依照下列步驟，在AEM Screens管道中使用文字覆蓋：

1. 導覽至 **TextOverlayDemo** —> **管道** —> **TextSample** 按一下 **編輯** 從動作列開啟編輯器。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 選取影像，然後按一下 **設定** （扳手圖示）以開啟「屬性」對話方塊。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 選取 **文字覆蓋** 選項，如下圖所示。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 了解文字覆蓋屬性 {#understanding-text-overlay-properties}

使用「文字覆蓋」屬性，您可以將文字新增至Screens專案中的任何元件。 下節提供文字覆蓋中可用屬性的概觀：

![text](assets/text.gif)

您可以在文字方塊中新增文字，並新增文字強調，例如粗體、斜體和底線。

**色彩變體** 此選項可讓文字變為「深色」（黑色文字）或「淺色」（白色文字）。

**大小調整和定位** 此選項可讓使用者水準或垂直對齊文字，或使用微調工具來對齊文字。

>[!NOTE]
>
>若要正確使用微調工具，請務必以(px)作為尾碼來識別正確的像素位置，例如200像素。 此運算式的結果是從起始點開始為200像素。

## 在文字覆蓋中使用ContextHub值 {#using-text-overlay-context-hub}

以下章節說明資料存放區中值的使用方式，例如文字覆蓋元件中的google工作表。

**必備條件**

為您的AEM Screens專案設定ContextHub設定。

若要了解如何使用資料存放區來設定及管理資料導向的資產變更，請參閱 [在AEM Screens中設定ContextHub](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

設定專案所需的設定後，請依照下列步驟使用google工作表中的值：

1. 導覽至 **TextOverlayDemo** —> **管道** —> **TextSample** 按一下 **屬性** 從動作列。

1. 選取 **個人化** 標籤來設定ContextHub設定。

   1. 選取 **ContextHub路徑** as **libs** > **設定** > **雲設定** > **預設** > **ContextHub設定** 按一下 **選擇**.

   1. 選取 **區段路徑** as **conf** > **螢幕** > **設定** > **wcm** > **區段** 按一下 **選擇**.

   1. 按一下&#x200B;**「儲存並關閉」**。

      >[!NOTE]
      >
      >使用ContextHub和區段路徑，您最初會在此儲存內容中樞設定和區段。

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 導覽至 **TextOverlayDemo** —> **管道** —> **TextSample** 按一下 **編輯** 從動作列開啟編輯器。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 新增影像和文字覆蓋元件至影像，如 [使用文字覆蓋](/help/user-guide/text-overlay.md#using-text-overlay) 區段。

1. 按一下 **設定** （扳手圖示）以開啟 **影像** 對話框。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 導覽至 **ContextHub** 標籤 **影像** 對話框。 按一下&#x200B;**「新增」**。

   >[!NOTE]
   >如果您尚未設定ContextHub設定，此選項會針對您的專案而停用。

1. 輸入 **值** 在 **預留位置** 欄位。 選取要從Google工作表中取得值的列，位於 **ContextHub變數**. 在此情況下，值會從Google工作表的第2列和第1列擷取。 現在，請輸入 **預設值** as **20**，如下圖所示。 完成後，按一下核取記號。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >下列影像會展示從google工作表擷取的值，以供您參考：

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 導覽回 **文字覆蓋** 頁簽，然後添加文本 *當前溫度{值}*，如下圖所示。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 按一下 **預覽** 來檢視所需的輸出。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)

---
title: 文字重疊
seo-title: 文字重疊
description: 文字覆蓋是AEM Screens提供的功能，可讓您提供覆蓋在影像上方的標題或說明，以在序列管道中建立引人入勝的體驗。 請詳閱本頁以了解更多。
seo-description: 文字覆蓋是AEM Screens提供的功能，可讓您提供覆蓋在影像上方的標題或說明，以在序列管道中建立引人入勝的體驗。 請詳閱本頁以了解更多。
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
feature: 製作畫面
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '850'
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
>**文字覆蓋**&#x200B;功能僅在您已安裝AEM 6.3 Feature Pack 5或AEM 6.4 Feature Pack 3時可用。

## 概覽 {#overview}

文字覆蓋是AEM Screens提供的功能，可讓您提供覆蓋在影像上方的標題或說明，以在序列管道中建立引人入勝的體驗。

若要了解如何建立自訂元件，請參閱&#x200B;**擴充AEM Screens元件**。

本節只會展示如何在AEM Screens專案中使用和運用海報元件，並在其中一個序列管道中作為文字覆蓋使用。

## 使用文字覆蓋{#using-text-overlay}

下節說明在AEM Screens專案中使用文字覆蓋的方式。

**必備條件**

開始實作此功能之前，請務必先將專案設定為開始實作文字覆蓋的先決條件。 例如，

* 建立AEM Screens專案（在此範例中， **TextOverlayDemo**）

* 在&#x200B;**Channels**&#x200B;資料夾下，建立標題為&#x200B;**TextSample**&#x200B;的序列通道

* 將內容新增至您的&#x200B;**TextSample**&#x200B;頻道

下圖顯示&#x200B;**Channels**&#x200B;資料夾中&#x200B;**TextSample**&#x200B;通道的&#x200B;**TextOverlayDemo**&#x200B;專案。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

請依照下列步驟，在AEM Screens管道中使用文字覆蓋：

1. 導覽至&#x200B;**TextOverlayDemo** —> **Channels** —> **TextSample** ，然後按一下動作列中的&#x200B;**Edit**&#x200B;以開啟編輯器。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 選取影像，然後按一下「**設定**（扳手圖示）」以開啟「屬性」對話方塊。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 從對話框的導航欄中選擇&#x200B;**文本覆蓋**&#x200B;選項，如下圖所示。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 了解文字覆蓋屬性{#understanding-text-overlay-properties}

使用「文字覆蓋」屬性，您可以將文字新增至Screens專案中的任何元件。 下節提供文字覆蓋中可用屬性的概觀：

![文字](assets/text.gif)

您可以在文字方塊中新增文字，並新增文字強調，例如粗體、斜體、底線等。

**顏** 色變體此選項允許文本為「深色」（黑色文本）或「淺色」（白色文本）。

**大小調** 整和定位此選項允許用戶水準或垂直對齊文本，或者使用微調工具對齊文本。

>[!NOTE]
>
>若要正確使用微調工具，請務必以(px)作為尾碼（例如200px）來識別正確的像素位置。 此運算式的結果將是從起始點開始200像素。

## 在文字覆蓋{#using-text-overlay-context-hub}中使用ContextHub值

以下章節說明資料存放區中值的使用方式，例如文字覆蓋元件中的google工作表。

**必備條件**

您必須為AEM Screens專案設定ContextHub設定。

若要了解如何使用資料存放區來設定及管理資料導向的資產變更，請參閱在AEM Screens中設定ContextHub](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/developing/configuring-context-hub.html) 。[

設定專案所需的設定後，請依照下列步驟使用google工作表中的值：

1. 導覽至&#x200B;**TextOverlayDemo** —> **Channels** —> **TextSample** ，然後從動作列按一下&#x200B;**Properties**。

1. 選取&#x200B;**Personalization**&#x200B;標籤以設定ContextHub設定。

   1. 選擇&#x200B;**ContextHub路徑**&#x200B;作為&#x200B;**libs**> **settings**> **cloudsettings** > **default** > **ContextHub配置**，然後按一下&#x200B;**選擇**。

   1. 選擇&#x200B;**段路徑**&#x200B;作為&#x200B;**conf**> **screens**> **settings** > **wcm** > **段**，然後按一下&#x200B;**選擇**。

   1. 按一下&#x200B;**「儲存並關閉」**。

      >[!NOTE]
      >
      >使用ContextHub和區段路徑，您最初會在此儲存內容中樞設定和區段。

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 導覽至&#x200B;**TextOverlayDemo** —> **Channels** —> **TextSample** ，然後按一下動作列中的&#x200B;**Edit**&#x200B;以開啟編輯器。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 如本頁的[使用文字覆蓋](/help/user-guide/text-overlay.md#using-text-overlay)區段所述，新增影像和文字覆蓋元件至您的影像。

1. 按一下「**設定**（扳手圖示）」以開啟「**影像**」對話方塊。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 從&#x200B;**Image**&#x200B;對話方塊導覽至&#x200B;**ContextHub**&#x200B;標籤。 按一下&#x200B;**「新增」**。

   >[!NOTE]
   >如果您尚未設定ContextHub設定，則專案將會停用此選項。

1. 在&#x200B;**預留位置**&#x200B;欄位中輸入&#x200B;**值**，在&#x200B;**ContextHub變數**&#x200B;中選擇要從google工作表中獲取值的行（在此例中，該值是從google工作表的行2和列1中檢索），然後輸入&#x200B;**預設值**&#x200B;作為&#x200B;**20**，如下圖所示。 完成後，按一下複選標籤。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >下列影像會展示從google工作表擷取的值，以供您參考：

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 從「影像」對話方塊導覽回「**文字覆蓋**」標籤，然後新增文字「*目前溫度{Value}*」，如下圖所示。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 按一下&#x200B;**預覽**&#x200B;以檢視所需的輸出。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
















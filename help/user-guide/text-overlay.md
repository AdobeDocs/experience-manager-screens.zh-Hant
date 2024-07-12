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
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '775'
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
>**文字覆蓋**&#x200B;功能僅在您已安裝AEM 6.3 Feature Pack 5或AEM 6.4 Feature Pack 3時才可用。

## 概觀 {#overview}

「文字覆蓋」是AEM Screens提供的功能。 它讓您透過在影像上方提供標題或說明，在順序頻道中建立引人入勝的體驗。

若要瞭解如何建立您自己的自訂元件，請參閱&#x200B;**延伸AEM Screens元件**。

本節僅說明如何在AEM Screens專案中使用和套用海報元件。 它也會示範在其中一個序列色版中作為文字覆蓋圖使用。

## 使用文字覆蓋 {#using-text-overlay}

下節將說明如何在AEM Screens專案中使用文字覆蓋。

**必備條件**

在實作此功能之前，請確定您已設定專案作為開始實作文字覆蓋的先決條件。 例如，

* 建立AEM Screens專案（在此範例中為&#x200B;**TextOverlayDemo**）

* 在&#x200B;**管道**&#x200B;資料夾下建立標題為&#x200B;**TextSample**&#x200B;的順序管道

* 新增內容至您的&#x200B;**TextSample**&#x200B;頻道

下圖顯示在&#x200B;**Channels**&#x200B;資料夾中具有&#x200B;**TextSample**&#x200B;頻道的&#x200B;**TextOverlayDemo**&#x200B;專案。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

請依照下列步驟，在AEM Screens頻道中使用文字覆蓋：

1. 導覽至&#x200B;**TextOverlayDemo** > **頻道** > **TextSample**，然後按一下動作列中的&#x200B;**編輯**。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 按一下影像，然後按一下&#x200B;**設定** （扳手圖示）以開啟內容對話方塊。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 從對話方塊的導覽列按一下&#x200B;**文字覆蓋**&#x200B;選項，如下圖所示。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 瞭解文字覆蓋屬性 {#understanding-text-overlay-properties}

您可以使用「文字覆蓋」屬性，將文字新增至Screens專案中的任何元件。 下節會提供文字覆蓋中可用屬性的概觀：

![文字](assets/text.gif)

您可以將文字新增至文字方塊，並新增印刷強調文字，例如粗體、斜體和底線。

**顏色變體**&#x200B;此選項允許文字為深色（黑色文字）或淺色（白色文字）。

**大小調整與定位**&#x200B;此選項可讓使用者水平或垂直對齊文字，或是使用微調工具對齊文字。

>[!NOTE]
>
>使用微調工具時，請務必以(px)作為尾碼來識別正確的畫素位置，例如200畫素。 此運算式的結果是從起點算起，為200畫素。

## 在文字覆蓋中使用ContextHub值 {#using-text-overlay-context-hub}

下節說明資料存放區中值的用法，例如，文字覆蓋元件中的google sheets 。

**必備條件**

為您的AEM Screens專案設定ContextHub設定。

若要瞭解如何使用資料存放區來設定及管理資料導向資產變更，請參閱[在AEM Screens中設定ContextHub](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/configuring-context-hub)。

在您設定專案所需的設定後，請依照下列步驟使用Google工作表中的值：

1. 導覽至&#x200B;**TextOverlayDemo** > **頻道** > **TextSample**，然後按一下動作列中的&#x200B;**內容**。

1. 按一下&#x200B;**Personalization**&#x200B;標籤，以便您可以設定ContextHub設定。

   1. 按一下&#x200B;**ContextHub路徑**&#x200B;做為&#x200B;**libs** > **設定** > **cloudsettings** > **預設** > **ContextHub設定**，然後按一下&#x200B;**選取**。

   1. 按一下&#x200B;**區段路徑**&#x200B;做為&#x200B;**conf** > **熒幕** > **設定** > **wcm** > **區段**，然後按一下&#x200B;**選取**。

   1. 按一下&#x200B;**「儲存並關閉」**。

      >[!NOTE]
      >
      >使用ContextHub和區段路徑，您最初會在此儲存您的ContextHub設定和區段。

      ![影像1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 導覽至&#x200B;**TextOverlayDemo** > **頻道** > **TextSample**，然後按一下動作列中的&#x200B;**編輯**。

   ![影像1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 依照此頁面的[使用文字覆蓋](/help/user-guide/text-overlay.md#using-text-overlay)區段所述，將影像和文字覆蓋元件新增至您的影像。

1. 按一下&#x200B;**設定** （扳手圖示）以開啟&#x200B;**影像**&#x200B;對話方塊。

   ![影像1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 從&#x200B;**影像**&#x200B;對話方塊瀏覽至&#x200B;**ContextHub**&#x200B;索引標籤。 按一下&#x200B;**新增**。

   >[!NOTE]
   >如果您尚未設定ContextHub組態，則會停用專案的此選項。

1. 在&#x200B;**預留位置**&#x200B;欄位中輸入&#x200B;**值**。 在&#x200B;**ContextHub變數**&#x200B;中，按一下您要從Google工作表取得值的列。 在此情況下，值會從Google工作表中擷取自列2和欄1。 現在，輸入&#x200B;**預設值**&#x200B;為&#x200B;**20**，如下圖所示。 完成後，按一下核取記號。

   ![影像1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >以下影像示範從Google工作表擷取的值，以供您參考：

   ![影像1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 從[影像]對話方塊瀏覽回&#x200B;**文字覆蓋**&#x200B;索引標籤，並新增文字&#x200B;*目前溫度{Value}*，如下圖所示。

   ![影像1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 按一下&#x200B;**預覽**。

   ![影像1](/help/user-guide/assets/text-overlay/text-overlay10.png)

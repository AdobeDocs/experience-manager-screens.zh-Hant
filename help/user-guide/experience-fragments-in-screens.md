---
title: 使用體驗片段
description: 瞭解如何在AEM Screens中使用體驗片段。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Experience Fragments
role: Admin, Developer
level: Intermediate
exl-id: 13c0d75e-435f-433e-8886-f451df863517
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '1102'
ht-degree: 0%

---

# 使用體驗片段 {#using-experience-fragments}

本頁涵蓋下列主題：

* **概觀**
* **在AEM Screens中使用體驗片段**
* **正在將變更傳播到頁面**

## 概觀 {#overview}

***體驗片段***&#x200B;是一或多個元件的群組，包括可在頁面中參考的內容和配置。 體驗片段可以包含任何元件。 例如，它可包含一或多個元件，這些元件可包含段落系統中被參考至完整體驗或由第三個端點請求的任何內容。


## 在AEM Screens中使用體驗片段 {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>下列範例使用&#x200B;**`We.Retail`**&#x200B;作為示範專案，其中體驗片段從&#x200B;**Sites**&#x200B;頁面套用至AEM Screens專案。

下列工作流程舉例說明如何使用Sites中`We.Retail`的體驗片段。 您可以選取網頁，並在其中一個專案的AEM Screens頻道中使用該內容。

### 必要條件 {#pre-requisites}

**使用頻道建立示範專案**

***正在建立專案***

1. 若要建立專案，請按一下&#x200B;**建立Screens專案**。
1. 將標題輸入為&#x200B;**DemoProject**。
1. 按一下「**儲存**」。

**DemoProject**&#x200B;已新增至您的AEM Screens。

***正在建立頻道***

1. 導覽至您建立的&#x200B;**DemoProject**，然後按一下&#x200B;**Channels**&#x200B;資料夾。

1. 按一下動作列中的&#x200B;**建立**，即可開啟精靈。
1. 從精靈中選擇&#x200B;**順序頻道**&#x200B;範本，然後按一下&#x200B;**下一步**。

1. 輸入&#x200B;**標題**&#x200B;作為&#x200B;**TestChannel**，然後按一下&#x200B;**建立**。

**TestChannel**&#x200B;已新增至您的&#x200B;**DemoProject**。\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### 建立體驗片段 {#creating-an-experience-fragment}

請依照下列步驟，在&#x200B;**DemoProject**&#x200B;中將&#x200B;**`We.Retail`**&#x200B;的內容套用至您的&#x200B;**TestChannel**。

1. **導覽至We.Retail中的網站頁面**

   1. 導覽至「網站」，然後按一下「**`We.Retail`** > **美國** > **英文** > **裝置**」，然後按一下此頁面，以便將其用作Screens頻道的體驗片段。

   1. 按一下動作列中的「**編輯**」，開啟您要用作Screens頻道體驗片段的頁面。

1. **重複使用內容**

   1. 按一下您要包含在頻道中的片段。
   1. 按一下右側的最後一個圖示，即可開啟&#x200B;**轉換成體驗片段**&#x200B;對話方塊。

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **建立體驗片段**

   1. 選擇&#x200B;**動作**&#x200B;做為&#x200B;**建立新的體驗片段**。

   1. 按一下&#x200B;**父路徑**。
   1. 按一下&#x200B;**範本**。 在此處選擇&#x200B;**體驗片段 — Screens變數**&#x200B;範本（欄位`/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`中的值）。

   1. 輸入&#x200B;**片段標題**&#x200B;作為&#x200B;**ScreensFragment**。

   1. 若要完成新體驗片段的建立，請按一下核取記號。

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   若要選取較簡單的選項，請按一下欄位右側的核取記號，以開啟選取對話方塊。

1. **正在建立體驗片段的即時副本**

   1. 導覽至AEM首頁。
   1. 按一下&#x200B;**體驗片段**&#x200B;並反白顯示&#x200B;**ScreensFragment**，然後按一下&#x200B;**變數作為即時副本**，如下圖所示：

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c.從&#x200B;**建立即時副本**&#x200B;精靈按一下&#x200B;**ScreensFragment**，然後按一下&#x200B;**下一步**。

   d.輸入&#x200B;**Title**&#x200B;和&#x200B;**Name**&#x200B;作為&#x200B;**Screens**。

   e.按一下&#x200B;**建立**，以便您建立即時副本。

   f.按一下&#x200B;**完成**，以便移回&#x200B;**ScreensFragment**&#x200B;頁面。

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >建立AEM Screens片段後，您可以編輯片段的屬性。 按一下片段，然後按一下動作列中的&#x200B;**屬性**。

   **編輯Screens片段的屬性**

   1. 導覽至&#x200B;**ScreensFragment** （您在前面的步驟中建立），然後按一下動作列中的&#x200B;**屬性**。

   1. 按一下「**離線設定**」標籤，如下圖所示。

   您可以將&#x200B;**使用者端資料庫** (Java™和CSS)和&#x200B;**靜態檔案**&#x200B;新增至您的體驗片段。

   以下範例顯示新增使用者端程式庫和字型作為靜態檔案的一部分到您的體驗片段。  ![片段](assets/fragment.gif)

1. **在Screens頻道中使用體驗片段作為元件**

   1. 導覽至您要使用&#x200B;**Screens**&#x200B;片段的Screens頻道。
   1. 按一下&#x200B;**TestChannel**，然後從動作列按一下&#x200B;**編輯**。

   1. 按一下側邊標籤中的元件圖示。
   1. 將&#x200B;**體驗片段**&#x200B;拖放至您的頻道。

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e.按一下&#x200B;**體驗片段**&#x200B;元件，然後按一下左上角（扳手）圖示，以開啟&#x200B;**體驗片段**&#x200B;對話方塊。

   f.按一下您在&#x200B;**路徑**&#x200B;中的&#x200B;*步驟3*&#x200B;中建立之片段的&#x200B;**Screens**&#x200B;即時副本。

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f.按一下您在&#x200B;**體驗片段**&#x200B;中的&#x200B;*步驟3*&#x200B;中建立之片段的&#x200B;**Screens**&#x200B;即時副本。

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h.輸入&#x200B;**持續時間**&#x200B;的毫秒數。

   i.從&#x200B;**體驗片段**&#x200B;對話方塊按一下&#x200B;**離線設定**，以便您可以定義使用者端程式庫和靜態檔案。

   >[!NOTE]
   >
   >若要新增使用者端程式庫或靜態檔案(除了您在步驟(4)中設定的專案)，您可以從&#x200B;**體驗片段**&#x200B;對話方塊的&#x200B;**離線設定**&#x200B;索引標籤中新增。

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j.按一下核取記號，以便完成處理。

### 驗證結果 {#validating-the-result}

完成上述步驟後，您可以在&#x200B;**ChannelOne**&#x200B;中驗證體驗片段，方法如下：

1. 正在瀏覽至&#x200B;**TestChannel**。
1. 從動作列選取&#x200B;**預覽**。

從您頻道中的&#x200B;**網站**&#x200B;頁面（體驗片段的即時副本）檢視內容，如下圖所示：\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## 將變更傳播至頁面 {#propagating-changes-from-the-master-page}

***即時副本***&#x200B;參考由轉出設定定義的同步化動作所維護的（來源的）副本。

由於您建立的體驗片段是來自&#x200B;**網站**&#x200B;頁面的即時副本，而您從主要頁面變更了該特定片段，因此您可以在您的頻道中檢視變更。 或者，檢視您使用體驗片段的目的地。

>[!NOTE]
>
>如需即時副本的詳細資訊，請參閱重複使用內容：多網站管理員和即時副本。

請依照下列步驟，將變更從主要管道傳播至您的目的地管道：

1. 從&#x200B;**網站** （主要）頁面按一下體驗片段，然後按一下鉛筆圖示，這樣您就可以編輯體驗片段中的專案。

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. 按一下體驗片段，然後按一下扳手圖示，即可開啟對話方塊以編輯影像。

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. **產品格線**&#x200B;對話方塊開啟。

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. 您可以編輯任何影像。 例如，這裡會取代此片段中的第一個影像。

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. 按一下體驗片段，然後按一下轉出圖示，這樣您就可以將變更傳播到您的頻道中使用的片段。

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. 按一下「轉出」。

   請注意，變更已轉出。

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### 驗證變更 {#validating-the-changes}

請依照下列步驟，確認管道中的變更：

1. 導覽至&#x200B;**Screens** > **管道** > **測試管道**。

1. 按一下動作列中的&#x200B;**預覽**。

下圖說明您的&#x200B;**TestChannel**&#x200B;中的變更：\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)

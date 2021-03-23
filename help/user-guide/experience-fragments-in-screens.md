---
title: 使用體驗片段
seo-title: 使用體驗片段
description: '請依本頁瞭解如何使用AEM Screens的體驗片段。 '
seo-description: '請依本頁瞭解如何使用AEM Screens的體驗片段。 '
uuid: 6ee16a94-3c53-43e0-99d5-c35cb9e01120
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 0e88e9e0-a95b-4acd-98ea-499d4d4e3c99
docset: aem65
feature: 製作螢幕、體驗片段
role: 管理員、開發人員
level: 中級
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1134'
ht-degree: 1%

---


# 使用體驗片段 {#using-experience-fragments}

本頁涵蓋下列主題：

* **概覽**
* **在AEM Screens使用體驗片段**
* **將更改傳播到頁面**

## 概覽 {#overview}

***體驗片段***&#x200B;是一組或多個元件，包括可在頁面中參考的內容和版面。 體驗片段可包含任何元件，例如，一個或多個元件可包含段落系統內任何內容，這些元件將參照至完整體驗或由第三端點要求。


## 在AEM Screens使用體驗片段{#using-experience-fragments-in-aem-screens}

>[!NOTE]
>以下範例使用&#x200B;**We.Retail**&#x200B;做為示範專案，從&#x200B;**Sites**&#x200B;頁面將體驗片段運用至AEM Screens專案。

例如，下列工作流程示範在網站中使用We.Retail的體驗片段。 您可以選擇網頁，並在其中一個專案中運用您AEM Screens頻道中的該內容。

### 先決條件{#pre-requisites}

**使用渠道建立示範專案**

***建立專案***

1. 按一下「建立畫面專案&#x200B;**」以建立新專案。**
1. 將標題輸入為&#x200B;**DemoProject**。
1. 按一下「**儲存**」。

**DemoProject**&#x200B;將添加到您的AEM Screens。

***建立渠道***

1. 導覽至您建立的&#x200B;**DemoProject**，並選取&#x200B;**Channels**&#x200B;資料夾。

1. 按一下操作欄中的&#x200B;**建立**&#x200B;以開啟嚮導。
1. 從嚮導中選擇&#x200B;**序列通道**&#x200B;模板，然後按一下&#x200B;**Next**。

1. 將&#x200B;**Title**&#x200B;輸入為&#x200B;**TestChannel**，然後按一下&#x200B;**Create**。

將&#x200B;**TestChannel**&#x200B;添加到&#x200B;**DemoProject**&#x200B;中。\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### 建立體驗片段{#creating-an-experience-fragment}

請依照下列步驟，將&#x200B;**We.Retail**&#x200B;的內容運用到&#x200B;**DemoProject**&#x200B;的&#x200B;**TestChannel**。

1. **導覽至We.Retail中的「網站」頁面**

   1. 導覽至「網站」並選取&#x200B;**We.Retail** -> **United States** -> **English** ->Equipment **，並選取此頁面做為您的「畫面」頻道的體驗片段。**

   1. 按一下動作列的「編輯」****，以開啟您要用作「畫面」頻道體驗片段的頁面。

1. **重新使用內容**

   1. 選取您要加入渠道的片段。
   1. 按一下右側的最後一個圖示，開啟「轉換為體驗片段&#x200B;**」對話方塊。**

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **建立體驗片段**

   1. 選擇&#x200B;**Action**&#x200B;作為&#x200B;**建立新的體驗片段**。

   1. 選擇&#x200B;**父路徑**。
   1. 選擇&#x200B;**Template**。 在此處選擇&#x200B;**體驗片段——畫面變化**&#x200B;範本（欄位`/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`中的值）。

   1. 將&#x200B;**片段標題**&#x200B;輸入為&#x200B;**ScreensFragment**。

   1. 按一下核取標籤，完成新體驗片段的建立。

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   注意：為了更輕鬆地選擇選項，請按一下欄位右側的複選標籤以開啟選擇對話框。

1. **建立體驗片段的即時副本**

   1. 導覽至AEM首頁。
   1. 選擇&#x200B;**體驗片段**&#x200B;並反白標示&#x200B;**ScreensFragment**，然後按一下「變更為即時副本&#x200B;**」，如下圖所示：**

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c.從&#x200B;**「建立即時副本」精靈中選取** ScreensFragment **，然後按一下「下一步」。******

   d.將&#x200B;**Title**&#x200B;和&#x200B;**Name**&#x200B;輸入為&#x200B;**Screens**。

   e.按一下「建立」以建立即時副本。****

   f.按一下「完成」，返回至「畫面片段」頁面。********

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >建立「畫面」片段後，您就可以編輯片段的屬性。 選擇該片段，然後從操作欄中按一下「屬性」(**Properties)。**

   **編輯畫面片段的屬性**

   1. 導覽至&#x200B;**ScreensFragment**（您在前述步驟中建立），然後從動作列按一下「屬性」。****

   1. 選擇&#x200B;**Offline Config**&#x200B;標籤，如下圖所示。

   您可以將&#x200B;**用戶端程式庫**（java和css）和&#x200B;**靜態檔案**&#x200B;新增至您的體驗片段。

   下列範例顯示在體驗片段中加入用戶端程式庫和靜態檔案中的字型。  ![片段](assets/fragment.gif)

1. **在畫面頻道中使用體驗片段做為元件**

   1. 導覽至您要使用&#x200B;**Screens**&#x200B;片段的「畫面」頻道。
   1. 選擇&#x200B;**TestChannel**，然後從操作欄中按一下&#x200B;**Edit**。

   1. 按一下側面頁籤中的元件表徵圖。
   1. 將&#x200B;**體驗片段**&#x200B;拖放至您的頻道。

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e.選擇&#x200B;**體驗片段**&#x200B;元件，並選取左上角（扳手）圖示以開啟&#x200B;**體驗片段**&#x200B;對話方塊。

   f.選擇在&#x200B;**Path**&#x200B;的&#x200B;*步驟3*&#x200B;中建立的片段的&#x200B;**螢幕**&#x200B;即時副本。

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f.在&#x200B;**體驗片段**&#x200B;的&#x200B;*步驟3*&#x200B;中，選取您在步驟3中建立之片段的&#x200B;**畫面**&#x200B;即時副本。

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h.在&#x200B;**持續時間**&#x200B;中輸入毫秒。

   i.從&#x200B;**體驗片段**&#x200B;對話方塊中選取&#x200B;**離線設定**，以定義用戶端程式庫和靜態檔案。

   >[!NOTE]
   >
   >如果除了在步驟(4)中配置的外，還要添加客戶端庫或靜態檔案，可以從&#x200B;**體驗片段**&#x200B;對話框的&#x200B;**離線配置**&#x200B;頁籤添加。

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j.按一下核取標籤以完成程式。

### 驗證結果{#validating-the-result}

完成上述步驟後，您可以通過以下方式驗證&#x200B;**ChannelOne**&#x200B;中的體驗片段：

1. 導覽至&#x200B;**TestChannel**。
1. 從操作欄中選擇&#x200B;**預覽**。

您會從頻道的&#x200B;**Sites**&#x200B;頁面（體驗片段的即時副本）檢視內容，如下圖所示：\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## 將更改傳播到頁面{#propagating-changes-from-the-master-page}

***即時*** 組排文字是指由同步動作（如轉出組態所定義）維護的復本（來源）。

由於體驗片段是從&#x200B;**Sites**&#x200B;頁面建立的即時副本，因此，如果您從主版頁面變更該特定片段，您將檢視頻道或使用體驗片段的目的地的變更。

>[!NOTE]
>
>如需即時副本的詳細資訊，請參閱重複使用內容：多網站管理員和即時副本。

請依照下列步驟，將變更從主頻道傳播至您的目的地頻道：

1. 從&#x200B;**Sites**（主版）頁面選取體驗片段，然後按一下鉛筆圖示以編輯體驗片段中的項目。

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. 選取「體驗片段」，然後按一下扳手圖示以開啟對話方塊以編輯影像。

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. 將開啟&#x200B;**產品網格**&#x200B;對話框。

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. 您可以編輯任何影像。 例如，此處會在此片段中取代第一個影像。

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. 選取「體驗片段」，然後按一下「轉出」圖示，將變更傳播至您頻道中使用的片段。

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. 按一下轉出以確認變更。

   您會看到變更已推出。

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### 驗證更改{#validating-the-changes}

請依照下列步驟確認您的渠道變更：

1. 導覽至&#x200B;**Screens** -> **Channels** -> **TestChannel**。

1. 從動作列按一下「預覽」，確認變更。****

下圖說明您&#x200B;**TestChannel**&#x200B;中的變更：\
![screen_shot_2018-06-08at3351pm](assets/screen_shot_2018-06-08at33351pm.png)


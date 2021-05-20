---
title: 使用體驗片段
seo-title: 使用體驗片段
description: '請詳閱本頁面，了解如何在AEM Screens中使用體驗片段。 '
seo-description: '請詳閱本頁面，了解如何在AEM Screens中使用體驗片段。 '
uuid: 6ee16a94-3c53-43e0-99d5-c35cb9e01120
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 0e88e9e0-a95b-4acd-98ea-499d4d4e3c99
docset: aem65
feature: 製作畫面、體驗片段
role: Administrator, Developer
level: Intermediate
exl-id: 13c0d75e-435f-433e-8886-f451df863517
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '1131'
ht-degree: 1%

---

# 使用體驗片段 {#using-experience-fragments}

本頁面涵蓋下列主題：

* **概覽**
* **在AEM Screens中使用體驗片段**
* **傳播對頁面的更改**

## 概覽 {#overview}

***體驗片段***&#x200B;是一組一或多個元件，包括可在頁面中參照的內容和版面。 體驗片段可包含任何元件，例如一或多個元件，這些元件可包含段落系統內的任何項目，而這些項目將參考至完整體驗，或由第三個端點請求。


## 在AEM Screens中使用體驗片段{#using-experience-fragments-in-aem-screens}

>[!NOTE]
>下列範例使用&#x200B;**We.Retail**&#x200B;做為示範專案，從此處將體驗片段從&#x200B;**Sites**&#x200B;頁面運用至AEM Screens專案。

例如，下列工作流程示範如何在Sites中使用We.Retail中的體驗片段。 您可以選擇網頁，並在其中一個專案中利用AEM Screens頻道中的該內容。

### 先決條件{#pre-requisites}

**使用管道建立示範專案**

***建立專案***

1. 按一下&#x200B;**建立螢幕專案**&#x200B;以建立新專案。
1. 將標題輸入為&#x200B;**DemoProject**。
1. 按一下「**儲存**」。

會將&#x200B;**DemoProject**&#x200B;新增至您的AEM Screens。

***建立管道***

1. 導覽至您建立的&#x200B;**DemoProject**，並選取&#x200B;**Channels**&#x200B;資料夾。

1. 按一下動作列中的&#x200B;**建立**&#x200B;以開啟精靈。
1. 從嚮導中選擇&#x200B;**序列通道**&#x200B;模板，然後按一下&#x200B;**下一步**。

1. 輸入&#x200B;**Title**&#x200B;作為&#x200B;**TestChannel**，然後按一下&#x200B;**Create**。

將將&#x200B;**TestChannel**&#x200B;添加到您的&#x200B;**DemoProject**&#x200B;中。\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### 建立體驗片段{#creating-an-experience-fragment}

請依照下列步驟，將&#x200B;**We.Retail**&#x200B;中的內容運用至&#x200B;**DemoProject**&#x200B;中的&#x200B;**TestChannel**。

1. **導覽至We.Retail中的「網站」頁面**

   1. 導覽至「網站」，並選取&#x200B;**We.Retail** -> **美國** -> **英文** -> **設備**，然後選取此頁面作為Screens頻道的體驗片段。

   1. 按一下動作列中的&#x200B;**編輯**，開啟您要作為Screens頻道體驗片段使用的頁面。

1. **重新使用內容**

   1. 選取您要納入管道的片段。
   1. 按一下右側的最後一個圖示，開啟&#x200B;**轉換為體驗片段**&#x200B;對話方塊。

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **建立體驗片段**

   1. 選擇&#x200B;**Action**&#x200B;作為&#x200B;**建立新體驗片段**。

   1. 選擇&#x200B;**父路徑**。
   1. 選擇&#x200B;**模板**。 在此處選擇&#x200B;**體驗片段 — 螢幕變化**&#x200B;範本（欄位`/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`中的值）。

   1. 將&#x200B;**片段標題**&#x200B;輸入為&#x200B;**ScreensFragment**。

   1. 按一下核取記號以完成新體驗片段的建立。

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   注意：要更輕鬆地選擇選項，請按一下欄位右側的複選標籤以開啟選擇對話框。

1. **建立體驗片段的即時副本**

   1. 導覽至AEM首頁。
   1. 選取&#x200B;**體驗片段**&#x200B;並反白顯示&#x200B;**ScreensFragment**，然後按一下「變化為即時副本&#x200B;**」，如下圖所示：**

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c.從&#x200B;**建立即時副本**&#x200B;精靈中選擇&#x200B;**ScreensFragment** ，然後按一下&#x200B;**下一步**。

   d.將&#x200B;**Title**&#x200B;和&#x200B;**Name**&#x200B;輸入為&#x200B;**Screens**。

   e.按一下&#x200B;**建立**&#x200B;以建立即時副本。

   f.按一下&#x200B;**Done**&#x200B;以返回&#x200B;**ScreensFragment**&#x200B;頁面。

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >建立Screens片段後，您就可以編輯片段的屬性。 選取片段，然後從動作列按一下「屬性&#x200B;**」。**

   **編輯畫面片段的屬性**

   1. 導覽至&#x200B;**ScreensFragment**（您在前述步驟中建立），然後從動作列按一下&#x200B;**屬性**。

   1. 選擇&#x200B;**離線配置**&#x200B;頁簽，如下圖所示。

   您可以將&#x200B;**用戶端程式庫**（java和css）和&#x200B;**靜態檔案**&#x200B;新增至體驗片段。

   下列範例顯示在體驗片段中新增用戶端程式庫和靜態檔案中的字型。  ![片段](assets/fragment.gif)

1. **在Screens頻道中使用體驗片段作為元件**

   1. 導覽至您要使用&#x200B;**Screens**&#x200B;片段的Screens頻道。
   1. 選擇&#x200B;**TestChannel**，然後從操作欄按一下&#x200B;**Edit**。

   1. 按一下側邊標籤中的元件圖示。
   1. 將&#x200B;**體驗片段**&#x200B;拖放至通道。

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e.選取&#x200B;**體驗片段**&#x200B;元件，然後選取左上角（扳手）圖示以開啟&#x200B;**體驗片段**&#x200B;對話方塊。

   f.選取您在&#x200B;**Path**&#x200B;的&#x200B;*Step 3*&#x200B;中建立的片段的&#x200B;**Screens**&#x200B;即時副本。

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f.選取您在&#x200B;**體驗片段**&#x200B;的&#x200B;*Step 3*&#x200B;中建立之片段的&#x200B;**Screens**&#x200B;即時副本。

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h.在&#x200B;**Duration**&#x200B;中輸入毫秒。

   我。從&#x200B;**體驗片段**&#x200B;對話方塊選取&#x200B;**離線設定**，以定義用戶端程式庫和靜態檔案。

   >[!NOTE]
   >
   >如果您除了在步驟(4)中設定外還想要新增用戶端程式庫或靜態檔案，您可以從&#x200B;**體驗片段**&#x200B;對話方塊的&#x200B;**離線設定**&#x200B;標籤新增。

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j.按一下核取記號以完成程式。

### 驗證結果{#validating-the-result}

完成上述步驟後，您可以透過下列方式驗證&#x200B;**ChannelOne**&#x200B;中的體驗片段：

1. 導覽至&#x200B;**TestChannel**。
1. 從動作列選取&#x200B;**預覽**。

您將從管道的&#x200B;**Sites**&#x200B;頁面（體驗片段的即時副本）檢視內容，如下圖所示：\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## 將更改傳播到頁{#propagating-changes-from-the-master-page}

***Live*** Copy是指由同步動作維護的復本（來源的），如轉出設定所定義。

自體驗片段以來，我們建立的是來自&#x200B;**Sites**&#x200B;頁面的即時副本，因此，如果您從主版頁面變更該特定片段，您將會檢視通道或您已使用體驗片段的目的地中的變更。

>[!NOTE]
>
>如需Live Copy的詳細資訊，請參閱重複使用內容：多網站管理員和即時副本。

請依照下列步驟，將變更從主管道傳播至您的目的地管道：

1. 從&#x200B;**Sites**（主版）頁面中選取體驗片段，然後按一下鉛筆圖示以編輯體驗片段中的項目。

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. 選取體驗片段，然後按一下扳手圖示以開啟對話方塊以編輯影像。

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. **產品網格**&#x200B;對話框開啟。

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. 您可以編輯任何影像。 例如，此處會取代此片段中的第一個影像。

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. 選取體驗片段，然後按一下轉出圖示，將變更傳播至管道中使用的片段。

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. 按一下轉出以確認變更。

   您會看到變更已推出。

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### 驗證更改{#validating-the-changes}

請依照下列步驟確認管道中的變更：

1. 導覽至&#x200B;**Screens** -> **頻道** -> **TestChannel**。

1. 按一下動作列中的&#x200B;**預覽**&#x200B;以確認變更。

下圖說明&#x200B;**TestChannel**&#x200B;中的更改：\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)

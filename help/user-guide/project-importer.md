---
title: 從檔案新增專案匯入工具
seo-title: 從檔案新增專案匯入工具
description: 這項功能可讓您將一組位置從CSV/XLS試算表大量匯入至AEM Screens專案。
seo-description: 這項功能可讓您將一組位置從CSV/XLS試算表大量匯入至AEM Screens專案。
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 從檔案新增專案匯入工具 {#new-project-importer-from-file}

本節說明從CSV/XLS試算表大量匯入位置集至AEM Screens專案的功能。

## 簡介 {#introduction}

當您在組織中第一次設定AEM Screens專案時，也需要建立所有位置。 如果您的專案涉及大量位置，會導致繁雜的工作，而且需要在UI中多次點選並等候。

此功能的目的是減少設定專案所需的時間，進而解決預算問題。

讓作者提供試算表作為輸入檔案，並讓系統自動在後端建立位置樹狀結構，此功能：

* *比透過使用者介面手動點選，可取得更佳的效能*
* *可讓客戶從自己的系統匯出其所在位置，並直接在AEM中輕鬆匯入*

如此可在初始專案設定期間或將現有的AEM畫面延伸至新位置時，節省時間和金錢。

## 架構概觀 {#architectural-overview}

下圖顯示Project Importer的架構概觀功能：

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### 資料模型 {#data-model}

Project Importer的資料模型說明如下：

>[!NOTE]
>
>目前版本僅支援匯入位置。

| **屬性** | **說明** |
|---|---|
| ***路徑{string*}** | 位置的資源路徑 |
| ***[./jcr:title]{string*}** | 要使用的範本名稱(即畫面／核心／范 *本／位置的位置*) |
| ***範本{string}*** | 用於頁面的可選標題 |
| ***[./jcr:description]{string}*** | 用於頁面的可選說明 |

因此，試算表(CSV/XLS)檔案需要下列欄：

* **路徑{string}** (要導入的位置的路徑，其中路徑的根是項目的位置資料夾(即， */foo* will be imported to */content/screens/&lt;project&gt;/locations/foo*)

* **範本{string}** （用於新位置的範本），目前唯一允許的值是「location」，但這將延伸至未來的所有畫面範本（「display」、「sequencechannel」等）
* [**./*] {string}**要在位置上設定的任何選用屬性(即。/jcr:title, ./jcr:description, ./foo, ./橫條圖). 目前的版本不允許篩選

>[!NOTE]
>
>任何不符合上述條件的欄將只會被忽略。 例如，如果工作表(CSV/XLS)檔案中定義了 **path**、**template**、**title**&#x200B;和 ******** itleImporter檔案以外的任何其他列，則這些欄位將被忽略，Apporject ImporterApporterAdmporterAxporter不會驗證將項目導入到AEM Project螢幕中的其他欄位。

## 使用Project Importer {#using-project-importer}

下節說明如何在AEM Screens專案中使用Project Importer。

>[!CAUTION]
>
>限制：
>
>* 目前版本不支援CSV/XLS/XLSX擴充功能以外的檔案。
>* 對於導入的檔案和以「」開頭的任何內容，不存在對屬性的過濾。/」將會匯入。
>



### 必備條件 {#prerequisites}

* 建立名為 **DemoProjectImport的新專案**

* 使用您需要匯入的範例CSV或Excel檔案。

為進行示範，您可從下方的章節下載Excel檔案。

[取得檔案](assets/minimal-file.xls)

### 以最低必填欄位匯入檔案 {#importing-the-file-with-minimum-required-fields}

請依照下列步驟，將檔案匯入至位置資料夾，並列出最低必填欄位：

>[!NOTE]
>
>下列範例將展示匯入專案所需的至少四個欄位：

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. 導覽至您的AEM Screens專案(**DemoProjectImport**)。

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. 從側欄選取專案** DemoProjectImporter **—&gt;** Create **—&gt;** Import Locations**。

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. 將開啟 **導入** 嚮導。 為具有位置的項目選擇您擁有的檔案，或選擇從「先決條件」(***Presequires***)部分下載的檔案( *minimal-file.xls* )。

   選取檔案後，按一下「下 **一步**」。

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. 從「導入」嚮導驗證檔案（位置）的內容，然後按一下「導 **入」**。

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. 因此，您現在可以檢視匯入至專案的所有位置。

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)

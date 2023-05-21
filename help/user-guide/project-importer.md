---
title: 從檔案新建項目導入程式
seo-title: New Project Importer from File
description: 此功能允許您將一組位置從CSV/XLS電子錶格批量導入到您的AEM Screens項目。
seo-description: This functionality allows you to bulk-import a set of locations from a CSV/XLS spreadsheet to your AEM Screens project.
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3bff9ef3-0d6f-41d8-a8ef-bcc5a795990e
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 2%

---

# 從檔案新建項目導入程式 {#new-project-importer-from-file}

本節介紹了將一組位置從CSV/XLS電子錶格批量導入到AEM Screens項目的功能。

## 簡介 {#introduction}

當您在組織中首次設定AEM Screens項目時，您也需要建立所有位置。 如果項目涉及大量位置，則會導致任務繁瑣，需要在UI中進行大量按一下和等待。

該功能的目的是減少設定項目所需的時間，從而解決預算問題。

通過讓作者提供電子錶格作為輸入檔案，並讓系統在後端自動建立位置樹，此功能：

* *比通過UI手動按一下可獲得更好的效能*
* *允許客戶從自己的系統導出他們擁有的位置，並可以輕鬆地直接將其導入AEM到*

這既節省了初始項目設定期間，也節省了將現有AEM Screens擴展到新地點的時間和資金。

## 架構概述 {#architectural-overview}

下圖顯示了項目導入程式功能的體系結構概述：

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### 資料模型 {#data-model}

項目導入程式的資料模型如下所述：

>[!NOTE]
>
>當前版本僅支援導入位置。

| **屬性** | **說明** |
|---|---|
| ***路徑{string}*}** | 位置的資源路徑 |
| ***[。/jcr：標題] {字串}*}** | 要使用的模板的名稱(即 *螢幕/核心/模板/位置*) |
| ***模板{string}*** | 用於頁面的可選標題 |
| ***[。/jcr：說明] {string}*** | 用於頁面的可選說明 |

因此，電子錶格(CSV/XLS)檔案需要以下列：

* **路徑{string}** 要導入的位置的路徑，其中路徑的根是項目的位置資料夾(即， */foo* 將導入 */content/screens/&lt;project>/locations/foo*)

* **模板{string}** 用於新位置的模板，目前唯一允許的值是「location」，但這將擴展到將來的所有螢幕模板（「display」、「sequencechannel」等）
* **[。/*] {string}** 要在位置(即。/jcr:title, ./jcr:description,。/foo,。/橫條圖). 當前版本目前不允許篩選

>[!NOTE]
>
>任何不符合上述條件的列將只被忽略。 例如，如果工作表(CSV/XLS)檔案中定義了除 **路徑**。**模板**。**標題**, **描述** 在檔案中，這些欄位將被忽略 **項目導入程式** 將不驗證將項目導入到您的AEM Screens項目的這些附加欄位。

## 使用項目導入程式 {#using-project-importer}

下節介紹項目導入程式在AEM Screens項目中的使用方式。

>[!CAUTION]
>
>限制:
>
>* 當前版本不支援CSV/XLS/XLSX擴展以外的檔案。
>* 對於導入的檔案和以「」開頭的任何內容，不存在對屬性的篩選。將導入/」。
>


### 必備條件 {#prerequisites}

* 建立標題為 **DemoProject導入**

* 使用需要導入的CSV或Excel檔案示例。

為了進行演示，您可以從下面的部分下載Excel檔案。

[取得檔案](assets/minimal-file.xls)

### 導入檔案時必須輸入最少的欄位 {#importing-the-file-with-minimum-required-fields}

按照以下步驟將檔案導入位置資料夾，並且最少包含必填欄位：

>[!NOTE]
>
>以下示例顯示了導入項目所需的最少四個欄位：

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. 導航到您的AEM Screens項目(**DemoProject導入**)。

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. 選擇項目** DemoProjectImporter **—>** 建立 **—>** 從側欄導入位置**。

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. 的 **導入** 的子菜單。 為項目選擇您具有位置的檔案或選擇檔案(***minimal file.xls***)從 *先決條件* 的子菜單。

   選擇檔案後，按一下 **下一個**。

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. 從「導入」嚮導中驗證檔案（位置）的內容，然後按一下 **導入**。

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. 因此，您現在將能夠查看導入到項目中的所有位置。

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)

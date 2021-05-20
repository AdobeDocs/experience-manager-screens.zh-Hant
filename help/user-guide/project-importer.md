---
title: 從檔案新增專案匯入工具
seo-title: 從檔案新增專案匯入工具
description: 此功能可讓您將一組位置從CSV/XLS試算表大量匯入至AEM Screens專案。
seo-description: 此功能可讓您將一組位置從CSV/XLS試算表大量匯入至AEM Screens專案。
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
feature: 管理畫面
role: Administrator
level: Intermediate
exl-id: 3bff9ef3-0d6f-41d8-a8ef-bcc5a795990e
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 1%

---

# 從檔案{#new-project-importer-from-file}新增專案匯入工具

本節說明將一組位置從CSV/XLS試算表大量匯入至AEM Screens專案的功能。

## 簡介 {#introduction}

當您在組織中首次設定AEM Screens專案時，也需要建立所有位置。 如果您的專案涉及大量位置，則會導致曠日持久的工作，需要在UI中點按並等候。

此功能的目的是減少設定項目所需的時間，從而解決預算問題。

讓作者提供試算表作為輸入檔案，並讓系統自動在後端建立位置樹狀結構，即可使用此功能：

* *比透過UI手動點按來達到更佳的效能*
* *可讓客戶從自己的系統匯出其所在的位置，並輕鬆直接在AEM中匯入*

這樣可在初始專案設定或將現有AEM Screens擴充至新位置時，節省時間和金錢。

## 架構概述{#architectural-overview}

下圖將展示Project Importer功能的架構概觀：

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### 資料模型 {#data-model}

專案匯入工具的資料模型說明如下：

>[!NOTE]
>
>目前版本僅支援匯入位置。

| **屬性** | **說明** |
|---|---|
| ***路徑{string*}** | 位置的資源路徑 |
| ***[。/jcr:title] {string*}** | 要使用的範本名稱（即&#x200B;*screens/core/templates/location*&#x200B;的位置） |
| ***模板{string}*** | 要用於頁面的可選標題 |
| ***[。/jcr:description] {string}*** | 用於頁面的可選說明 |

因此，試算表(CSV/XLS)檔案需要下列欄：

* **路徑{string}** 要匯入的位置的路徑，其中路徑的根為專案的位置資料夾(亦即 */* foo將匯入至 */content/screens/&lt;project>/locations/foo*)

* **範本{string}** 用於新位置的範本，目前唯一允許的值是「location」，但這將延伸至未來的所有Screens範本（「display」、「sequencchannel」等）
* **[。/*] {string}**&#x200B;要在位置上設定的任何選用屬性（即）。/jcr:title, ./jcr:description,./foo, 。/橫條圖). 目前的版本不允許篩選

>[!NOTE]
>
>任何不符合上述條件的欄將會忽略。 例如，若您的檔案中有任何其他欄在工作表(CSV/XLS)檔案中定義，但&#x200B;**path**、**template**、**title**&#x200B;和&#x200B;**description**&#x200B;除外，則這些欄位將被忽略，而&#x200B;**Project Importer**&#x200B;將您的專案匯入至AEM Screens專案時不會驗證這些其他欄位。

## 使用項目導入程式{#using-project-importer}

以下章節說明在AEM Screens專案中如何使用專案匯入工具。

>[!CAUTION]
>
>限制:
>
>* 目前版本不支援CSV/XLS/XLSX擴充功能以外的檔案。
>* 匯入的檔案和任何開頭為「」的項目均不存在篩選屬性。/」。

>



### 必備條件 {#prerequisites}

* 建立名為&#x200B;**DemoProjectImport**&#x200B;的新項目

* 使用您需要匯入的範例CSV或Excel檔案。

為了示範，您可以從下方的區段下載excel檔案。

[取得檔案](assets/minimal-file.xls)

### 使用最少必填欄位{#importing-the-file-with-minimum-required-fields}導入檔案

請依照下列步驟，將檔案匯入至位置資料夾，並填入最少必要欄位：

>[!NOTE]
>
>下列範例將展示匯入專案所需的至少四個欄位：

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. 導覽至您的AEM Screens專案(**DemoProjectImport**)。

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. 從側欄中選擇項目** DemoProjectImporter **—>**&#x200B;建立&#x200B;**—>**&#x200B;導入位置**。

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. **Import**&#x200B;嚮導開啟。 為具有位置的項目選擇您擁有的檔案，或選擇從&#x200B;*Preceipores*&#x200B;部分下載的檔案(***minimal-file.xls***)。

   選取檔案後，按一下&#x200B;**Next**。

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. 驗證導入嚮導中的檔案（位置）的內容，然後按一下&#x200B;**導入**。

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. 因此，您現在可以檢視匯入至專案的所有位置。

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)

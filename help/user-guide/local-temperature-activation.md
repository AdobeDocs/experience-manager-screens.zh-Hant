---
title: 旅行中心溫度激活
seo-title: 旅行中心溫度激活
description: 下列使用案例說明如何根據Google Sheets中填入的值啟用旅行中心當地溫度。
seo-description: 下列使用案例說明如何根據Google Sheets中填入的值啟用旅行中心當地溫度。
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 旅行中心溫度激活 {#travel-center-temperature-activation}

下列使用案例說明如何根據Google Sheets中填入的值啟用旅行中心當地溫度。

## 說明 {#description}

對於此使用案例，如果您的Google Sheets的「值」小於50，則會顯示含熱飲的影像，如果值大於或等於50，則會顯示含冷飲的影像。 若有其他值或無值，播放器將顯示預設影像。

## 先決條件 {#preconditions}

在您開始實作旅行中心當地溫度啟動之前，您必須瞭解如何在AEM Screens專案中設定 ***Data Store***、 ***Audience Segmentation******和Enable Targeting for Channels*** 。

如需詳細 [資訊，請參閱「在AEM畫面中設定ContextHub](configuring-context-hub.md) 」。

## 基本流程 {#basic-flow}

請依照下列步驟，實作「旅行中心當地溫度啟動」使用案例：

1. **填入Google工作表**

   1. 導覽至ContextHubDemo google工作表。
   1. 添加帶有 **Heading1的列** ，其中包含相應的溫度值。
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **根據需求在「對象」中設定區段**

   1. 導覽至對象中的區段(請參 ***閱步驟2:在「在AEM畫面中設定ContextHub*** 」頁 **[](configuring-context-hub.md)** 面中設定「觀眾區段」，以取得詳細資訊)。

   1. 選擇「 **工作表A1 1** 」，然後單 **擊編輯**。

   1. 選擇比較屬性，然後按一下設定圖示以編輯屬性。
   1. 從屬 **性名稱的下拉式清單中選取** 「Googlesheets/value/1/0 **」**

   1. 從下 **拉式選單中** ，將運算子選為**大於或等於*

   1. 將值 **輸入** 50 **。**

   1. 同樣地，選擇**工作表A1 2 **並按一下「編 **輯」**。

   1. 選擇「 **比較屬性——值** 」，然後按一下配置表徵圖以編輯屬性。
   1. 從屬 **性名稱的下拉式清單中選取** 「Googlesheets/value/1/0 **」**

   1. 從下 **拉式選單中** ，選取「運算子」為「小於**」

   1. 將值 **輸入** 50 **。**

1. 導覽並選取您的頻道()，然後從動作 **列按一下** 「編輯」。 在下列範例中， **DataDrivenWeather**，會使用循序頻道來展示功能。

   >[!NOTE]
   >
   >您的頻道應已擁有預設影像，且應依「在AEM畫面中設定ContextHub」中所述，預先 [設定觀眾](configuring-context-hub.md)。

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >您應該已使用「屬 **性」(Properties** ) **&gt;「個人化」(Personalization** **ContextHub)頁籤來設定ContextHub****** Configurations。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 從編 **輯器中選取** 「定位」，然後從下拉式選單中選取「品牌 **」和「活動** 」，然後按一下「 ********&#x200B;開始定位」。

   ![new_activity3](assets/new_activity3.gif)

1. **勾選預覽**

   1. 按一下「 **預覽」。** 此外，請開啟您的Google工作表並更新其值。
   1. 將值變更為小於50，您就可以檢視夏季飲品的影像。 如果Google Sheet中的值大於或等於50，則應該能夠檢視熱飲影像。
   ![result3](assets/result3.gif)


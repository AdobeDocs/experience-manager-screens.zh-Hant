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
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---


# 旅行中心溫度激活{#travel-center-temperature-activation}

下列使用案例說明如何根據Google Sheets中填入的值啟用旅行中心當地溫度。

## 說明 {#description}

對於此使用案例，如果您的Google Sheets的「值」小於50，則會顯示含熱飲的影像，如果值大於或等於50，則會顯示含冷飲的影像。 若有其他值或無值，播放器將顯示預設影像。

## 先決條件{#preconditions}

在開始實作旅行中心當地溫度啟動之前，您必須瞭解如何在AEM Screens專案中設定&#x200B;***Data Store***、***觀眾區隔***&#x200B;和&#x200B;***啟用頻道定位***。

如需詳細資訊，請參閱「在AEM Screens[中設定ContextHub」。](configuring-context-hub.md)

## 基本流{#basic-flow}

請依照下列步驟，實作「旅行中心當地溫度啟動」使用案例：

1. **填入Google工作表**

   1. 導覽至ContextHubDemo Google工作表。
   1. 添加具有&#x200B;**標題1**&#x200B;的列，其溫度值對應。

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **根據需求在「對象」中設定區段**

   1. 導覽至對象中的區段(請參閱&#x200B;***步驟2:在&#x200B;**[「在AEM Screens](configuring-context-hub.md)**頁面中設定ContextHub」中設定「觀眾區隔」，以取得詳細資訊)。***

   1. 選擇&#x200B;**工作表A1 1**，然後按一下&#x200B;**編輯**。

   1. 選擇比較屬性，然後按一下設定圖示以編輯屬性。
   1. 從&#x200B;**屬性名稱**&#x200B;的下拉式清單中選擇&#x200B;**googlessheets/value/1/0**

   1. 從下拉菜單中選擇&#x200B;**運算子**&#x200B;作為&#x200B;**greater-than-or-equal**

   1. 將&#x200B;**Value**&#x200B;輸入為&#x200B;**50**

   1. 同樣，選擇&#x200B;**工作表A1 2**&#x200B;並按一下&#x200B;**編輯**。

   1. 選擇&#x200B;**比較屬性——值** ，然後按一下配置表徵圖以編輯屬性。
   1. 從&#x200B;**屬性名稱**&#x200B;的下拉式清單中選擇&#x200B;**googlessheets/value/1/0**

   1. 從下拉菜單中選擇&#x200B;**Operator**&#x200B;作為&#x200B;**less-than**

   1. 將&#x200B;**Value**&#x200B;輸入為&#x200B;**50**

1. 導覽並選取您的頻道()，然後從動作列按一下「編輯&#x200B;**」。**&#x200B;在以下範例中，**DataDrivenWeather**&#x200B;使用循序頻道來展示功能。

   >[!NOTE]
   >
   >您的頻道應已有預設影像，且應依[在AEM Screens](configuring-context-hub.md)中設定ContextHub中所述預先設定觀眾。

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >您應使用渠道&#x200B;**屬性** —> **個人化**&#x200B;標籤設定&#x200B;**ContextHub** **配置**。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 從編輯器中選擇&#x200B;**Targeting**，然後從下拉式選單中選擇&#x200B;**Brand**&#x200B;和&#x200B;**Activity**，然後按一下「開始定位&#x200B;**」。**

   ![new_activity3](assets/new_activity3.gif)

1. **勾選預覽**

   1. 按一下「預覽」。**** 此外，請開啟您的Google工作表並更新其值。
   1. 將值變更為小於50，您就可以檢視夏季飲品的影像。 如果Google Sheet中的值大於或等於50，則應該能夠檢視熱飲影像。

   ![result3](assets/result3.gif)


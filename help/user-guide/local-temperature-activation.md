---
title: 旅行中心溫度激活
seo-title: 旅行中心溫度激活
description: 以下使用案例示範如何根據Google工作表中填入的值啟用旅行中心當地溫度。
seo-description: 以下使用案例示範如何根據Google工作表中填入的值啟用旅行中心當地溫度。
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
feature: 製作畫面
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# 旅行中心溫度激活 {#travel-center-temperature-activation}

以下使用案例示範如何根據Google工作表中填入的值啟用旅行中心當地溫度。

## 說明 {#description}

若為此使用案例，如果您的Google工作表的值小於50，則會顯示含有熱飲的影像，若值大於或等於50，則會顯示含有冷飲的影像。 如果有其他值或沒有值，播放器將顯示預設影像。

## 先決條件 {#preconditions}

在開始實作旅遊中心當地溫度啟動之前，您必須了解如何在AEM Screens專案中設定&#x200B;***Data Store***、***受眾細分***&#x200B;和&#x200B;***啟用頻道鎖定目標***。

如需詳細資訊，請參閱[在AEM Screens中設定ContextHub ](configuring-context-hub.md) 。

## 基本流量 {#basic-flow}

按照以下步驟實施「Travel Center Local Temperature Activation」使用案例：

1. **填入Google工作表**

   1. 導覽至ContextHubDemo Google工作表。
   1. 添加帶有&#x200B;**Heading1**&#x200B;的列，並為溫度添加相應值。

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **根據需求在受眾中設定區段**

   1. 導覽至對象中的區段(請參閱&#x200B;***步驟2:在「在AEM Screens ](configuring-context-hub.md)**中設定ContextHub」頁面中設定「對象區段」***以取得詳細資訊)。**[

   1. 選擇&#x200B;**工作表A1 1**，然後按一下&#x200B;**編輯**。

   1. 選取比較屬性，然後按一下設定圖示以編輯屬性。
   1. 從&#x200B;**屬性名稱**&#x200B;中的下拉式清單中選擇&#x200B;**googlesheets/value/1/0**

   1. 從下拉式選單中選取&#x200B;**Operator**&#x200B;作為&#x200B;**greater-than-or-equal**

   1. 將&#x200B;**值**&#x200B;輸入為&#x200B;**50**

   1. 同樣地，選擇&#x200B;**工作表A1 2**&#x200B;並按一下&#x200B;**編輯**。

   1. 選擇&#x200B;**比較屬性 — 值** ，然後按一下配置表徵圖以編輯屬性。
   1. 從&#x200B;**屬性名稱**&#x200B;中的下拉式清單中選擇&#x200B;**googlesheets/value/1/0**

   1. 從下拉式選單中，將&#x200B;**Operator**&#x200B;選為&#x200B;**less-than**

   1. 將&#x200B;**值**&#x200B;輸入為&#x200B;**50**

1. 導覽並選取您的通道()，然後按一下動作列中的&#x200B;**Edit** 。 在以下範例中， **DataDrivenWeather**&#x200B;使用循序通道來展示功能。

   >[!NOTE]
   >
   >您的管道應已有預設影像，且應依[在AEM Screens中設定ContextHub中所述預先設定對象。](configuring-context-hub.md)

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >您應該已使用通道&#x200B;**屬性** —> **個人化**&#x200B;標籤設定&#x200B;**ContextHub** **配置**。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 從編輯器中選擇&#x200B;**目標定位**，然後從下拉式選單中選擇&#x200B;**品牌**&#x200B;和&#x200B;**活動**，然後按一下&#x200B;**開始定位**。

   ![new_activity3](assets/new_activity3.gif)

1. **勾選預覽**

   1. 按一下「**預覽」。** 此外，請開啟您的Google工作表並更新其值。
   1. 將值變更為50以下，您應該就能檢視夏季飲品的影像。 如果「Google工作表」中的值大於或等於50，則應該可以檢視熱飲的影像。
   ![結果3](assets/result3.gif)

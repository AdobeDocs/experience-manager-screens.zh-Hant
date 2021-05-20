---
title: 零售庫存目標激活
seo-title: 零售庫存目標激活
description: 此使用案例會展示三種不同彩色運動衫的零售庫存。 根據Google Sheets中記錄的可用運動衫數量，螢幕上會顯示數量最多的影像（紅色、綠色或藍色運動衫）。
seo-description: 此使用案例會展示三種不同彩色運動衫的零售庫存。 根據Google Sheets中記錄的可用運動衫數量，螢幕上會顯示數量最多的影像（紅色、綠色或藍色運動衫）。
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
feature: 製作畫面
role: Administrator, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# 零售庫存目標激活{#retail-inventory-targeted-activation}

下列使用案例會根據您的Google工作表中的值示範三個不同的影像。

## 說明 {#description}

此使用案例會展示三種不同彩色運動衫的零售庫存。 根據Google Sheets中記錄的可用運動衫數量，螢幕上會顯示數量最多的影像（紅色、綠色或藍色運動衫）。

針對此使用案例，紅、綠或藍毛衣會根據可用毛衣數的最高值顯示在螢幕上。

## 先決條件 {#preconditions}

在開始實作零售庫存目標鎖定啟動之前，您必須了解如何在AEM Screens專案中設定&#x200B;***Data Store***、***對象區段***&#x200B;和&#x200B;***啟用管道目標鎖定***。

如需詳細資訊，請參閱[在AEM Screens中設定ContextHub ](configuring-context-hub.md) 。

## 基本流{#basic-flow}

請依照下列步驟，實作「零售庫存啟用」使用案例：

1. **填入Google工作表**

   1. 導覽至ContextHubDemo Google工作表。
   1. 新增三欄（紅、綠、藍），並為三件不同的運動衫加上對應的值。

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **根據需求設定對象**

   1. 導覽至對象中的區段(請參閱&#x200B;***步驟2:在「在AEM Screens ](configuring-context-hub.md)**中設定ContextHub」頁面中設定「對象區段」***以取得詳細資訊)。**[

   1. 新增三個區段&#x200B;**For_Red**、**For_Green**&#x200B;和&#x200B;**For_Blue**。

   1. 選擇&#x200B;**For_Red**，然後從操作欄按一下&#x200B;**Edit**。

   1. 拖放&#x200B;**比較：屬性 — 對編輯器執行屬性** ，然後按一下設定圖示以編輯屬性。
   1. 從&#x200B;**第一個屬性名稱**&#x200B;中的下拉式清單中選擇&#x200B;**googlesheets/value/1/2**

   1. 從下拉式選單中選取&#x200B;**Operator**&#x200B;作為&#x200B;**greater-than**

   1. 選擇&#x200B;**資料類型**&#x200B;作為&#x200B;**number**

   1. 從&#x200B;**第二屬性名稱**&#x200B;中的下拉式清單中選擇&#x200B;**googlesheets/value/1/1**。

   1. 拖放&#x200B;**其他比較：屬性 — 對編輯器執行屬性** ，然後按一下設定圖示以編輯屬性。
   1. 從&#x200B;**第一個屬性名稱**&#x200B;中的下拉式清單中選擇&#x200B;**googlesheets/value/1/2**。

   1. 從下拉式選單中選取&#x200B;**Operator**&#x200B;作為&#x200B;**greater-than**

   1. 選擇&#x200B;**資料類型**&#x200B;作為&#x200B;**number**

   1. 從&#x200B;**第二屬性名稱**&#x200B;中的下拉式清單中選擇&#x200B;**googlesheets/value/1/0**

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同樣地，請編輯比較屬性規則，並將其新增至&#x200B;**For_Blue**&#x200B;區段，如下圖所示：

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同樣地，請編輯比較屬性規則，並將其新增至** For_Green **區段，如下圖所示：

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >您會注意到，對於區段&#x200B;**For_Green**&#x200B;和&#x200B;**For_Green**，資料無法在編輯器中解析，因為目前只有第一個比較與Google工作表中的值一樣有效。

1. 導覽並選取您的&#x200B;**DataDrivenRetail**&#x200B;管道（循序管道），然後按一下動作列中的&#x200B;**Edit**。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >您應該已使用通道&#x200B;**屬性** —> **個人化**&#x200B;標籤設定&#x200B;**ContextHub** **配置**。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   您必須同時選取&#x200B;**Brand**&#x200B;和&#x200B;**Area**，活動才能在您啟動鎖定目標程式時正確列出。

1. **新增預設影像**

   1. 將預設影像新增至通道，然後按一下&#x200B;**Targeting**。
   1. 從下拉式選單中選取&#x200B;**Brand**&#x200B;和&#x200B;**Activity**，然後按一下&#x200B;**Start Targeting**。

   1. 按一下&#x200B;**開始鎖定目標**。

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   開始鎖定目標之前，您必須按一下側邊欄的「**+新增體驗鎖定目標」，以新增區段（** For_Green **、** For_Red **及** For_Blue **），如下圖所示。**

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 將影像新增至所有三個不同的畫面，如下所示。

   ![retail_targeting](assets/retail_targeting.gif)

1. **勾選預覽**

   1. 按一下「**預覽」。** 此外，請開啟您的Google工作表並更新其值。
   1. 變更所有三個不同欄的值，您會注意到顯示影像會根據庫存中的最高值更新。
   ![retail_result](assets/retail_result.gif)

---
title: 零售庫存鎖定
seo-title: 零售庫存鎖定
description: 此使用案例會展示三種不同顏色的運動衫的零售庫存。 根據Google Sheets中記錄的庫存中可用的汗衫數量，螢幕上會顯示數量最多的影像（紅色、綠色或藍色汗衫）。
seo-description: 此使用案例會展示三種不同顏色的運動衫的零售庫存。 根據Google Sheets中記錄的庫存中可用的汗衫數量，螢幕上會顯示數量最多的影像（紅色、綠色或藍色汗衫）。
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
feature: 製作畫面
role: 管理員、開發人員
level: 中級
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 0%

---


# 零售庫存目標啟動{#retail-inventory-targeted-activation}

下列使用案例會根據您的Google工作表中的值，展示3種不同的影像。

## 說明 {#description}

此使用案例會展示三種不同顏色的運動衫的零售庫存。 根據Google Sheets中記錄的庫存中可用的汗衫數量，螢幕上會顯示數量最多的影像（紅色、綠色或藍色汗衫）。

在此使用案例中，紅色、綠色或藍色毛衣會根據可用毛衣數的最高值顯示在您的螢幕上。

## 先決條件{#preconditions}

在開始實作零售庫存定位啟動之前，您必須瞭解如何在AEM Screens專案中設定&#x200B;***資料商店***、***受眾細分***&#x200B;和&#x200B;***啟用渠道定位***。

如需詳細資訊，請參閱「在AEM Screens設定ContextHub」。[](configuring-context-hub.md)

## 基本流{#basic-flow}

請依照下列步驟實施「零售庫存啟動」使用案例：

1. **填入Google工作表**

   1. 導覽至ContextHubDemo Google工作表。
   1. 為3種不同的運動衫新增3欄（紅色、綠色和藍色）及對應值。

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **依需求設定觀眾**

   1. 導覽至對象中的區段(請參閱&#x200B;***步驟2:在&#x200B;**[設定AEM Screens](configuring-context-hub.md)**頁面的ContextHub中設定「觀眾區隔」，以取得詳細資訊)。***

   1. 新增三個新區段&#x200B;**For_Red**、**For_Green**&#x200B;和&#x200B;**For_Blue**。

   1. 選擇&#x200B;**For_Red**，然後從操作欄按一下&#x200B;**Edit**。

   1. 拖放&#x200B;**比較：屬性——對編輯器的屬性**，然後按一下配置表徵圖以編輯屬性。
   1. 從&#x200B;**第一屬性名稱**&#x200B;的下拉式清單中選擇&#x200B;**googlessheets/value/1/2**

   1. 從下拉菜單中選擇&#x200B;**Operator**&#x200B;作為&#x200B;**greater-than**

   1. 選擇&#x200B;**資料類型**&#x200B;作為&#x200B;**數字**

   1. 從&#x200B;**第二屬性名稱**&#x200B;的下拉式清單中選擇&#x200B;**googlessheets/value/1/1**。

   1. 拖放&#x200B;**其他比較：屬性——對編輯器的屬性**，然後按一下配置表徵圖以編輯屬性。
   1. 從&#x200B;**第一屬性名稱**&#x200B;的下拉式清單中選擇&#x200B;**googlessheets/value/1/2**。

   1. 從下拉菜單中選擇&#x200B;**Operator**&#x200B;作為&#x200B;**greater-than**

   1. 選擇&#x200B;**資料類型**&#x200B;作為&#x200B;**數字**

   1. 從&#x200B;**第二屬性名稱**&#x200B;的下拉式清單中選擇&#x200B;**googlessheets/value/1/0**

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同樣地，請編輯比較屬性規則並新增至&#x200B;**For_Blue**&#x200B;區段，如下圖所示：

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同樣地，請編輯比較屬性規則並新增至** For_Green **segment，如下圖所示：

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >您會注意到，對於區段&#x200B;**For_Green**&#x200B;和&#x200B;**For_Green**，編輯器中無法解析資料，因為目前只有第一個比較與Google工作表中的值一樣有效。

1. 導覽並選取您的&#x200B;**DataDrivenRetail**&#x200B;頻道（序列頻道），然後從動作列按一下「編輯&#x200B;**a3/>」。**

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >您應使用渠道&#x200B;**屬性** —> **個人化**&#x200B;標籤設定&#x200B;**ContextHub** **配置**。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   您必須同時選擇&#x200B;**Brand**&#x200B;和&#x200B;**Area**，才能在啟動定位程式時正確列出活動。

1. **新增預設影像**

   1. 將預設影像新增至您的頻道，然後按一下「定位」**。**
   1. 從下拉式選單中選擇&#x200B;**品牌**&#x200B;和&#x200B;**活動**，然後按一下「開始定位&#x200B;**」。**

   1. 按一下「開始定位」**。**

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   在開始定位之前，您必須按一下側欄上的「新增體驗定位」區段（**For_Green**、**For_Red**&#x200B;和&#x200B;**For_Blue**），如下圖所示。****

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 將影像新增至所有三個不同的畫格，如下所示。

   ![retail_targeting](assets/retail_targeting.gif)

1. **勾選預覽**

   1. 按一下「預覽」。**** 此外，請開啟您的Google工作表並更新其值。
   1. 變更所有三個不同欄的值，您會注意到顯示影像會根據庫存中的最高值而更新。

   ![retail_result](assets/retail_result.gif)


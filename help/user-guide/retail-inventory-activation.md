---
title: 零售詳細目錄目標啟動
description: 瞭解此AEM Screens使用案例，其展示三種不同顏色運動衫的零售庫存量。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# 零售詳細目錄目標啟動 {#retail-inventory-targeted-activation}

下列使用案例會根據Google工作表中的值，示範三個不同的影像。

## 說明 {#description}

此使用案例展示了三種不同顏色運動衫的零售庫存量。 根據Google Sheets中記錄的可用庫存運動衫數量，會顯示數量最高的影像（紅色、綠色或藍色運動衫）。

紅色、綠色或藍色毛衣會根據可用毛衣數量的最高值顯示。

## 先決條件 {#preconditions}

開始實作零售詳細目錄鎖定目標啟用之前，請先瞭解如何在AEM Screens專案中設定&#x200B;***資料存放區***、***對象細分***&#x200B;和&#x200B;***啟用管道***&#x200B;的鎖定目標。

如需詳細資訊，請參閱[在AEM Screens中設定ContextHub](configuring-context-hub.md)。

## 基本流量 {#basic-flow}

請依照下列步驟，實作零售庫存啟用使用案例：

1. **填入Google工作表**

   1. 導覽至ContextHubDemo Google工作表。
   1. 為三件不同的運動衫新增對應值的三欄（紅色、綠色和藍色）。

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **根據需求設定對象**

   1. 導覽至您對象中的區段(如需詳細資訊，請參閱&#x200B;**[在AEM Screens中設定ContextHub](configuring-context-hub.md)**&#x200B;頁面中的&#x200B;***步驟2：設定對象細分***)。

   1. 新增三個新區段&#x200B;**For_Red**、**For_Green**&#x200B;和&#x200B;**For_Blue**。

   1. 按一下&#x200B;**For_Red**，然後按一下動作列中的&#x200B;**編輯**。

   1. 將&#x200B;**Comparison ： Property - Property**&#x200B;拖放至編輯器。
   1. 按一下&#x200B;**組態**&#x200B;圖示。
   1. 從&#x200B;**First Property name**&#x200B;的下拉式清單中，按一下&#x200B;**Googlesheets/value/1/2**。
   1. 按一下下拉式功能表中的&#x200B;**運運算元**，並設為&#x200B;**大於**。
   1. 按一下&#x200B;**資料型別**，並以&#x200B;**數字**&#x200B;顯示。
   1. 從&#x200B;**第二個屬性名稱**&#x200B;的下拉式清單中，按一下&#x200B;**google工作表/value/1/1**。
   1. 拖放&#x200B;**另一個比較：屬性 — 屬性**&#x200B;到編輯器並按一下&#x200B;**設定**&#x200B;圖示。
   1. 從&#x200B;**First Property name**&#x200B;的下拉式清單中，按一下&#x200B;**Googlesheets/value/1/2**。
   1. 按一下下拉式功能表中的&#x200B;**運運算元**，並設為&#x200B;**大於**。
   1. 按一下&#x200B;**資料型別**，並以&#x200B;**數字**&#x200B;顯示。
   1. 從&#x200B;**第二個屬性名稱**&#x200B;的下拉式清單中按一下&#x200B;**google工作表/value/1/0**。

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同樣地，編輯比較屬性規則並將其新增至&#x200B;**For_Blue**&#x200B;區段，如下圖所示：

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同樣地，編輯比較屬性規則並將其新增至&#x200B;**For_Green**&#x200B;區段，如下圖所示：

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >請注意，對於區段&#x200B;**For_Green**&#x200B;和&#x200B;**For_Green**，資料無法在編輯器中解析，因為根據Google工作表中的值，目前只有第一次比較有效。

1. 導覽並按一下您的&#x200B;**DataDrivenRetail**&#x200B;管道（順序管道）。
1. 按一下動作列中的&#x200B;**編輯**。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >您應該已經使用管道&#x200B;**屬性** > **Personalization**&#x200B;索引標籤來設定您的&#x200B;**ContextHub** **設定**。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   >
   >按一下&#x200B;**品牌**&#x200B;和&#x200B;**區域**，以便在您啟動鎖定目標程式時正確列出活動。

1. **正在新增預設影像**

   1. 新增預設影像至您的頻道，然後按一下&#x200B;**鎖定目標**。
   1. 從下拉式功能表按一下&#x200B;**品牌**&#x200B;和&#x200B;**活動**，然後按一下&#x200B;**開始鎖定目標**。
   1. 按一下&#x200B;**開始鎖定目標**。

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   >
   >開始鎖定目標之前，請從側邊欄選取&#x200B;**+新增體驗鎖定目標**，以新增區段（**For_Green**、**For_Red**&#x200B;和&#x200B;**For_Blue**），如下圖所示。

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 將影像新增至所有三種不同的情境，如下所示。

   ![零售定位](assets/retail_targeting.gif)

1. **正在檢查預覽**

   1. 按一下「**預覽」。**&#x200B;也請開啟您的Google工作表並更新其值。
   1. 變更所有三個不同欄的值。 請注意，顯示影像會根據詳細目錄中的最高值更新。

   ![retail_result](assets/retail_result.gif)

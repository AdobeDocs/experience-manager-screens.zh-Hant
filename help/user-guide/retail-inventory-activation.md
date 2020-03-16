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
translation-type: tm+mt
source-git-commit: a7d3ec582dde83ed6efb08a6c3c6a75cc0820970

---


# 零售庫存鎖定 {#retail-inventory-targeted-activation}

下列使用案例會根據您的Google工作表中的值，展示3種不同的影像。

## 說明 {#description}

此使用案例會展示三種不同顏色的運動衫的零售庫存。 根據Google Sheets中記錄的庫存中可用的汗衫數量，螢幕上會顯示數量最多的影像（紅色、綠色或藍色汗衫）。

在此使用案例中，紅色、綠色或藍色毛衣會根據可用毛衣數的最高值顯示在您的螢幕上。

## 先決條件 {#preconditions}

在您開始實作零售庫存定位啟動之前，您必須瞭解如何在AEM Screens專案中設定 ***Data Store***、 ***Audience Segmentation******和Enable Targeting for Channels*** 。

如需詳細 [資訊，請參閱「在AEM畫面中設定ContextHub](configuring-context-hub.md) 」。

## 基本流程 {#basic-flow}

請依照下列步驟實施「零售庫存啟動」使用案例：

1. **填入Google工作表**

   1. 導覽至ContextHubDemo Google工作表。
   1. 為3種不同的運動衫新增3欄（紅色、綠色和藍色）及對應值。
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **依需求設定觀眾**

   1. 導覽至對象中的區段(請參 ***閱步驟2:在「在AEM畫面中設定ContextHub*** 」頁 **[](configuring-context-hub.md)**面中設定「觀眾區段」，以取得詳細資訊)。

   1. 新增三個 **新區段For_Red**、 **For_Green**&#x200B;和 **For_Blue**。

   1. 選 **取For_Red** ，然後從動作 **列按一下「編輯** 」。

   1. 拖放比 **較：屬性** -對編輯器的屬性，然後按一下配置表徵圖以編輯屬性。
   1. 從「 **第一個屬性名稱」的下拉式清單中選取****Googlesheets/value/1/2**

   1. 從下 **拉式選** 單中選取「運 **算元** 」為「大於」

   1. 選擇數 **據類型** ，作為 **數字**

   1. 從「 **第二個屬性名稱」(** Second Property name)的下拉式清單中，選取 **Googlesheets/value/1/1**。

   1. 拖放另一 **個比較：屬性** -對編輯器的屬性，然後按一下配置表徵圖以編輯屬性。
   1. 從「 **第一個屬性名稱」(** First Property name)的下拉式清單中，選取 **Googlesheets/value/1/2**。

   1. 從下 **拉式選** 單中選取「運 **算元** 」為「大於」

   1. 選擇 **資料類型** ，作為 **數字**

   1. 從「 **第二個屬性名稱」(****Second Property name)的下拉式清單中，選取Googlesheets/value/1/0**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同樣地，請編輯比較屬性規則並新 **增至For_Blue** 區段，如下圖所示：

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同樣地，請編輯比較屬性規則並新增至** For_Green **segment，如下圖所示：

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >您會注意到，對於 **For_Green** 和 **** For_Green區段，無法在編輯器中解析資料，因為目前只有第一個比較與Google工作表中的值相同，才有效。

1. 導覽並選取您 **的DataDrivenRetail** 頻道（序列頻道），然後從動作列按 **一下「編輯** 」。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >您應該已使用「屬 **性」(Properties** ) **>「個人化」(Personalization** **ContextHub)頁籤來設定ContextHub****** Configurations。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   您必須同時選取 **品牌****** 和區域，才能在啟動定位程式時正確列出活動。

1. **新增預設影像**

   1. 新增預設影像至您的頻道，然後按一下「定 **位」**。
   1. 從下 **拉式選單選** 擇「品牌 **」和「活動** 」，然後按一下「開始 **定位」**。

   1. 按一下 **開始定位**。
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   在開始定位之前，您必須按一下從側邊欄上「**+新增體驗定位」，新增區段(** For_Green **、** For_Red **和** For_Blue **** )，如下圖所示。

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 將影像新增至所有三個不同的畫格，如下所示。

   ![retail_targeting](assets/retail_targeting.gif)

1. **勾選預覽**

   1. 按一下「 **預覽」。** 此外，請開啟您的Google工作表並更新其值。
   1. 變更所有三個不同欄的值，您會注意到顯示影像會根據庫存中的最高值而更新。
   ![retail_result](assets/retail_result.gif)


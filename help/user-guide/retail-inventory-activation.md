---
title: 零售庫存目標激活
seo-title: Retail Inventory Targeted Activation
description: 此使用案例展示了三種不同顏色的運動衫的零售庫存。 根據在「Google頁」中記錄的庫存中可用的汗衫數量，螢幕上將顯示數量最多的影像（紅色、綠色或藍色運動衫）。
seo-description: This Use Case showcases the retail inventory stock for three different colored sweatshirts. Depending on the number of sweatshirts available in stock that is recorded in Google Sheets, the image (red, green, or blue sweatshirt) with highest number is displayed on the screen.
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# 零售庫存目標激活 {#retail-inventory-targeted-activation}

以下用例根據「Google工作表」中的值演示了三種不同的影像。

## 說明 {#description}

此使用案例展示了三種不同顏色的運動衫的零售庫存。 根據在「Google頁」中記錄的庫存中可用的汗衫數量，螢幕上將顯示數量最多的影像（紅色、綠色或藍色運動衫）。

對於此用例，紅色、綠色或藍色毛衣將根據可用毛衣數的最高值顯示在螢幕上。

## 先決條件 {#preconditions}

在開始實施零售庫存目標激活之前，必須瞭解如何設定 ***資料儲存***。 ***受眾細分*** 和 ***為通道啟用目標*** AEM Screens項目。

請參閱 [在AEM Screens配置ContextHub](configuring-context-hub.md) 的上界。

## 基本流 {#basic-flow}

按照以下步驟實施Retail Inventory激活使用案例：

1. **填充Google頁**

   1. 導航到ContextHubDemoGoogle工作表。
   1. 添加三列（紅色、綠色和藍色），並為三件不同的運動衫添加相應的值。

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **根據要求配置受眾**

   1. 導航至受眾中的段(請參閱 ***步驟2:設定受眾細分*** 在 **[在AEM Screens配置ContextHub](configuring-context-hub.md)** )的正平方根。

   1. 添加三個新段 **紅色**。 **綠色**, **藍色**。

   1. 選擇 **紅色** 按一下 **編輯** 按鈕。

   1. 拖放 **比較：屬性 — 屬性** 編輯器，然後按一下「配置」表徵圖以編輯屬性。
   1. 選擇 **谷歌表/價值/1/2** 從 **第一個屬性名稱**

   1. 選擇 **運算子** 如 **大於** 下拉菜單中

   1. 選擇 **資料類型** 如 **數**

   1. 選擇 **谷歌表/值/1/1** 從 **第二個屬性名稱**。

   1. 拖放 **另一個比較：屬性 — 屬性** 編輯器，然後按一下「配置」表徵圖以編輯屬性。
   1. 選擇 **谷歌表/價值/1/2** 從 **第一個屬性名稱**。

   1. 選擇 **運算子** 如 **大於** 下拉菜單中

   1. 選擇 **資料類型** 如 **數**

   1. 選擇 **谷歌表/值/1/0** 從 **第二個屬性名稱**

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同樣，編輯和添加比較屬性規則到 **藍色** 如下圖所示：

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同樣，如下圖所示，編輯比較屬性規則並將其添加到** For_Green **段：

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >您會注意到，對於 **綠色** 和 **綠色**，無法在編輯器中解析資料，因為只有第一個比較現在才有效，與「Google工作表」中的值相同。

1. 導航並選擇 **資料驅動零售** 通道（序列通道），然後按一下 **編輯** 按鈕。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >你應該把 **上下文中心** **配置** 使用頻道 **屬性** —> **個性化** 頁籤。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   必須同時選擇 **品牌** 和 **區域** 用於啟動「目標」進程時要正確列出的活動。

1. **添加預設影像**

   1. 將預設影像添加到頻道，然後按一下 **目標**。
   1. 選擇 **品牌** 和 **活動** 按一下 **開始目標**。

   1. 按一下 **開始目標**。

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   在開始目標之前，必須添加段(**綠色**。 **紅色**, **藍色**) **+添加體驗目標** 如下圖所示。

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 將影像添加到所有三個不同的螢幕，如下所示。

   ![零售目標](assets/retail_targeting.gif)

1. **檢查預覽**

   1. 按一下 **預覽。** 另外，開啟您的Google工作表並更新其值。
   1. 更改所有三個不同列的值，您會注意到顯示影像會根據庫存中的最高值進行更新。
   ![retail_result](assets/retail_result.gif)

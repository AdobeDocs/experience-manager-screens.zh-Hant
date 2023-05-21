---
title: 酒店預訂激活
seo-title: Hospitality Reservation Activation
description: 以下使用案例演示了基於Google工作表中填充的值的醫院預訂激活的使用。
seo-description: The following use case demonstrates the usage of hospital reservation activation based on the values populated in Google Sheets.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 酒店預訂激活 {#hospitality-reservation-activation}

以下使用案例演示了基於Google工作表中填充的值的醫院預訂激活的使用。

## 說明 {#description}

對於此使用案例，Google表填充了兩家餐廳的預訂百分比 **餐廳1** 和 **餐廳2**。 根據Restaurant1和Restaurant2的值應用公式，並根據公式將值1或2分配給 **廣告目標** 列。

如果 **餐廳1** > **餐廳2**，則 **阿德塔傑** 賦值 **1** 否則 **廣告目標** 賦值 **2**。 值1生成 *牛排食品* 選項和值2導致顯示 *泰國食品* 的子菜單。

## 先決條件 {#preconditions}

在開始執行保留激活之前，必須瞭解如何設定 ***資料儲存***。 ***受眾細分*** 和 ***為通道啟用目標*** AEM Screens項目。

請參閱 [在AEM Screens配置ContextHub](configuring-context-hub.md) 的上界。

## 基本流 {#basic-flow}

按照以下步驟為您的AEM Screens項目實施酒店預訂激活使用案例：

1. **填充Google工作表並添加公式。**

   例如，將公式應用到第三列 **廣告目標**，如下圖所示。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **根據要求配置受眾中的段**

   1. 導航至受眾中的段(請參閱 ***步驟2:設定受眾細分*** 在 **[在AEM Screens配置ContextHub](configuring-context-hub.md)** )的正平方根。

   1. 選擇 **工作表A1 1** 按一下 **編輯**。

   1. 選擇比較屬性，然後按一下配置表徵圖以編輯屬性。
   1. 選擇 **谷歌表/價值/1/2** 從 **屬性名稱**

   1. 選擇 **運算子** 如 **等** 下拉菜單中

   1. 輸入 **值** 如 **1**

   1. 同樣，選擇 **工作表A1 2** 按一下 **編輯**。

   1. 選擇比較屬性，然後按一下配置表徵圖以編輯屬性。
   1. 選擇 **谷歌表/價值/1/2** 從 **屬性名稱**

   1. 選擇 **運算子** 如 **2**

1. 導航並選擇您的頻道()，然後按一下 **編輯** 按鈕。 在以下示例中， **資料驅動餐廳**，使用順序通道來顯示該功能。

   >[!NOTE]
   >
   >您的頻道應已經擁有預設映像，應按中所述預配置觀眾 [在AEM Screens配置ContextHub](configuring-context-hub.md)。

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >你應該把 **上下文中心** **配置** 使用頻道 **屬性** —> **個性化** 頁籤。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 選擇 **目標** 從編輯器中選擇 **品牌** 和 **活動** 按一下 **開始目標**。
1. **檢查預覽**

   1. 按一下 **預覽。** 另外，開啟您的Google表並更新其值。
   1. 更新中的值 **餐廳1** 和 **餐廳2** 的子菜單。 如果 **餐廳1** > **餐廳2** 您應該能夠查看 *牛排* 否則， *泰語* 食物影像顯示在螢幕上。
   ![result5](assets/result5.gif)

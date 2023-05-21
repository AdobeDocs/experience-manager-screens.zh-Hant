---
title: 旅行中心溫度激活
seo-title: Travel Center Temperature Activation
description: 以下使用案例演示了基於Google工作表中填充的值的旅行中心局部溫度激活的使用。
seo-description: The following use case demonstrates the usage of travel center local temperature activation based on the values populated in Google Sheets.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 旅行中心溫度激活 {#travel-center-temperature-activation}

以下使用案例演示了基於Google工作表中填充的值的旅行中心局部溫度激活的使用。

## 說明 {#description}

對於此使用情形，如果您的Google表的值小於50，則顯示含熱飲的影像，如果值大於或等於50，則顯示含冷飲的影像。 如果有其它值或沒有值，播放器將顯示預設影像。

## 先決條件 {#preconditions}

在開始實施旅行中心本地溫度激活之前，必須瞭解如何設定 ***資料儲存***。 ***受眾細分*** 和 ***為通道啟用目標*** AEM Screens項目。

請參閱 [在AEM Screens配置ContextHub](configuring-context-hub.md) 的上界。

## 基本流 {#basic-flow}

按照以下步驟實施「Travel Center Local Temperature Activation（旅行中心本地溫度激活）」使用案例：

1. **填充Google頁**

   1. 導航到ContextHubDemoGoogle工作表。
   1. 添加列 **標題1** 與溫度的對應值。

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **根據要求配置受眾中的段**

   1. 導航至受眾中的段(請參閱 ***步驟2:設定受眾細分*** 在 **[在AEM Screens配置ContextHub](configuring-context-hub.md)** )的正平方根。

   1. 選擇 **工作表A1 1** 按一下 **編輯**。

   1. 選擇比較屬性，然後按一下配置表徵圖以編輯屬性。
   1. 選擇 **谷歌表/值/1/0** 從 **屬性名稱**

   1. 選擇 **運算子** 如 **大於等於** 下拉菜單中

   1. 輸入 **值** 如 **50**

   1. 同樣，選擇 **工作表A1 2** 按一下 **編輯**。

   1. 選擇 **比較屬性 — 值** 然後按一下「配置」表徵圖以編輯屬性。
   1. 選擇 **谷歌表/值/1/0** 從 **屬性名稱**

   1. 選擇 **運算子** 如 **小於** 下拉菜單中

   1. 輸入 **值** 如 **50**

1. 導航並選擇您的頻道()，然後按一下 **編輯** 按鈕。 在以下示例中， **資料驅動天氣**，使用順序通道來顯示該功能。

   >[!NOTE]
   >
   >您的頻道應已經擁有預設映像，應按中所述預配置觀眾 [在AEM Screens配置ContextHub](configuring-context-hub.md)。

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >你應該把 **上下文中心** **配置** 使用頻道 **屬性** —> **個性化** 頁籤。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 選擇 **目標** 從編輯器中選擇 **品牌** 和 **活動** 按一下 **開始目標**。

   ![新建活動3](assets/new_activity3.gif)

1. **檢查預覽**

   1. 按一下 **預覽。** 另外，開啟您的Google工作表並更新其值。
   1. 將值更改為小於50，您應該能夠查看夏季飲料的影像。 如果「Google紙」中的值大於或等於50，則應能查看熱飲影像。
   ![result3](assets/result3.gif)

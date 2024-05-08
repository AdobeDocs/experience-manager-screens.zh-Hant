---
title: 旅行中心溫度啟用
description: 使用AEM Screens，瞭解此使用案例如何根據Google Sheets中填入的值，示範如何使用旅行中心當地溫度啟用。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# 旅行中心溫度啟用 {#travel-center-temperature-activation}

下列使用案例示範如何根據Google Sheets中填入的值，使用旅行中心本機溫度啟動。

## 說明 {#description}

針對此使用案例，如果Google Sheets中的值小於50，則會顯示含有熱飲的影像。 如果值大於或等於50，則會顯示含有冷飲的影像。 如果有其他值或完全沒有值，播放器會顯示預設影像。

## 先決條件 {#preconditions}

在您開始實作旅行中心當地溫度啟動之前，請先瞭解如何設定 ***資料存放區***， ***對象細分*** 和 ***啟用頻道目標定位*** 在AEM Screens專案中。

另請參閱 [在AEM Screens中設定ContextHub](configuring-context-hub.md) 以取得詳細資訊。

## 基本流量 {#basic-flow}

請依照下列步驟，實作Travel Center本機溫度啟動使用案例：

1. **填入Google工作表**

   1. 導覽至ContextHubDemo Google工作表。
   1. 新增包含的欄 **`Heading1`** 有對應的溫度值。

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **根據需求在Audiences中設定區段**

   1. 導覽至您對象中的區段(請參閱 ***步驟2：設定對象細分*** 在 **[在AEM Screens中設定ContextHub](configuring-context-hub.md)** 頁面（以取得更多詳細資料）。

   1. 按一下 **工作表A1 1** 並按一下 **編輯**.

   1. 按一下比較屬性，然後按一下設定圖示。
   1. 按一下 **谷歌眼表/value/1/0** 從的下拉式清單 **屬性名稱**

   1. 按一下 **運運算元** 作為 **大於或等於** 從下拉式功能表

   1. 輸入 **值** 作為 **50**

   1. 同樣地，選取 **工作表A1 2** 並按一下 **編輯**.

   1. 按一下 **比較屬性 — 值** 並選取設定圖示。
   1. 按一下 **谷歌眼表/value/1/0** 從的下拉式清單 **屬性名稱**

   1. 按一下 **運運算元** 作為 **小於** 從下拉式功能表

   1. 輸入 **值** 作為 **50**

1. 導覽並選取您的管道()，然後按一下 **編輯** 從動作列移除。 在以下範例中， **DataDrivenWeather**，循序頻道可用來展示此功能。

   >[!NOTE]
   >
   >您的管道應已具有預設影像，且對象應如所述預先設定 [在AEM Screens中設定ContextHub](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >您應該已設定您的 **ContextHub** **設定** 使用通道 **屬性** > **個人化** 標籤。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 按一下 **目標定位** 在編輯器中，按一下 **品牌** 和 **活動** 從下拉式功能表，然後按一下 **開始定位**.

   ![new_activity3](assets/new_activity3.gif)

1. **檢查預覽**

   1. 按一下 **預覽。** 此外，請開啟Google工作表並更新其值。
   1. 將值變更為小於50。 您應該能夠檢視冷飲的影像。 如果「Google工作表」中的值為50或更大，您應該會看到熱飲的影像。

   ![result3](assets/result3.gif)

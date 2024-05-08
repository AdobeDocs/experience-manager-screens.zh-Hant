---
title: Hospitality Reservation Activation
description: 瞭解此使用案例如何示範如何根據Google Sheets中填入的值來使用旅館業預訂啟用。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Hospitality Reservation Activation {#hospitality-reservation-activation}

下列使用案例示範如何根據Google Sheets中填入的值，使用醫院預約啟用。

## 說明 {#description}

在此使用案例中，Google工作表會填入兩家餐廳的訂位百分比 **`Restaurant1`** 和 **`Restaurant2`**. 根據下列的值套用公式： `Restaurant1` 和 `Restaurant2` 而且根據公式，值1或2會指派給 **adtarget** 欄。

如果 **`Restaurant1`** > **`Restaurant2`**，然後 **AdTarget** 已指派值 **1** 否則 **adtarget** 已指派值 **2**. 值1產生 *牛排食品* 選項和值二會顯示 *泰國菜* 選項。

## 先決條件 {#preconditions}

開始實施預訂啟用之前，請先瞭解如何設定 ***資料存放區***， ***對象細分*** 和 ***啟用頻道目標定位*** 在AEM Screens專案中。

另請參閱 [在AEM Screens中設定ContextHub](configuring-context-hub.md) 以取得詳細資訊。

## 基本流量 {#basic-flow}

請依照下列使用案例步驟，為您的AEM Screens專案實作旅館業保留啟用：

1. **填入Google工作表並新增公式**.

   例如，將公式套用至第三欄 **adtarget**，如下圖所示。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **根據需求在Audiences中設定區段**

   1. 導覽至您對象中的區段(請參閱 ***步驟2：設定對象細分*** 在 **[在AEM Screens中設定ContextHub](configuring-context-hub.md)** 頁面（以取得更多詳細資料）。
   1. 按一下 **工作表A1 1** 並按一下 **編輯**.
   1. 按一下比較屬性，然後按一下 **設定** 圖示。
   1. 按一下 **谷歌眼表/value/1/2** 從的下拉式清單 **屬性名稱**.
   1. 按一下 **運運算元** 作為 **等於** （從下拉式功能表）。
   1. 輸入 **值** 作為 **1**.
   1. 同樣地，按一下 **工作表A1 2** 並按一下 **編輯**.
   1. 按一下比較屬性，然後按一下 **設定** 圖示。
   1. 按一下 **谷歌眼表/value/1/2** 從的下拉式清單 **屬性名稱**.
   1. 按一下 **運運算元** 作為 **2**.

1. 導覽並按一下您的管道()，然後按一下 **編輯** 從動作列移除。 在以下範例中， **DataDrivenRestaurant**，循序頻道可用來展示此功能。

   >[!NOTE]
   >
   >您的管道應已具有預設影像，且對象應如所述預先設定 [在AEM Screens中設定ContextHub](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >您應該已設定您的 **ContextHub** **設定** 使用通道 **屬性** > **個人化** 標籤。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 按一下 **目標定位** 在編輯器中，按一下 **品牌** 和 **活動** 從下拉式功能表，然後按一下 **開始定位**.
1. **檢查預覽**

   1. 按一下 **預覽。** 此外，請開啟Google工作表並更新其值。
   1. 更新中的值 **`Restaurant1`** 和 **`Restaurant2`** 欄。 如果 **`Restaurant1`** > **`Restaurant2`，** 您應該能夠檢視 *牛排* 其他食物， *泰文* 食品影像會顯示在您的熒幕上。

   ![result5](assets/result5.gif)

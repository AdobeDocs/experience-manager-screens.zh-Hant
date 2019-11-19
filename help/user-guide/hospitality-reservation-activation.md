---
title: 酒店預訂激活
seo-title: 酒店預訂激活
description: 下列使用案例說明如何根據Google工作表中填入的值啟用醫院預訂。
seo-description: 下列使用案例說明如何根據Google工作表中填入的值啟用醫院預訂。
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 酒店預訂激活 {#hospitality-reservation-activation}

下列使用案例說明如何根據Google工作表中填入的值啟用醫院預訂。

## 說明 {#description}

在此使用案例中，Google Sheet會填入兩間餐廳 **Restaurant1** 和 **Restaurant2的預訂百分比**。 公式會根據Restaurant1和Restaurant2的值套用，並根據公式，值1或2會指派給 **AdTarget** 欄。

如果 **Restaurant1** **Restaurant2的值，則** AdTaget **被指定值***否則，********** AdTarget被指定值為2AdTarget。 Value 1會產 *生Steak food* option（牛排食品），而Value 2會在顯示畫面 *上顯示Thai* food（泰式食品）選項。

## 先決條件 {#preconditions}

在開始實作保留啟動之前，您必須瞭解如何在AEM Screens專案中設定 ***Data Store***、 ***Audience Segmentation******和Enable Targeting for Channels*** 。

如需詳細 [資訊，請參閱「在AEM畫面中設定ContextHub](configuring-context-hub.md) 」。

## 基本流程 {#basic-flow}

請依照下列步驟，為您的AEM Screens專案實作酒店預訂啟動使用案例：

1. **填入Google工作表並新增公式。**

   例如，將公式套用至第三欄 **AdTarget**，如下圖所示。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **根據需求在「對象」中設定區段**

   1. 導覽至對象中的區段(請參 ***閱步驟2:在「在AEM畫面中設定ContextHub*** 」(** [在AEM Screens](configuring-context-hub.md)**頁面中設定觀眾區隔)，以取得詳細資訊。

   1. 選擇「 **工作表A1 1** 」，然後單 **擊編輯**。

   1. 選擇比較屬性，然後按一下設定圖示以編輯屬性。
   1. 從屬 **性名稱的下拉式清單中選取** 「Googlesheets/value/1/2 **」**

   1. 從下 **拉式選單中** ，將運算子選取為**equal **

   1. 將值 **輸入****為1**

   1. 同樣地，選擇**工作表A1 2 **並按一下「編 **輯」**。

   1. 選擇比較屬性，然後按一下設定圖示以編輯屬性。
   1. 從屬 **性名稱的下拉式清單中選取** 「Googlesheets/value/1/2 **」**

   1. 將運算 **元選** 為 **2**

1. 導覽並選取您的頻道()，然後從動作 **列按一下** 「編輯」。 在下列範例中 **,DataDrivenRestaurant**，會使用循序頻道來展示功能。

   >[!NOTE]
   >
   >您的頻道應已擁有預設影像，且應依「在AEM畫面中設定ContextHub」中所述，預先 [設定觀眾](configuring-context-hub.md)。

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >您應該已使用「屬 **性」(Properties** ) **&gt;「個人化」(Personalization** **ContextHub)頁籤來設定ContextHub****** Configurations。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 從編 **輯器中選取** 「定位」，然後從下拉式選單中選取「品牌 **」和「活動** 」，然後按一下「 ********&#x200B;開始定位」。
1. **勾選預覽**

   1. 按一下「 **預覽」。** 此外，請開啟您的Google工作表並更新其值。
   1. 更新 **Restaurant1和****Restaurant2欄中的值** 。 如果 **Restaurant1** &gt; **Restaurant2,** 您應該可以檢視牛排食品的影像，否則，您的螢幕上會 **** 顯示泰式食品的影像。
   ![result5](assets/result5.gif)


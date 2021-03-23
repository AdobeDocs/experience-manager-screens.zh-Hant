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
feature: 製作畫面
role: 管理員、開發人員
level: 中級
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---


# 酒店預訂激活{#hospitality-reservation-activation}

下列使用案例說明如何根據Google工作表中填入的值啟用醫院預訂。

## 說明 {#description}

在此使用案例中，Google Sheet會填入兩間餐廳&#x200B;**Restaurant1**&#x200B;和&#x200B;**Restaurant2**&#x200B;的預訂百分比。 公式根據Restaurant1和Restaurant2的值套用，並根據公式將值1或2指派給&#x200B;**AdTarget**&#x200B;欄。

如果&#x200B;**Restaurant1**>**Restaurant2**&#x200B;的值，則&#x200B;**AdTaget**&#x200B;被指派值&#x200B;**1**&#x200B;否則&#x200B;**AdTarget**&#x200B;被指派值&#x200B;**2**... 值1生成&#x200B;*牛排食品*&#x200B;選項，值2在顯示屏上顯示&#x200B;*泰式食品*&#x200B;選項。

## 先決條件{#preconditions}

在開始實作保留啟動之前，您必須瞭解如何在AEM Screens專案中設定&#x200B;***資料商店***、***受眾細分***&#x200B;和&#x200B;***啟用頻道定位***。

如需詳細資訊，請參閱「在AEM Screens設定ContextHub」。[](configuring-context-hub.md)

## 基本流{#basic-flow}

請依照下列步驟，為您的AEM Screens專案實作酒店預訂啟動使用案例：

1. **填入Google工作表並新增公式。**

   例如，將公式套用至第三欄&#x200B;**AdTarget**，如下圖所示。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **根據需求在「對象」中設定區段**

   1. 導覽至對象中的區段(請參閱&#x200B;***步驟2:在&#x200B;**[設定AEM Screens](configuring-context-hub.md)**頁面的ContextHub中設定「觀眾區隔」，以取得詳細資訊)。***

   1. 選擇&#x200B;**工作表A1 1**，然後按一下&#x200B;**編輯**。

   1. 選擇比較屬性，然後按一下設定圖示以編輯屬性。
   1. 從&#x200B;**屬性名稱**&#x200B;的下拉式清單中選擇&#x200B;**googlessheets/value/1/2**

   1. 從下拉菜單中選擇&#x200B;**Operator**&#x200B;作為&#x200B;**equal**

   1. 將&#x200B;**Value**&#x200B;輸入為&#x200B;**1**

   1. 同樣，選擇&#x200B;**工作表A1 2**&#x200B;並按一下&#x200B;**編輯**。

   1. 選擇比較屬性，然後按一下設定圖示以編輯屬性。
   1. 從&#x200B;**屬性名稱**&#x200B;的下拉式清單中選擇&#x200B;**googlessheets/value/1/2**

   1. 選擇&#x200B;**運算子**&#x200B;作為&#x200B;**2**

1. 導覽並選取您的頻道()，然後從動作列按一下「編輯&#x200B;**」。**&#x200B;在以下範例中，**DataDrivenRestaurant**&#x200B;會使用循序頻道來展示功能。

   >[!NOTE]
   >
   >您的頻道應已有預設影像，且應依[在AEM Screens設定ContextHub中所述預先設定觀眾。](configuring-context-hub.md)

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >您應使用渠道&#x200B;**屬性** —> **個人化**&#x200B;標籤設定&#x200B;**ContextHub** **配置**。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 從編輯器中選擇&#x200B;**Targeting**，然後從下拉式選單中選擇&#x200B;**Brand**&#x200B;和&#x200B;**Activity**，然後按一下「開始定位&#x200B;**」。**
1. **勾選預覽**

   1. 按一下「預覽」。**** 此外，請開啟您的Google工作表並更新其值。
   1. 更新&#x200B;**Restaurant1**&#x200B;和&#x200B;**Restaurant2**&#x200B;欄中的值。 如果&#x200B;**Restaurant1** > **Restaurant2,**&#x200B;您應該能夠檢視&#x200B;*Steak*&#x200B;食品的影像，則螢幕上會顯示&#x200B;*Thai*&#x200B;食品影像。

   ![結果5](assets/result5.gif)


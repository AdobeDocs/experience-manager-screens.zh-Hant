---
title: 酒店預訂激活
seo-title: 酒店預訂激活
description: 下列使用案例示範如何根據Google工作表中填入的值啟用醫院預留。
seo-description: 下列使用案例示範如何根據Google工作表中填入的值啟用醫院預留。
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
feature: 製作畫面
role: Administrator, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# 酒店預訂激活{#hospitality-reservation-activation}

下列使用案例示範如何根據Google工作表中填入的值啟用醫院預留。

## 說明 {#description}

對於此使用案例，Google工作表中會填入兩間餐廳&#x200B;**Restaurant1**&#x200B;和&#x200B;**Restaurant2**&#x200B;的預訂百分比。 公式根據Restaurant1和Restaurant2的值套用，並根據公式將值1或2指派給&#x200B;**AdTarget**&#x200B;欄。

如果值&#x200B;**Restaurant1** > **Restaurant2**，則為&#x200B;**AdTaget**&#x200B;分配值&#x200B;**1**&#x200B;否則為&#x200B;**AdTarget**&#x200B;分配值&#x200B;**2**。 值1生成&#x200B;*牛排食品*&#x200B;選項，值2在您的顯示屏上顯示&#x200B;*泰式食品*&#x200B;選項。

## 先決條件 {#preconditions}

開始實作保留啟用前，您必須了解如何在AEM Screens專案中設定&#x200B;***Data Store***、***受眾細分***&#x200B;和&#x200B;***啟用頻道目標鎖定***。

如需詳細資訊，請參閱[在AEM Screens中設定ContextHub ](configuring-context-hub.md) 。

## 基本流{#basic-flow}

請依照下列步驟，為您的AEM Screens專案實作旅館業保留啟用使用案例：

1. **填入Google工作表並新增公式。**

   例如，將公式套用至第三欄&#x200B;**AdTarget**，如下圖所示。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **根據需求在受眾中設定區段**

   1. 導覽至對象中的區段(請參閱&#x200B;***步驟2:在「在AEM Screens ](configuring-context-hub.md)**中設定ContextHub」頁面中設定「對象區段」***以取得詳細資訊)。**[

   1. 選擇&#x200B;**工作表A1 1**，然後按一下&#x200B;**編輯**。

   1. 選取比較屬性，然後按一下設定圖示以編輯屬性。
   1. 從&#x200B;**屬性名稱**&#x200B;中的下拉式清單中選擇&#x200B;**googlesheets/value/1/2**

   1. 從下拉式選單中選取&#x200B;**Operator**&#x200B;作為&#x200B;**equal**

   1. 將&#x200B;**值**&#x200B;輸入為&#x200B;**1**

   1. 同樣地，選擇&#x200B;**工作表A1 2**&#x200B;並按一下&#x200B;**編輯**。

   1. 選取比較屬性，然後按一下設定圖示以編輯屬性。
   1. 從&#x200B;**屬性名稱**&#x200B;中的下拉式清單中選擇&#x200B;**googlesheets/value/1/2**

   1. 選擇&#x200B;**Operator**&#x200B;作為&#x200B;**2**

1. 導覽並選取您的通道()，然後按一下動作列中的&#x200B;**Edit** 。 在以下示例中， **DataDrivenRestaurant**&#x200B;使用循序通道來展示功能。

   >[!NOTE]
   >
   >您的管道應已有預設影像，且應依[在AEM Screens中設定ContextHub中所述預先設定對象。](configuring-context-hub.md)

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >您應該已使用通道&#x200B;**屬性** —> **個人化**&#x200B;標籤設定&#x200B;**ContextHub** **配置**。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 從編輯器中選擇&#x200B;**目標定位**，然後從下拉式選單中選擇&#x200B;**品牌**&#x200B;和&#x200B;**活動**，然後按一下&#x200B;**開始定位**。
1. **勾選預覽**

   1. 按一下「**預覽」。** 此外，請開啟您的Google工作表並更新其值。
   1. 更新&#x200B;**Restaurant1**&#x200B;和&#x200B;**Restaurant2**&#x200B;欄中的值。 如果&#x200B;**Restaurant1** > **Restaurant2,**&#x200B;您應該能夠查看&#x200B;*牛排*&#x200B;食品的影像，否則，螢幕上將顯示&#x200B;*泰國*&#x200B;食品影像。
   ![結果5](assets/result5.gif)

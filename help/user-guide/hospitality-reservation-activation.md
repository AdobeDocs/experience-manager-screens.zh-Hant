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
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Hospitality Reservation Activation {#hospitality-reservation-activation}

下列使用案例示範如何根據Google Sheets中填入的值，使用醫院預約啟用。

## 說明 {#description}

在此使用案例中，Google工作表會填入兩個餐廳&#x200B;**`Restaurant1`**&#x200B;和&#x200B;**`Restaurant2`**&#x200B;上的預訂百分比。 根據`Restaurant1`和`Restaurant2`的值套用公式，並根據公式，將值1或2指派給&#x200B;**AdTarget**&#x200B;資料行。

如果&#x200B;**`Restaurant1`** > **`Restaurant2`**&#x200B;的值，則&#x200B;**AdTaget**&#x200B;會指派值&#x200B;**1**，否則&#x200B;**AdTarget**&#x200B;會指派值&#x200B;**2**。 值1會產生&#x200B;*牛排食品*&#x200B;選項，而值2會在您的熒幕上顯示&#x200B;*泰式食品*&#x200B;選項。

## 先決條件 {#preconditions}

開始實作保留區啟用之前，請先瞭解如何設定&#x200B;***資料存放區***、***對象細分***&#x200B;和&#x200B;***在AEM Screens專案中啟用管道***&#x200B;的鎖定目標。

如需詳細資訊，請參閱[在AEM Screens中設定ContextHub](configuring-context-hub.md)。

## 基本流量 {#basic-flow}

請依照下列使用案例步驟，為您的AEM Screens專案實作旅館業保留啟用：

1. **填入Google工作表並新增公式**。

   例如，將公式套用至第三欄&#x200B;**AdTarget**，如下圖所示。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **根據需求設定對象中的區段**

   1. 導覽至您對象中的區段(如需詳細資訊，請參閱&#x200B;**[在AEM Screens中設定ContextHub](configuring-context-hub.md)**&#x200B;頁面中的&#x200B;***步驟2：設定對象細分***)。
   1. 按一下&#x200B;**工作表A1 1**&#x200B;並按一下&#x200B;**編輯**。
   1. 按一下比較屬性，然後按一下&#x200B;**組態**&#x200B;圖示。
   1. 從&#x200B;**屬性名稱**&#x200B;的下拉式清單中，按一下&#x200B;**google工作表/value/1/2**。
   1. 從下拉式功能表中按一下&#x200B;**運運算元**&#x200B;做為&#x200B;**equal**。
   1. 輸入&#x200B;**值**&#x200B;作為&#x200B;**1**。
   1. 同樣地，按一下&#x200B;**工作表A1 2**&#x200B;並按一下&#x200B;**編輯**。
   1. 按一下比較屬性，然後按一下&#x200B;**組態**&#x200B;圖示。
   1. 從&#x200B;**屬性名稱**&#x200B;的下拉式清單中，按一下&#x200B;**google工作表/value/1/2**。
   1. 按一下&#x200B;**運運算元**&#x200B;做為&#x200B;**2**。

1. 瀏覽並按一下您的頻道()，然後按一下動作列中的&#x200B;**編輯**。 在下列範例&#x200B;**DataDrivenRestaurant**&#x200B;中，使用循序頻道來展示功能。

   >[!NOTE]
   >
   >您的頻道應該已有預設影像，且對象應該已預先設定，如[在AEM Screens中設定ContextHub](configuring-context-hub.md)中所述。

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >您目前應該已經設定使用管道&#x200B;**屬性** > **Personalization**&#x200B;索引標籤的&#x200B;**ContextHub** **設定**。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. 從編輯器按一下&#x200B;**鎖定目標**，然後從下拉式功能表按一下&#x200B;**品牌**&#x200B;和&#x200B;**活動**，然後按一下&#x200B;**開始鎖定目標**。
1. **正在檢查預覽**

   1. 按一下「**預覽」。**&#x200B;也請開啟您的Google工作表並更新其值。
   1. 更新&#x200B;**`Restaurant1`**&#x200B;和&#x200B;**`Restaurant2`**&#x200B;欄中的值。 若&#x200B;**`Restaurant1`** > **`Restaurant2`，**，您應該可以檢視&#x200B;*牛排*&#x200B;食物的影像，否則，熒幕上會顯示&#x200B;*泰文*&#x200B;食物的影像。

   ![結果5](assets/result5.gif)

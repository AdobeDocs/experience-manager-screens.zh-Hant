---
title: 使用資料觸發器製作
description: 進一步瞭解如何在AEM Screens頻道中使用資料觸發器進行創作。
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 1%

---

# 使用資料觸發器製作 {#authoring-with-data-triggers}

本節著重說明如何在您的管道中啟用鎖定目標。

>[!IMPORTANT]
>
>AEM Screens管道中支援資料觸發程式的最低版本為AEM 6.5.3 Feature Pack 3。

## 先決條件 {#prereqs}

在依照下列步驟在管道中啟用鎖定目標之前，請先瞭解在AEM Screens中設定所需的[重要條款](configuring-context-hub.md)，以瞭解AEM Screens中的ContextHub和鎖定目標。

>[!IMPORTANT]
>
>在AEM Screens頻道中啟用鎖定目標之前，建議您先瞭解並設定ContextHub設定。

如需詳細資訊，請遵循下列連結：

1. **[設定資料存放區](configuring-context-hub.md)**
1. **[設定對象細分](configuring-context-hub.md)**

完成上述步驟後，您就可以在頻道中啟用鎖定目標功能。

## 使用Data Triggers製作概述 {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## 在AEM Screens頻道中啟用鎖定目標 {#enabling-targeting}

請依照下列步驟，在您的管道中啟用目標定位。

1. 導覽至其中一個AEM Screens管道。 下列步驟示範如何使用在AEM Screens頻道中建立的&#x200B;**DataDrivenRetail** *（順序頻道）*&#x200B;來啟用鎖定目標。

1. 按一下頻道&#x200B;**DataDrivenRetail**，然後從動作列按一下&#x200B;**屬性**。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 按一下&#x200B;**Personalization**&#x200B;標籤，以便您可以設定ContextHub設定，然後按一下ContextHub和區段路徑。

   1. 按一下&#x200B;**ContextHub路徑**&#x200B;做為&#x200B;**libs** > **設定** > **cloudsettings** > **預設** > **ContextHub設定**，然後按一下&#x200B;**按一下**。

   1. 按一下&#x200B;**區段路徑**&#x200B;做為&#x200B;**conf** > **`We.Retail`** > **設定** > **wcm** > **區段**，然後按一下&#x200B;**按一下**。

   1. 按一下&#x200B;**「儲存並關閉」**。

   >[!NOTE]
   >
   >使用ContextHub和區段路徑，您最初會在此儲存您的ContextHub設定和區段。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. 瀏覽並按一下&#x200B;**DataDrivenAssets** > **管道**&#x200B;中的&#x200B;**DataDrivenRetail**，然後按一下動作列中的&#x200B;**編輯**。 在管道編輯器中拖放資產。

   >[!NOTE]
   >
   >如果您已正確設定所有專案，您會在編輯器的下拉式清單中看到&#x200B;**鎖定目標**&#x200B;選項，如下圖所示。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. 按一下&#x200B;**鎖定目標**。

1. 從下拉式功能表按一下&#x200B;**品牌**&#x200B;和&#x200B;**活動**，然後按一下&#x200B;**開始鎖定目標**。

### 瞭解更多：範例使用案例 {#learn-more-example-use-cases}

為您的AEM Screens專案設定ContextHub後，您可以依照不同的使用案例來瞭解資料觸發的資產如何在不同產業中扮演重要角色：

1. **[零售庫存目標啟動](retail-inventory-activation.md)**
1. **[旅行中心溫度啟用](local-temperature-activation.md)**
1. **[旅館預訂啟用](hospitality-reservation-activation.md)**

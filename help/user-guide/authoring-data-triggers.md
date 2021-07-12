---
title: 使用資料觸發器製作
seo-title: 使用資料觸發器製作
description: 請詳閱本頁，了解如何使用資料觸發器製作。
feature: 製作畫面
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 1%

---

# 使用資料觸發器製作 {#authoring-with-data-triggers}

本節重點說明如何在您的管道中啟用定位。

>[!IMPORTANT]
>
>支援AEM Screens管道中資料觸發器的最低版本為AEM 6.5.3 Feature Pack 3。

## 必備條件 {#prereqs}

您必須先了解在AEM Screens中設定[重要術語，才能依照下列步驟在管道中啟用定位，這是了解AEM Screens中的ContextHub和定位所需的。](configuring-context-hub.md)

>[!IMPORTANT]
>
>建議您先了解並設定ContextHub設定，再在AEM Screens管道中啟用目標定位。

如需詳細資訊，請遵循下列連結：

1. **[設定資料儲存](configuring-context-hub.md)**
1. **[設定受眾細分](configuring-context-hub.md)**

完成上述步驟後，您就可以在管道中啟用定位。

## 使用Data Triggers編寫概述 {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## 在AEM Screens管道中啟用鎖定目標 {#enabling-targeting}

請依照下列步驟，在您的管道中啟用鎖定目標。

1. 導覽至其中一個AEM Screens管道。 下列步驟示範如何使用在AEM Screens管道中建立的&#x200B;**DataDrivenRetail** *（序列管道）*&#x200B;來啟用定位。

1. 選擇通道&#x200B;**DataDrivenRetail**，然後從操作欄按一下&#x200B;**屬性**。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 選取&#x200B;**Personalization**&#x200B;標籤以設定ContextHub設定，並選取ContextHub和區段路徑。

   1. 選擇&#x200B;**ContextHub路徑**&#x200B;作為&#x200B;**libs**> **settings**> **cloudsettings** > **default** > **ContextHub配置**，然後按一下&#x200B;**選擇**。

   1. 選擇&#x200B;**段路徑**&#x200B;作為&#x200B;**conf** > **We.Retail** > **settings** > **wcm** > **段**，然後按一下&#x200B;**選擇**。

   1. 按一下&#x200B;**「儲存並關閉」**。
   >[!NOTE]
   >
   >使用ContextHub和區段路徑，您最初會在此儲存內容中樞設定和區段。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. 從&#x200B;**DataDrivenAssets** > **Channels**&#x200B;導航並選擇&#x200B;**DataDrivenRetail**，然後從操作欄按一下&#x200B;**Edit**。 將資產拖放至管道編輯器中。

   >[!NOTE]
   >
   >如果您已正確設定所有項目，您會在編輯器的下拉式清單中看到「**目標定位**」選項，如下圖所示。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. 按一下&#x200B;**目標定位**。

1. 從下拉式選單中選取&#x200B;**Brand**&#x200B;和&#x200B;**Activity**，然後按一下&#x200B;**Start Targeting**。

### 更多詳情：範例使用案例 {#learn-more-example-use-cases}

為AEM Screens專案設定ContextHub後，您可以遵循不同的使用案例來了解資料觸發資產在不同產業中扮演重要角色的方式：

1. **[零售庫存目標激活](retail-inventory-activation.md)**
1. **[旅行中心溫度激活](local-temperature-activation.md)**
1. **[酒店預訂激活](hospitality-reservation-activation.md)**

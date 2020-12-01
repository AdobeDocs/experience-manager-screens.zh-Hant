---
title: 使用資料觸發器製作內容
seo-title: 使用資料觸發器製作內容
description: 請依本頁瞭解如何使用資料觸發程式來編寫。
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 1%

---


# 使用資料觸發器製作{#authoring-with-data-triggers}

本節重點說明如何在您的通道中啟用定位。

>[!IMPORTANT]
>
>支援AEM Screens頻道中資料觸發器的最低版本為AEM 6.5.3 Feature Pack 3。

## 必備條件 {#prereqs}

在遵循下列步驟以啟用頻道中的定位之前，您必須先瞭解瞭解瞭解AEM Screens中ContextHub和Targeting的[ Key Terms in Configuring in AEM Screens](configuring-context-hub.md)。

>[!IMPORTANT]
>
>建議您先瞭解並設定ContextHub組態，再在AEM Screens頻道中啟用定位。

請依照下列連結取得詳細資訊：

1. **[設定資料儲存區](configuring-context-hub.md)**
1. **[設定受眾細分](configuring-context-hub.md)**

完成上述步驟後，您就可以在通道中啟用定位。

## 使用資料觸發器製作內容概述{#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## 在AEM畫面頻道{#enabling-targeting}中啟用定位

請依照下列步驟，在您的通道中啟用定位。

1. 導覽至其中一個AEM Screens頻道。 下列步驟示範如何使用在AEM Screens頻道中建立的&#x200B;**DataDrivenRetail** *（序列頻道）*&#x200B;啟用定位。

1. 選擇渠道&#x200B;**DataDrivenRetail**，然後從操作欄中按一下「屬性」。****

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 選擇&#x200B;**個人化**&#x200B;標籤以設定ContextHub組態，並選擇ContextHub和Segments路徑。

   1. 選擇&#x200B;**ContextHub路徑**&#x200B;作為&#x200B;**libs** > **settings** > **cloudsettings** > **default** > **ContextHub配置**&#x200B;並按一下&#x200B;**選擇**。

   1. 選擇&#x200B;**區段路徑**&#x200B;作為&#x200B;**conf** > **We.Retail** > **settings** > **wcm**>區段&#x200B;**，然後按一下**&#x200B;選擇&#x200B;**。**

   1. 按一下&#x200B;**「儲存並關閉」**。
   >[!NOTE]
   >
   >使用ContextHub和區段路徑，您最初在此儲存上下文中心組態和區段。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. 從&#x200B;**DataDrivenAssets** > **Channels**&#x200B;導覽並選取&#x200B;**DataDrivenRetail**，然後從動作列按一下&#x200B;**Edit**。 將資產拖放至渠道編輯器。

   >[!NOTE]
   >
   >如果您已正確設定所有項目，您會從編輯器的下拉式清單中看到&#x200B;**定位**&#x200B;選項，如下圖所示。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. 按一下「**定位**」。

1. 從下拉式選單中選擇&#x200B;**品牌**&#x200B;和&#x200B;**活動**，然後按一下「開始定位&#x200B;**」。**

### 更多資訊：範例使用案例{#learn-more-example-use-cases}

在您為AEM Screens專案設定ContextHub後，您可以依照不同的使用案例來瞭解資料觸發資產在不同產業中扮演重要角色的方式：

1. **[零售庫存鎖定](retail-inventory-activation.md)**
1. **[旅行中心溫度激活](local-temperature-activation.md)**
1. **[酒店預訂激活](hospitality-reservation-activation.md)**

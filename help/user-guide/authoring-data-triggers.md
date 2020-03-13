---
title: 使用資料觸發器製作內容
seo-title: 使用資料觸發器製作內容
description: 請依本頁瞭解如何使用資料觸發程式來編寫。
translation-type: tm+mt
source-git-commit: 9490eb2aa089268884d0f39a32eb8c53de110ed7

---


# 使用資料觸發器製作內容 {#authoring-with-data-triggers}

本節重點說明如何在您的通道中啟用定位。

>[!IMPORTANT]
> 支援AEM Screens頻道中資料觸發器的最低版本為AEM 6.4.3 Feature Pack 3。

## 必備條件 {#prereqs}

在遵循下列步驟以啟用頻道中的定位之前，您必須先瞭解在AEM Screens中設定的關鍵詞語 [](configuring-context-hub.md) ，以瞭解在AEM Screens中的ContextHub和定位。

>[!IMPORTANT]
> 建議您先瞭解並設定ContextHub組態，再在AEM Screens頻道中啟用定位。

請依照下列連結取得詳細資訊：

1. **[設定資料儲存區](configuring-context-hub.md)**
1. **[設定受眾細分](configuring-context-hub.md)**

完成上述步驟後，您就可以在通道中啟用定位。

## 使用資料觸發器製作內容概觀 {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## 在AEM畫面頻道中啟用定位 {#enabling-targeting}

請依照下列步驟，在您的通道中啟用定位。

1. 導覽至其中一個AEM Screens頻道。 下列步驟示範如何使用在AEM畫面頻道中建 **立的DataDrivenRetail***（序列頻道）* ，來啟用定位。

1. 選取渠道 **DataDrivenRetail** ，然後從動作列 **按一下「屬性** 」。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 選擇「個 **人化** 」標籤以設定ContextHub組態。

   1. 選擇ContextHub路徑 **,** 作為libs **>** settings **> Default Settings** > Default Zetings ****************> Configurations Journations CloudSelectLoudLouds。

   1. 選擇「路徑 **」** 段作為「會議 **」** >「零售」 **>「零售」>「****************** WcmSegments」>「AldSignments」>「ChickSelectSelectLight」。

   1. 按一 **下儲存並關閉**。
   >[!NOTE]
   >
   >使用ContextHub和區段路徑，您最初在此儲存上下文中心組態和區段。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. 從DataDriven Assets > **Channels中導覽並選取** DataDriven Retail **，然後從動作列** 按一下Edit ******** Driven Retail。

   >[!NOTE]
   >
   >如果您已正確設定所有項目，您會從編輯器的下拉式清單中看到 **Targeting** （定位）選項，如下圖所示。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   >
   >為渠道配置ContextHub配置後，如果您要遵循下列所有使用案例，請務必遵循1到4的前述步驟，對於其他三個順序渠道亦然。

### 更多資訊：範例使用案例 {#learn-more-example-use-cases}

在您為AEM Screens專案設定ContextHub後，您可以依照不同的使用案例來瞭解資料觸發資產在不同產業中扮演重要角色的方式：

1. **[零售庫存鎖定](retail-inventory-activation.md)**
1. **[旅行中心溫度激活](local-temperature-activation.md)**
1. **[酒店預訂激活](hospitality-reservation-activation.md)**


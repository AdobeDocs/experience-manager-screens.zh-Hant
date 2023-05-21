---
title: 使用資料觸發器創作
seo-title: Authoring with Data Triggers
description: 按照此頁瞭解如何使用資料觸發器編寫。
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 1%

---

# 使用資料觸發器創作 {#authoring-with-data-triggers}

本部分重點介紹如何在渠道中啟用目標。

>[!IMPORTANT]
>
>支援AEM Screens通道中資料觸發器的最低版本AEM為6.5.3 Feature Pack 3。

## 必備條件 {#prereqs}

在執行以下步驟以在渠道中啟用目標之前，必須瞭解 [配置關鍵術語在AEM Screens](configuring-context-hub.md) 在AEM Screens瞭解ContextHub和目標。

>[!IMPORTANT]
>
>建議您先瞭解並設定ContextHub配置，然後在AEM Screens渠道中啟用目標。

有關詳細資訊，請遵循以下連結：

1. **[設定資料儲存](configuring-context-hub.md)**
1. **[設定受眾細分](configuring-context-hub.md)**

完成上述步驟後，即可在通道中啟用目標。

## 使用資料觸發器創作概述 {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## 在AEM Screens頻道啟用目標 {#enabling-targeting}

按照以下步驟在您的渠道中啟用目標。

1. 導航到其中一個AEM Screens頻道。 以下步驟演示如何使用 **資料驅動零售** *（序列通道）* 在AEM Screens頻道創作。

1. 選擇頻道 **資料驅動零售** 按一下 **屬性** 按鈕。

   ![screen_shot_2019-05-01at4332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 選擇 **個性化** 頁籤，以設定ContextHub配置並選擇ContextHub和Segments路徑。

   1. 選擇 **上下文中心路徑** 如 **液體** > **設定** > **雲設定** > **預設** > **ContextHub配置** 按一下 **選擇**。

   1. 選擇 **段路徑** 如 **會議** > **We.Retail** > **設定** > **寬** > **段** 按一下 **選擇**。

   1. 按一下&#x200B;**「儲存並關閉」**。
   >[!NOTE]
   >
   >使用ContextHub和Segments路徑，在其中您最初保存了上下文中心配置和段。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. 導航並選擇 **資料驅動零售** 從 **資料驅動資產** > **頻道** 按一下 **編輯** 按鈕。 在頻道編輯器中拖放資源。

   >[!NOTE]
   >
   >如果您已正確設定所有內容，您將看到 **目標** 的子菜單。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. 按一下 **目標**。

1. 選擇 **品牌** 和 **活動** 按一下 **開始目標**。

### 瞭解詳情：示例使用案例 {#learn-more-example-use-cases}

在為AEM Screens項目配置ContextHub後，您可以按照不同的使用案例來瞭解資料觸發的資產如何在不同的行業中扮演關鍵角色：

1. **[零售庫存目標激活](retail-inventory-activation.md)**
1. **[旅行中心溫度激活](local-temperature-activation.md)**
1. **[酒店預訂激活](hospitality-reservation-activation.md)**

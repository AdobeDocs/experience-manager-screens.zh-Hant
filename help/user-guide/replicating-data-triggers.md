---
title: 將資料觸發器複製到發佈伺服器
seo-title: Replicate data-triggers to publish server
description: 按照此頁瞭解如何將資料觸發器複製到發佈伺服器。
seo-description: Replicate data-triggers to publish server.
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 2%

---

# 將資料觸發器複製到發佈伺服器 {#replicating-data-triggers}

當使用ContextHub和AEMTargeting Engine根據作者/發佈設定中的資料觸發器自定義內容時，所有與ContextHub和Personal化相關的配置在發佈時不會與頻道自動複製。

按照本頁瞭解單獨發佈這些配置所需的手冊步驟。

這主要歸結於手動發佈：

1. ContextHub儲存和UI模組配置
1. 個性化觀眾
1. 個性化活動

## 將資料觸發器複製到發佈伺服器的步驟 {#replicating-data-triggers-publish}

按照以下步驟將資料觸發器複製到發佈伺服器。

### 步驟1:複製ContextHub配置 {#replicating-contexthub-configurations}

1. 導航到 **工具** > **部署** > **分佈** > **發佈代理** 然後按一下發佈代理以配置設定。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >或者，可以使用 `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` 直接導航到螢幕以配置和test連接。

1. 按一下 **Test連接** 從操作欄驗證作者與發佈實例的通信，如下圖所示。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >如果test失敗，您需要修復作者和發佈實例之間的複製代理配置。 請參閱 [疑難解答Test連接](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) 的子菜單。

1. 選擇 **添加** 從 **分發代理** 螢幕樹並選擇項目的配置路徑，例如， `/conf/screens/settings/cloudsettings/configuration`。

1. 按一下 **提交**。

### 複製受眾 {#replicating-audiences}

1. 導航到實AEM例> **個性化** > **觀眾** 或 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` 導航。

1. 深入到項目資料夾，例如， `/conf/screens/`。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. 從用戶介面中選擇所有受眾和段。

1. 按一下 **管理發布** 按鈕。

1. 按一下 **下一個** 和 **發佈**。

### 複製活動  {#replicating-activities}

1. 導航到實AEM例> **個性化** > **活動** 或 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` 導航。

1. 深入到項目資料夾， `/content/campaigns/screens/…`。

1. 從用戶介面中選擇所有活動。

1. 按一下 **管理發布** 按鈕。

1. 按一下 **下一個** 和 **發佈**。

>[!IMPORTANT]
>
>複製ContextHub配置和受眾是在項目設定期間完成的，同時複製活動，每次在渠道內更改目標時都需要複製活動。

#### 結果 {#result}

如果複製成功，則應查看發佈實例（或項目的類似結構）上的以下結構：

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 疑難解答Test連接 {#troubleshoot-test}

如果test連接在複製ContextHub配置時失敗，請按照以下部分排除此問題：

1. 導航到「工具」> **部署** > **分佈** > **發佈代理**。

1. 按一下 **編輯** 從操作欄中，確保中的終結點URL **導入程式終結點** 欄位還指向分發代理中的發佈伺服器URL。
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. 如果不使用預設的管理員憑據，則需要使用不同的用戶名和密碼配置分發代理。

   請遵循下列步驟：

   1. 導航到「工具」> **操作** > **Web控制台** `http://localhost:4502/system/console/configMgr`開啟 **Adobe Experience ManagerWeb控制台螢幕**。
   1. 搜索 **Apache Sling分發傳輸憑據 — 基於用戶憑據的DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 通過填充 **名稱**。 **用戶名** 和 **密碼**，例如， *slingTransportSecretProvider*。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. 按一下 **保存**
   1. 使用 `Cmd +F` 搜索 **Apache Sling分發代理 — 轉發代理工廠** 開啟配置並搜索 **傳輸機密提供程式**。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. 更新 `(name=default)` 與 `(name=slingTransportSecretProvider)`。
   1. 按一下 **保存** 並再次運行test連接 **分發代理** 從實例中重AEM新篩選。

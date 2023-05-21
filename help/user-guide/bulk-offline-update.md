---
title: 批量離線更新
seo-title: Bulk Offline Update
description: 按照本頁瞭解如何批量更新所有通道。
seo-description: Follow this page to learn how you can update all the channels in bulk.
uuid: 9b52c5e7-aa6d-4f55-b23c-8bd923723552
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 5d4ca652-d918-4b2b-b239-a2be9255ef0d
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d0a0b065-798e-4108-86ac-0a1f4e211cfc
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# 批量離線更新 {#bulk-offline-update}

本節介紹「批量離線更新」的以下主題：

* **概觀**
* **使用批量離線更新**

>[!CAUTION]
>
>只有安裝了6.3功能包3或AEM6.4螢幕功能包1時，才AEM能使用此AEM Screens功能。
>
>要訪問此功能包，必須聯繫Adobe支援並請求訪問。 擁有權限後，您可以從包共用下載它。

## 概觀 {#overview}

批量離線更新，允許您批量更新所有通道。 它避免了導航到特定頻道和更新內容的麻煩。 相反，您可以在一個瞬間更新特定項目的頻道中的所有內容。

您還可以將此活動安排在較低網路流量的時間內。

>[!NOTE]
>
>「批量離線更新」功能已優化，只更新那些已修改的通道。

## 使用批量離線更新 {#using-bulk-offline-update}

您可以手動使用用戶介面(UI)中的批量離線更新，或從OSGi服務計畫批量更新。

### 使用AEM Screens用戶介面 {#using-aem-screens-user-interface}

按照以下步驟為AEM Screens項目使用批量離線更新：

1. 導航到您的AEM Screens項目。
1. 選擇項目並按一下 **更新離線內容** 的子菜單。

   ![screen_shot_2018-04-24at12256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Adobe Experience ManagerWeb控制台配置 {#adobe-experience-manager-web-console-configuration}

按照以下步驟為AEM Screens項目使用批量離線更新：

1. Adobe Experience ManagerWeb控制台配置。
1. 搜索批量離線更新服務。

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. 添加以下屬性：

   **項目路徑** 指定AEM Screens項目的路徑。 路徑通常 `/content/screens/<Name of your project>`。

   *例如*。 `/content/screens/we-retail`。 通過選擇AEM Screens下的任何項目（請勿按滑鼠該表徵圖），可以在URL中找到此路徑。

   >[!NOTE]
   >
   >指定相對於渠道的項目路徑。

   **計畫頻率** 指定此服務應更新離線內容的時間，例如，下午5:00或17:00。

1. 按一下 **保存** 保存設定，您的內容將在指定時間更新。

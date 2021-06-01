---
title: 大量離線更新
seo-title: 大量離線更新
description: 請詳閱本頁，了解如何大量更新所有管道。
seo-description: 請詳閱本頁，了解如何大量更新所有管道。
uuid: 9b52c5e7-aa6d-4f55-b23c-8bd923723552
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 5d4ca652-d918-4b2b-b239-a2be9255ef0d
noindex: true
feature: 製作畫面
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# 大量離線更新{#bulk-offline-update}

本節涵蓋下列關於大量離線更新的主題：

* **概覽**
* **使用大量離線更新**

>[!CAUTION]
>
>只有在您已安裝AEM 6.3 Feature Pack 3或AEM 6.4 Screens Feature Pack 1時，才能使用此AEM Screens功能。
>
>若要存取此Feature Pack，您必須聯絡Adobe支援並要求存取權。 擁有權限後，您就可以從「封裝共用」下載。

## 概覽 {#overview}

「大量離線更新」，可讓您大量更新所有通道。 避免導覽至特定頻道及更新內容的麻煩。 相反地，您可以在一分鐘內更新特定專案頻道中的所有內容。

您也可以將此活動排程在較低網路流量的時間。

>[!NOTE]
>
>「大量離線更新」功能已最佳化，僅更新已修改的通道。

## 使用批量離線更新{#using-bulk-offline-update}

您可以從使用者介面(UI)手動使用大量離線更新，或從OSGi服務排程大量更新。

### 使用AEM Screens使用者介面{#using-aem-screens-user-interface}

請依照下列步驟，為AEM Screens專案使用大量離線更新：

1. 導覽至您的AEM Screens專案。
1. 選取專案，然後按一下動作列中的&#x200B;**更新離線內容**&#x200B;以手動更新頻道內容。

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Adobe Experience Manager Web控制台配置{#adobe-experience-manager-web-console-configuration}

請依照下列步驟，為AEM Screens專案使用大量離線更新：

1. Adobe Experience Manager Web主控台設定。
1. 搜索大量離線更新服務。

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. 新增下列屬性：

   **專** 案路徑指定AEM Screens專案的路徑。路徑通常為`/content/screens/<Name of your project>`。

   *例如*、  `/content/screens/we-retail`。您可以在URL中選取AEM Screens下的任何專案來找到此路徑（請勿按圖示）。

   >[!NOTE]
   >
   >指定與管道相對的專案路徑。

   **排** 程頻率指定時間，例如下午5:00或17:00，此服務應該更新離線內容。

1. 按一下「**儲存**」以儲存您的設定，而您的內容將會在指定的時間更新。


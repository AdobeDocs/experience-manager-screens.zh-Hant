---
title: 大量離線更新
seo-title: 大量離線更新
description: 請依本頁瞭解如何大量更新所有渠道。
seo-description: 請依本頁瞭解如何大量更新所有渠道。
uuid: 9b52c5e7-aa6d-4f55-b23c-8bd923723552
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 5d4ca652-d918-4b2b-b239-a2be9255ef0d
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 大量離線更新 {#bulk-offline-update}

本節介紹「大量離線更新」的下列主題：

* **綜覽**
* **使用大量離線更新**

>[!CAUTION]
>
>只有在您已安裝AEM 6.3 Feature Pack 3或AEM 6.4 Screens Feature Pack 1時，才能使用此AEM Screens功能。
>
>若要存取此功能套件，您必須聯絡Adobe支援並要求存取權。 一旦您擁有權限，就可從「套件共用」下載。

## 概覽 {#overview}

「大量離線更新」，可讓您大量更新所有頻道。 它可避免瀏覽至特定頻道並更新內容的麻煩。 相反地，您可以在單一瞬間更新特定專案的頻道中的所有內容。

您也可以將此活動排程在較低網路流量的時間。

>[!NOTE]
>
>「大量離線更新」功能已最佳化，僅更新已修改的頻道。

## 使用大量離線更新 {#using-bulk-offline-update}

您可以手動使用使用者介面(UI)的大量離線更新，或排程OSGi服務的大量更新。

### 使用AEM Screens使用者介面 {#using-aem-screens-user-interface}

請依照下列步驟，針對AEM Screens專案使用大量離線更新：

1. 導覽至您的AEM Screens專案。
1. 選取專案，然後從動 **作列按一下「更新離線內容** 」，以手動更新頻道內容。

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Adobe Experience Manager Web Console設定 {#adobe-experience-manager-web-console-configuration}

請依照下列步驟，針對AEM Screens專案使用大量離線更新：

1. Adobe Experience Manager Web Console設定。
1. 搜尋大量離線更新服務。

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. 新增下列屬性：

   **專案路徑** ：指定AEM Screens專案的路徑。 路徑通常是 `/content/screens/<Name of your project>`。

   *例如*, `/content/screens/we-retail`。 您可以在URL中，選取「AEM畫面」下的任何專案（請勿按一下圖示）來尋找此路徑。

   >[!NOTE]
   >
   >指定與您渠道相對的專案路徑。

   **排程頻率** ：指定此服務應更新離線內容的時間，例如下午5:00或17:00。

1. 按一 **下「儲存** 」以儲存您的設定，您的內容將會在指定的時間更新。

---
title: 大量離線更新
description: 瞭解如何大量更新所有管道。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d0a0b065-798e-4108-86ac-0a1f4e211cfc
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# 大量離線更新 {#bulk-offline-update}

本節涵蓋下列有關大量離線更新的主題：

* **概觀**
* **使用大量離線更新**

<!-- OBSOLETE VERSIONS
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, you must contact Adobe Support and request access. Once you have permissions you can download it from Package Share. -->

## 概觀 {#overview}

大量離線更新可讓您大量更新所有管道。 這可避免導覽至特定頻道和更新內容的麻煩。 反之，您可以一次更新一個特定專案之頻道中的所有內容。

您也可以將此活動排程在網路流量較低的時候。

>[!NOTE]
>
>「大量離線更新」功能已最佳化，僅更新已修改的管道。

## 使用大量離線更新 {#using-bulk-offline-update}

您可以從使用者介面(UI)手動使用大量離線更新，或從OSGi服務排程大量更新。

### 使用AEM Screens使用者介面 {#using-aem-screens-user-interface}

請依照下列步驟，對AEM Screens專案使用大量離線更新：

1. 導覽至您的AEM Screens專案。
1. 選取專案，然後選取 **更新離線內容** 以手動更新頻道內容。

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Adobe Experience Manager Web主控台設定 {#adobe-experience-manager-web-console-configuration}

請依照下列步驟，對AEM Screens專案使用大量離線更新：

1. Adobe Experience Manager Web主控台設定。
1. 搜尋大量離線更新服務。

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. 新增下列屬性：

   **專案路徑** 指定AEM Screens專案的路徑。 路徑通常為 `/content/screens/<Name of your project>`.

   *例如*， `/content/screens/we-retail`. 您可以選取AEM Screens底下的任何專案（不要按一下圖示），在URL中找到此路徑。

   >[!NOTE]
   >
   >指定相對於您管道的專案路徑。

   **排程頻率** 指定時間，例如，下午5:00或17:00，此服務應在此時間更新離線內容。

1. 選取 **儲存** 以儲存您的設定。 您的內容會在指定時間更新。

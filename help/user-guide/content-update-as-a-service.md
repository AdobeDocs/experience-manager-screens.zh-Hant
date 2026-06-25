---
title: 內容更新即服務
description: 瞭解內容更新即服務。
contentOwner: Jyotika syal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: de9f669b-9ce7-4d70-99b4-0b69ef3c1af5
TQID: https://experienceleague.adobe.com/p-13F7oySwiZfXHItW8zTIJRWiab5dOKxx-iU99vE9w
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 340
ht-degree: 0%

---

# 內容更新即服務 {#content-update-as-a-service}

>[!IMPORTANT]
>此內容對AEM內部部署/AMS （AEM 6.5LTS和AEM 6.5）有效。 如需AEM as a Cloud Service Screens內容，請參閱[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

本節涵蓋下列有關更新content-as-a-service的主題：

* **概觀**
* **使用大量離線更新**

<!--
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permission you can download it from Package Share. 
-->

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
1. 按一下專案，然後從動作列按一下&#x200B;**更新離線內容**，以手動更新頻道內容。

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Adobe Experience Manager Web主控台設定 {#adobe-experience-manager-web-console-configuration}

請依照下列步驟，對AEM Screens專案使用大量離線更新：

1. Adobe Experience Manager Web主控台設定。
1. 搜尋大量離線更新服務。

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. 新增下列屬性：

   **專案路徑** — 指定AEM Screens專案的路徑。 路徑通常是`/content/screens/<Name of your project>`。

   *例如*，`/content/screens/we-retail`。 您可以選取AEM Screens底下的任何專案（不要按一下圖示），在URL中找到此路徑。

   >[!NOTE]
   >
   >指定相對於您管道的專案路徑。

   **排程頻率** — 指定此服務應更新離線內容的時間，例如，下午5:00或17:00。

1. 按一下「儲存&#x200B;**&#x200B;**」，以便儲存您的設定。 您的所有內容都會在指定的時間更新。

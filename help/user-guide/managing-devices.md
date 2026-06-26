---
title: 管理裝置
description: 瞭解AEM Screens中的裝置指派和管理。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
TQID: https://experienceleague.adobe.com/BtVUYTZ9GisSxK6-M-QsYRGdykFB51IchqI7CX-vsa8
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 288
ht-degree: 5%

---

# 管理裝置 {#managing-devices}

>[!IMPORTANT]
>此內容對AEM內部部署/AMS （AEM 6.5LTS和AEM 6.5）有效。 如需AEM as a Cloud Service Screens內容，請參閱[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

此頁面說明裝置指定任務。

裝置主控台可讓您存取裝置管理員，將裝置指派給顯示器。

>[!CAUTION]
>
>指派裝置之前，請先註冊該裝置。 請參閱[裝置註冊](device-registration.md)。

## 裝置指派 {#device-assignment}

請依照下列步驟，將裝置指定給顯示器：

1. 導覽至專案的「裝置」資料夾，例如

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. 按一下您的&#x200B;**裝置**&#x200B;資料夾，然後按一下動作列中的&#x200B;**裝置管理員**。 已指派和未指派的裝置隨即顯示。

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. 從清單中按一下未指派的裝置，然後在動作列中按一下&#x200B;**指派裝置**。

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. 從清單中按一下您要指派裝置的顯示畫面，然後按一下&#x200B;**指派**。

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. 按一下&#x200B;**完成**&#x200B;以完成指派程式。


   顯示儀表板會在&#x200B;**裝置**&#x200B;面板中顯示指派的裝置。

   ![chlimage_1-37](assets/chlimage_1-37.png)

   按一下(**...**) 在&#x200B;**裝置**&#x200B;面板的右上角，新增裝置設定或更新裝置。

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>每次將第一個裝置新增到新的Screens專案時，都會建立使用者群組。例如，如果專案節點名稱為&#x200B;*we-retail*，則使用者群組名稱為&#x200B;*screens-we-retail-devices*。此群組已新增為&#x200B;**參與者**&#x200B;群組的成員，如下圖所示：

![chlimage_1-39](assets/chlimage_1-39.png)

### 後續步驟 {#the-next-steps}

在您熟悉指派通道給顯示區之後，請參閱t[監視與疑難排解](monitoring-screens.md)。


---
title: 套用轉變
description: 瞭解如何將轉換套用至您的AEM Screens專案。
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
TQID: https://experienceleague.adobe.com/t4JTCyQhe7kb5v-dveK4Np9dAAGLBeatCN2kyTM6ELc
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: e8696a6a-4caa-4059-b0b2-3fbb66f5ab7e
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 322
ht-degree: 0%

---

# 套用轉變 {#applying-transitions}

>[!IMPORTANT]
>此內容對AEM內部部署/AMS （AEM 6.5LTS和AEM 6.5）有效。 如需AEM as a Cloud Service Screens內容，請參閱[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

本節說明如何在不同的資產（影像和視訊）與管道中的內嵌序列之間套用&#x200B;**轉變**&#x200B;元件。

>[!CAUTION]
>
>若要深入瞭解&#x200B;**轉變**&#x200B;元件的屬性，請參閱[轉變](adding-components-to-a-channel.md#transition)。

## 在頻道中新增轉變元件至Assets {#adding-transition}

請依照下列步驟，將轉變元件新增至AEM Screens專案：

>[!NOTE]
>
>**先決條件**
>
>使用管道&#x200B;**TestTransition**&#x200B;建立AEM Screens專案&#x200B;**TestProject**。 此外，設定位置和顯示以檢視輸出。

1. 導覽至頻道&#x200B;**TestTransition**，然後按一下動作列中的&#x200B;**編輯**。

   ![影像1](assets/transitions1.png)

   >[!NOTE]
   >
   >**TestTransition**&#x200B;頻道中已有一些資產（影像和影片）。 例如，**TestTransition**&#x200B;頻道包含三個影像和兩個影片，如下所示：

   ![image2](assets/transitions2.png)


1. 將&#x200B;**轉變**&#x200B;元件拖放到您的編輯器中。

   >[!CAUTION]
   >
   >將轉變新增至頻道中的資產之前，請務必不要在循序頻道中的第一個資產之前新增轉變。 管道中的第一個專案必須是資產，而非轉變。

   ![影像3](assets/transitions3.png)

   >[!NOTE]
   >
   >根據預設，轉換元件（例如&#x200B;**Type**）的屬性設定為&#x200B;**淡化**，而&#x200B;**持續時間**&#x200B;設定為&#x200B;*1600毫秒*。 此外，不建議將轉換持續時間設定為超過套用到的資產。

1. 此外，如果您將&#x200B;**內嵌順序**&#x200B;元件（包含順序頻道）新增至此頻道編輯器，則可以在結尾新增轉變元件。 這麼做可確保內容以正確順序播放，如下圖所示：

   ![影像3](assets/transitions5.png)

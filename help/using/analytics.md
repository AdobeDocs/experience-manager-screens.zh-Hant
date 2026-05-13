---
title: Analytics與AEM Screens
description: 瞭解使用Adobe Experience Manager Screens的Adobe Analytics。
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
TQID: https://experienceleague.adobe.com/i7B7E5Kyno2U-ZTxEOPfhrr9W7fqYTWTV5vvcteRicY
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: eb30f47f-d87a-400f-8f78-63ce7979ff56
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 288
ht-degree: 0%

---

# Analytics與AEM Screens {#analytics-screens}

>[!NOTE]
>
>此活動的一般利害關係人為行銷/業務策略師。

AEM Screens可以在本機擷取每個播放器裝置執行的每個可追蹤事件。 此資料會儲存在本機，直到可以上傳至雲端進行處理為止。 除了所有事件資料外，也會新增deviceID和timestamp。 此功能可確保將一個播放器的資料與其他播放器區分開來。 此外，一天中不同時間執行的資料可視需要個別評估。

您擷取此資料有兩個基本原因。

第一個涉及&#x200B;**回饋回圈和機器學習**，第二個涉及建立供人類使用的圖表、儀表板和報告&#x200B;**。**

在回饋回圈使用案例中，您不需要關注視覺化報表或控制面板，而是想要定義AEM可針對內容修改執行的規則。 透過使用和處理特定時段的所有Screens播放器事件資料，您可以定義評估image1與image2效能的規則。 結合銷售資料與播放資料，AEM可判斷image1對銷售的影響較大，並自動指示所有播放器使用image1。

使用分析的第二個使用案例是透過報表和儀表板處理播放事件和使用資料，以供人類消耗。
您可以使用此資料建立互動式體驗的熱度圖，以透過應用程式決定偏好的歷程圖。 您也可以選擇建立控制面板，以圖形化方式解譯消費者與應用程式互動的次數。

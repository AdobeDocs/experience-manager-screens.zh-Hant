---
title: Analytics與AEM Screens
description: 瞭解使用Adobe Experience Manager Screens的Adobe Analytics。
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Analytics與AEM Screens {#analytics-screens}

>[!NOTE]
>
>此活動的一般利害關係人為行銷/業務策略師。

AEM Screens可以在本機擷取每個播放器裝置執行的每個可追蹤事件。 此資料會儲存在本機，直到可以上傳至雲端進行處理為止。 除了所有事件資料外，也會新增deviceID和timestamp。 此功能可確保將一個播放器的資料與其他播放器區分開來。 此外，一天中不同時間執行的資料可視需要個別評估。

您擷取此資料有兩個基本原因。

第一個涉及&#x200B;**回饋回圈和機器學習**，第二個涉及建立供人類使用的圖表、儀表板和報告&#x200B;**。**

在回饋回圈使用案例中，您不需要關注視覺化報表或控制面板，而是想要定義AEM可針對內容修改執行的規則。 透過使用和處理特定時段的所有Screens播放器事件資料，您可以定義評估image1與image2效能的規則。 透過結合銷售資料與播放資料，AEM可以判斷image1對銷售的影響更大，並自動指示所有播放器使用image1。

使用分析的第二個使用案例是透過報表和儀表板處理播放事件和使用資料，以供人類消耗。
您可以使用此資料建立互動式體驗的熱度圖，以透過應用程式決定偏好的歷程圖。 您也可以選擇建立控制面板，以圖形化方式解譯消費者與應用程式互動的次數。

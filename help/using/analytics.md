---
title: Analytics搭配AEM Screens
seo-title: Analytics搭配AEM Screens
description: 本頁說明Analytics與AEM Screens
seo-description: 本頁面說明使用AEM Screens的分析
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# 具有AEM Screens的Analytics {#analytics-screens}

>[!NOTE]
>
>此活動的一般利害關係人為行銷/業務策略師。

AEM Screens提供在本機擷取每個播放器裝置執行之每個可追蹤事件的功能。 此資料會儲存在本機，直到可上傳至雲端進行處理為止。 除了所有事件資料外，也新增deviceID和時間戳記。 這可確保來自一個播放器的資料可與另一個播放器區分，並且可視需要個別評估一天中不同時間執行的資料。

我們可能想要擷取此資料有兩個基本原因。

第一個包括&#x200B;**反饋循環和機器學習**，第二個包括建立用於人類消費的圖形、控制面板和報告&#x200B;**。**

在回饋循環使用案例中，我們不關心視覺報表或控制面板，而是想要定義AEM可針對內容修改執行的規則。 透過使用和處理特定時段的所有Screens播放器事件資料，我們可以定義一個規則，以評估image1與image2的有效性。 透過結合銷售資料與播放資料，AEM可判斷image1對銷售的影響大得多，並自動指示所有播放器使用image1。

使用analytics的第二個使用案例是透過報表和控制面板處理播放事件和使用資料以供人類使用。
我們可能會使用這些資料建立互動式體驗的熱度圖，以決定透過應用程式的偏好歷程圖。 我們也可以選擇建立控制面板，以圖形化方式解釋消費者與我們的應用程式互動的次數。


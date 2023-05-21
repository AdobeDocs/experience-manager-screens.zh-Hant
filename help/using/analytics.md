---
title: AEM Screens分析
seo-title: Analytics with AEM Screens
description: 本頁介紹分析與AEM Screens
seo-description: The page describes the analytics with AEM Screens
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# AEM Screens分析 {#analytics-screens}

>[!NOTE]
>
>此活動的典型利益相關方是營銷/業務策略師。

AEM Screens提供了本地捕獲每個玩家設備執行的每個可跟蹤事件的能力。 此資料將本地儲存，直到可以上傳到雲進行處理。 除了所有事件資料外，還添加了deviceID和時間戳。 這確保來自一個播放器的資料能夠與另一個播放器區別開來，並且如果需要，可以在一天的不同時間執行的資料可以被單獨評估。

我們可能希望捕獲此資料有兩個基本原因。

第一個是 **反饋環和機器學習** 而第二個則涉及 **建立圖形、面板和報告** 是供人類消費的。

在反饋循環使用案例中，我們不關心可視報告或儀表板，而是要定義可針對內容修改執AEM行的規則。 通過使用和處理來自特定時間段的所有螢幕播放器事件資料，我們可以定義一個規則來評估image1與image2的有效性。 通過將銷售資料與回放數AEM據相結合，可以確定image1對銷售的影響大得多，並自動指示所有玩家使用image1。

使用分析的第二個使用案例是通過報告和儀表板處理回放事件和使用資料以供人類使用。
我們可以使用這些資料建立互動式體驗的熱度圖，以通過我們的應用程式確定首選的行程圖。 我們還可以選擇建立一個儀表板，該儀表板提供消費者與應用程式交互的次數的圖形解釋。

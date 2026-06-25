---
title: 資料觸發程式
description: 瞭解AEM Screens中的資料觸發程式。
exl-id: 23c4268e-48be-4c84-b5eb-c96152b166f7
TQID: https://experienceleague.adobe.com/oeJ7C6Rt8-Z9sFnEP1S1tn0VW4PuiKkXkeDYaz8Vd4s
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: eb3ad9f8-54a2-45f3-abb1-d3976415a718
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 307
ht-degree: 0%

---

# 動態Creative最佳化 {#dynamic-creative}

>[!IMPORTANT]
>此內容對AEM內部部署/AMS （AEM 6.5LTS和AEM 6.5）有效。 如需AEM as a Cloud Service Screens內容，請參閱[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

>[!NOTE]
>
>此活動的一般利害關係人是AEM實作人員。

**Dynamic Creative Optimization** （或DCO）可用來建立數位看板體驗，以反映任何指定位置在任何指定時間及任何指定使用者的獨特環境。

這種用法也稱為內容的使用者端平面化。

推理的目的是確保每個播放器裝置或端點都可使用資料集，根據各種不同因素決定要自動播放的最佳內容。

此功能消除了在內容製作時需人為持續干預的需求。 它還有助於降低網路操作的總擁有成本，並讓數位體驗更相關、更情境化且更有效率。

例如：

* 使用功能產品的目前庫存等級
* 外部溫度或天氣
* 當地媒體廣告行銷活動是否存在
* 網路流量，甚至包括客戶挑選產品進行檢查時的本地事件

所有這些範例及其他範例都可用來提供更高層級的情境和個人化。

擁有包含DCO的視覺化銷售策略，可大幅提升網路的收視率。

資料觸發器有兩種主要型別：

* **本機資料觸發器**：這些資料觸發器是裝置上的本機資料觸發器。 例如，如果您觸碰熒幕，會啟動感應器以觸發本機資料資產或通道切換。
* **遠端資料觸發程式**：這涉及資料觸發的通道切換或根據網站服務API傳回值的資產切換。

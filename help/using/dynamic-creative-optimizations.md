---
title: 資料觸發程式
description: 瞭解AEM Screens中的資料觸發程式。
exl-id: 23c4268e-48be-4c84-b5eb-c96152b166f7
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Dynamic Creative Optimizations {#dynamic-creative}

>[!NOTE]
>
>此活動的典型利害關係人是AEM實作人員。

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

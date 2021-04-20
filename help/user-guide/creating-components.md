---
title: 建立元件
seo-title: 建立元件
description: 元AEM件可用來封存、格式化和轉譯網頁上提供的內容。 請依照本頁來瞭解製作頻道和轉換元件。
seo-description: 元AEM件可用來封存、格式化和轉譯網頁上提供的內容。 請依照本頁來瞭解製作頻道和轉換元件。
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
feature: Developing Screens
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 2%

---


# 建立元件{#creating-components}

元AEM件可用來封存、格式化和轉譯網頁上提供的內容。

>[!NOTE]
>
>如需建立元件的詳細資訊，請參AEM閱開發元AEM件。

## 製作頻道{#authoring-channels}

頻道是內容傳送至一組顯示器的中心物件。 因此，內容作者通常會在編輯器中開啟頻道以新增或修改內容。 由於渠道是&#x200B;***cq:Page***，因此它將遵循相同的傳統UX模式來添加和更改渠道上的元件。

但是，由於頻道中的元件通常呈現全螢幕，因此在嘗試編輯單一元件或編寫新訂單時，製作體驗會受到影響。 因此，頻道將依賴選擇器來呈現不同的元件檢視。 製作環境將運用編輯選擇器來啟動自訂的頻道演算。

例如， `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

使用者在編輯時，不需要處理將選取器新增至URL的問題。 客戶端邏輯正在監聽層交換機事件，並且如果通道具有專用資源類型&#x200B;*screens/core/components/channel，則添加選擇器。*

## 轉換元件{#rendering-components}

若要啟用正確的編寫功能，元件必須提供下列兩個轉譯：

| **元件** | **轉譯** |
|---|---|
| *my-component/my-component.html* | 生產演算 |
| *my-component/edit.html* | 在較小的視圖中編輯渲染 |

內建元件運用下列用戶端程式庫類別：

| **元件** | **客戶庫** |
|---|---|
| *cq.screens.components.edit* | CSS和JS，必須在編寫時載入 |
| *cq.screens.components.production* | 在頻道執行時必須載入的CSS和JS |
| *cq.screens.components* | 共用CSS和JS |

>[!NOTE]
>
>若要開發自訂元件，請使用***[AEM Screens範例元件範本](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***。


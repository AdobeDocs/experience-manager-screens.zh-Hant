---
title: 建立元件
seo-title: 建立元件
description: AEM元件可用來保留、格式化及轉譯可在您的網頁上使用的內容。 請依照本頁面了解製作管道和轉譯元件。
seo-description: AEM元件可用來保留、格式化及轉譯可在您的網頁上使用的內容。 請依照本頁面了解製作管道和轉譯元件。
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
feature: 開發螢幕
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 2%

---


# 建立元件{#creating-components}

AEM元件可用來保留、格式化及轉譯可在您的網頁上使用的內容。

>[!NOTE]
>
>若要了解建立AEM元件的詳細資訊，請參閱開發AEM元件。

## 製作通道{#authoring-channels}

頻道是傳遞至一組顯示器的內容的中央物件。 因此，內容作者通常會在編輯器中開啟管道，以新增或修改內容。 由於管道是&#x200B;***cq:Page***，因此會遵循相同的傳統UX模式，在管道上新增和變更元件。

不過，由於管道中的元件通常呈現全螢幕，因此在嘗試編輯單一元件或撰寫新訂單時，製作體驗會受到影響。 因此，通道將仰賴選取器來轉譯元件的不同檢視。 製作環境會利用編輯選取器來啟動自訂通道呈現。

例如， `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

使用者在編輯時不必將選取器新增至URL。 如果通道具有專用資源類型&#x200B;*screens/core/components/channel，則客戶端邏輯正在偵聽層交換機事件並添加選擇器。*

## 呈現元件{#rendering-components}

若要啟用正確的編寫功能，元件必須提供下列兩個呈現：

| **元件** | **轉譯** |
|---|---|
| *my-component/my-component.html* | 生產轉譯 |
| *my-component/edit.html* | 以較小的視圖編輯呈現 |

內建元件利用下列用戶端程式庫類別：

| **元件** | **客戶庫** |
|---|---|
| *cq.screens.components.edit* | CSS和JS，必須在製作期間載入 |
| *cq.screens.components.production* | 頻道執行時必須載入的CSS和JS |
| *cq.screens.components* | 共用CSS和JS |

>[!NOTE]
>
>若要開發自訂元件，請使用***[AEM Screens範例元件範本](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***。


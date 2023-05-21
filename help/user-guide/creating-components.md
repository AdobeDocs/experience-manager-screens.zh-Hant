---
title: 建立元件
seo-title: Creating Components
description: 組AEM件用於保存、格式化和呈現網頁上提供的內容。 請按照此頁瞭解創作渠道和渲染元件。
seo-description: AEM components are used to hold, format, and render the content made available on your webpages. Follow this page to learn about authoring channels and rendering components.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 3%

---

# 建立元件 {#creating-components}

組AEM件用於保存、格式化和呈現網頁上提供的內容。

>[!NOTE]
>
>要瞭解建立元件的詳細信AEM息，請參閱開AEM發元件。

## 創作渠道 {#authoring-channels}

該頻道是傳遞到一組顯示器的內容的中心對象。 因此，內容作者通常會在編輯器中開啟一個頻道來添加或修改內容。 因為頻道是 ***cq：頁*** 它將遵循相同的傳統UX模式在通道上添加和更改元件。

但是，由於通道中的元件通常呈現全屏，因此在嘗試編輯單個元件或編寫新訂單時，創作體驗會受到影響。 因此，通道將依靠選擇器來呈現元件的不同視圖。 創作環境將利用編輯選擇器來激活自定義通道呈現。

例如 `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

用戶在編輯時不必將選擇器添加到URL。 客戶端邏輯正在偵聽層交換機事件，並且如果通道具有專用資源類型，則添加選擇器 *螢幕/核心/元件/通道。*

## 渲染元件 {#rendering-components}

要啟用正確的創作，元件需要提供以下兩種渲染：

| **Component** | **轉譯** |
|---|---|
| *my-component/my-component.html* | 生產渲染 |
| *my-component/edit.html* | 在較小視圖中編輯渲染 |

內置元件利用以下客戶端庫類別：

| **Component** | **客戶庫** |
|---|---|
| *cq.screens.components.edit* | CSS和JS，在創作過程中必須載入 |
| *cq.screens.components.production* | 在通道運行時必須載入的CSS和JS |
| *cq.screens.components* | 共用CSS和JS |

>[!NOTE]
>
>要開發自定義元件，請使用***[AEM Screens樣本元件模板](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***。

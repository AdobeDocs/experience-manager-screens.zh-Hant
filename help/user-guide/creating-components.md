---
title: 建立元件
seo-title: Creating Components
description: AEM元件可用來保留、格式化及轉譯可在您的網頁上使用的內容。 請依照本頁所述操作，瞭解製作管道和演算元件的相關資訊。
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

AEM元件可用來保留、格式化及轉譯可在您的網頁上使用的內容。

>[!NOTE]
>
>若要瞭解建立AEM元件的詳細資訊，請參閱開發AEM元件。

## 製作管道 {#authoring-channels}

色版是傳送至一組顯示器的內容中心物件。 因此，內容作者通常會在編輯器中開啟管道，以新增或修改內容。 由於頻道是 ***cq：Page*** 它會遵循相同的傳統UX模式，在通道上新增和變更元件。

不過，由於管道中的元件通常會在全熒幕上呈現，因此在嘗試編輯單一元件或撰寫新訂單時，編寫體驗會受到影響。 因此，管道將依賴選取器來呈現元件的不同檢視。 製作環境將利用編輯選擇器來啟動自訂管道呈現。

例如 `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

編輯時，使用者不必將選擇器新增至URL。 使用者端邏輯正在接聽層切換事件，並在通道具有專用資源型別時新增選擇器 *screens/core/components/channel.*

## 演算元件 {#rendering-components}

若要啟用正確編寫，元件需要提供下列兩種轉譯：

| **Component** | **轉譯** |
|---|---|
| *my-component/my-component.html* | 生產呈現 |
| *my-component/edit.html* | 在較小的檢視中編輯演算 |

內建元件會運用下列使用者端程式庫類別：

| **Component** | **客戶庫** |
|---|---|
| *cq.screens.components.edit* | 編寫期間必須載入的CSS和JS |
| *cq.screens.components.production* | 通道執行時須載入的CSS和JS |
| *cq.screens.components* | 共用的CSS和JS |

>[!NOTE]
>
>若要開發自訂元件，請使用***[AEM Screens範例元件範本](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***。

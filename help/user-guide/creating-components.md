---
title: 建立元件
description: 瞭解如何使用AEM元件來保留、格式化及轉譯可在您的網頁上使用的內容。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 3%

---

# 建立元件 {#creating-components}

AEM元件可用來保留、格式化及轉譯可在網頁上使用的內容。

>[!NOTE]
>
>若要瞭解建立AEM元件的詳細資訊，請參閱開發AEM元件。

## 製作管道 {#authoring-channels}

色版是內容傳送至一組顯示器的中心物件。 因此，內容作者通常會在編輯器中開啟管道，以新增或修改內容。 由於通道是&#x200B;***`cq:Page`***，因此遵循相同的傳統UX模式在通道上新增和變更元件。

不過，由於管道內的元件通常會以全熒幕呈現，因此在嘗試編輯單一元件或撰寫新訂單時，編寫體驗會受影響。 因此，管道需仰賴選取器來呈現元件的不同檢視。 製作環境會使用編輯選擇器來啟動自訂色版轉譯。

例如 `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

使用者在編輯時不必將選擇器新增到URL。 使用者端邏輯正在接聽層切換事件，如果通道具有專用資源型別&#x200B;*screens/core/components/channel*，則新增選取器。

## 演算元件 {#rendering-components}

若要啟用正確編寫，元件必須提供下列兩種轉譯：

| **Component** | **轉譯** |
|---|---|
| *my-component/my-component.html* | 生產演算 |
| *my-component/edit.html* | 在較小的檢視中編輯演算 |

內建元件使用下列使用者端程式庫類別：

| **Component** | **使用者端資料庫** |
|---|---|
| *cq.screens.components.edit* | 在編寫期間必須載入的CSS和JS |
| *cq.screens.components.production* | 通道執行時須載入的CSS和JS |
| *cq.screens.components* | 共用的CSS和JS |

>[!NOTE]
>
>若要開發自訂元件，請使用&#x200B;***[AEM Screens範例元件範本](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***。

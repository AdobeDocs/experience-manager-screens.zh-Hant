---
title: 應用過渡
seo-title: Applying Transitions
description: 按照此頁瞭解如何將過渡應用到螢幕項目。
seo-description: Follow this page to learn how to apply transitions to your Screens projects.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 1%

---

# 應用過渡 {#applying-transitions}

本節介紹如何應用 **過渡** 在不同資源（影像和視頻）和通道中嵌入的序列之間的元件。


>[!CAUTION]
>
>詳細瞭解 **過渡** 元件，請參閱 [過渡](adding-components-to-a-channel.md#transition)。

## 將轉換元件添加到渠道中的資產 {#adding-transition}

按照以下步驟將過渡元件添加到您的AEM Screens項目：

>[!NOTE]
>
>**必備條件**
>
>建立AEM Screens項目 **測試項目** 有頻道 **測試轉換**。 此外，設定一個位置和一個顯示器以查看輸出。

1. 導航到通道 **測試轉換** 按一下 **編輯** 按鈕。

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >的 **測試轉換** 渠道中已經沒有多少資產（影像和視頻）。 例如， **測試轉換** channel包括三張影像和兩個視頻，如下所示：

   ![image2](assets/transitions2.png)


1. 拖放 **過渡** 元件。
   >[!CAUTION]
   >
   >在將過渡添加到渠道中的資產之前，請確保不要在順序渠道中的第一個資產之前添加過渡。 渠道中的第一項必須是資產，而不是過渡。

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >預設情況下，轉換元件的屬性，如 **類型** 設定為 **淡** 和 **持續時間** 設定為 *1600毫秒*。  此外，建議不要設定比要應用的資產長的過渡持續時間。

1. 另外，如果您 **嵌入序列** 元件（包括序列通道）到此通道編輯器中，可以在末尾添加過渡元件，以便按順序播放內容，如下圖所示：

   ![image3](assets/transitions5.png)

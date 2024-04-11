---
title: 套用轉變
description: 瞭解如何將轉換套用至您的AEM Screens專案。
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: 97084aee861e152abcc5f117a2a4759dced038cc
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# 套用轉變 {#applying-transitions}

本節說明如何套用 **轉變** 不同資產（影像和影片）之間的元件，以及管道中的內嵌順序。

>[!CAUTION]
>
>詳細瞭解「 」的屬性 **轉變** 元件，請參閱 [轉變](adding-components-to-a-channel.md#transition).

## 在管道中新增轉變元件至資產 {#adding-transition}

請依照下列步驟，將轉變元件新增至AEM Screens專案：

>[!NOTE]
>
>**必備條件**
>
>建立AEM Screens專案 **測試專案** 使用管道 **TestTransition**. 此外，設定位置和顯示以檢視輸出。

1. 導覽至頻道 **TestTransition** 並按一下 **編輯** 從動作列移除。

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >此 **TestTransition** 頻道中已經有很少的資產（影像和影片）。 例如， **TestTransition** 頻道包含三個影像和兩個影片，如下所示：

   ![image2](assets/transitions2.png)


1. 拖放 **轉變** 元件至您的編輯器。

   >[!CAUTION]
   >
   >將轉變新增至管道中的資產之前，請務必不要在循序管道中的第一個資產之前新增轉變。 管道中的第一個專案必須是資產，而非轉變。

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >依預設，轉變元件的屬性，例如 **型別** 設為 **淡化** 和 **持續時間** 設為 *1600毫秒*. 此外，不建議將轉換持續時間設定為超過套用到的資產。

1. 此外，如果您新增 **內嵌順序** 元件（包括順序色版）至此色版編輯器，您可以在結尾新增轉變元件。 這可確保內容以正確順序播放，如下圖所示：

   ![image3](assets/transitions5.png)

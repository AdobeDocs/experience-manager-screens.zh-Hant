---
title: 套用轉場效果
seo-title: 套用轉場效果
description: 請依照本頁面進行，瞭解如何將轉場效果套用至您的畫面專案。
seo-description: 請依照本頁面進行，瞭解如何將轉場效果套用至您的畫面專案。
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 9b54b153676852742859b704ac9aedf908fceecf
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 1%

---


# 套用轉場{#applying-transitions}

本節說明如何在不同資產（影像和視訊）和頻道中的內嵌序列之間套用&#x200B;**Transition**&#x200B;元件。


>[!CAUTION]
>
>要詳細瞭解&#x200B;**Transition**&#x200B;元件的屬性，請參閱[Transitions](adding-components-to-a-channel.md#transition)。

## 在渠道{#adding-transition}中向資產添加過渡元件

請依照下列步驟，將轉場元件新增至您的AEM Screens專案：

>[!NOTE]
>
>**必備條件**
>
>建立AEM Screens專案&#x200B;**TestProject**，其頻道為&#x200B;**TestTransition**。 此外，請設定位置和顯示器以檢視輸出。

1. 導覽至Channel **TestTransition**，然後從動作列按一下「編輯」。****

   ![影像1](assets/transitions1.png)

   >[!NOTE]
   >
   >**TestTransition**&#x200B;頻道中已經沒有多少資產（影像和視訊）。 例如，**TestTransition**&#x200B;頻道包含三個影像和兩個視訊，如下所示：

   ![影像2](assets/transitions2.png)


1. 將&#x200B;**Transition**&#x200B;元件拖放至您的編輯器。
   >[!CAUTION]
   >
   >在您新增轉場至渠道中的資產之前，請務必不要在循序渠道中的第一個資產之前新增轉場。 渠道中的第一個項目必須是資產，而非轉場。

   ![影像3](assets/transitions3.png)

   >[!NOTE]
   >
   >預設情況下，諸如&#x200B;**Type**&#x200B;的過渡元件的屬性被設定為&#x200B;**淡化**，並且&#x200B;**持續時間**&#x200B;被設定為&#x200B;*1600 ms*。  此外，建議不要設定比套用資產長的轉場持續時間。

1. 此外，如果您將&#x200B;**內嵌序列**&#x200B;元件（包含序列頻道）新增至此頻道編輯器，您可在最後新增轉場元件，讓內容依順序播放，如下圖所示：

   ![影像3](assets/transitions5.png)


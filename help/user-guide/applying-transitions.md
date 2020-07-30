---
title: 套用轉場效果
seo-title: 套用轉場效果
description: 請依照本頁面進行，瞭解如何將轉場效果套用至您的畫面專案。
seo-description: 請依照本頁面進行，瞭解如何將轉場效果套用至您的畫面專案。
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 8492bdd071ae029a68ec4a4983c79ce326cac38b
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 1%

---


# 套用轉場效果 {#applying-transitions}

本節說明如何在不同資產( **影像和視訊)和頻道中內嵌的序列之間套用** Transition元件。


>[!CAUTION]
>
>要詳細瞭解過渡元件的屬 **性** ，請參閱 [Transitions](adding-components-to-a-channel.md#transition)。

## 新增轉場元件至渠道中的資產 {#adding-transition}

請依照下列步驟，將轉場元件新增至您的AEM Screens專案：

>[!NOTE]
>
>**必備條件**
>
> 建立AEM Screens專案 **TestProject**&#x200B;與頻道 **TestTransition**。 此外，請設定位置和顯示器以檢視輸出。

1. 導覽至Channel **TestTransition** ，然後從動作 **列按一下「編輯** 」。

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >TestTransition **頻道中** ，已經沒有多少資產（影像和視訊）。 例如， **TestTransition** 頻道包含三張影像和兩個視訊，如下所示：

   ![image2](assets/transitions2.png)


1. 將Transition元件拖 **放至** 您的編輯器。
   >[!CAUTION]
   >
   >在您新增轉場至渠道中的資產之前，請務必不要在循序渠道中的第一個資產之前新增轉場。 渠道中的第一個項目必須是資產，而非轉場。

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >預設情況下，過渡元件(如 **Type** )的屬性設定為 **Fade** , **Duration** （持續時間） *設定為* 1600 ms。  此外，建議不要設定比套用資產長的轉場持續時間。

1. 此外，如果您將內嵌序列元件（包含序列頻道）新增至此頻道編輯器，您可在最後新增轉場元件，讓內容依順序播放，如下圖所示： ****

   ![image3](assets/transitions5.png)


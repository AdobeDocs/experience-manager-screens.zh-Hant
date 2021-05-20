---
title: 套用轉變
seo-title: 套用轉變
description: 請依照本頁面操作，了解如何將轉變套用至您的Screens專案。
seo-description: 請依照本頁面操作，了解如何將轉變套用至您的Screens專案。
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
feature: 製作畫面
role: Administrator, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 1%

---

# 套用轉變{#applying-transitions}

本節說明如何在不同資產（影像和視訊）和管道中內嵌的序列之間套用&#x200B;**Transition**&#x200B;元件。


>[!CAUTION]
>
>要詳細了解&#x200B;**Transition**&#x200B;元件的屬性，請參閱[Transitions](adding-components-to-a-channel.md#transition)。

## 在通道{#adding-transition}中將轉變元件新增至資產

請依照下列步驟，將轉變元件新增至您的AEM Screens專案：

>[!NOTE]
>
>**必備條件**
>
>建立具有通道&#x200B;**TestTransition**&#x200B;的AEM Screens專案&#x200B;**TestProject**。 此外，還可設定一個位置和一個顯示器來查看輸出。

1. 導覽至通道&#x200B;**TestTransition**，然後從動作列按一下&#x200B;**Edit**。

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >**TestTransition**&#x200B;通道中已有少數資產（影像和視訊）。 例如， **TestTransition**&#x200B;頻道包含三個影像和兩個視訊，如下所示：

   ![image2](assets/transitions2.png)


1. 將&#x200B;**Transition**&#x200B;元件拖放至編輯器。
   >[!CAUTION]
   >
   >將轉變新增至管道中的資產之前，請務必不要在循序管道中的第一個資產之前新增轉變。 管道中的第一個項目必須是資產，而非轉變。

   ![影像3](assets/transitions3.png)

   >[!NOTE]
   >
   >預設情況下，轉換元件（如&#x200B;**Type**）的屬性設定為&#x200B;**Fade**，而&#x200B;**Duration**&#x200B;設定為&#x200B;*1600 ms*。  此外，建議您不要設定超過套用資產的轉變持續時間。

1. 此外，如果向此通道編輯器添加&#x200B;**嵌入序列**&#x200B;元件（包括序列通道），則可以在末尾添加過渡元件，以便按順序播放內容，如下圖所示：

   ![影像3](assets/transitions5.png)

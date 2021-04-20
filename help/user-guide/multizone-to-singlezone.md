---
title: MultiZone到SingleZone轉場使用案例
description: 請依照本頁瞭解MultiZone到SingleZone轉場使用案例。
seo-description: MultiZone to SingleZone轉變使用案例。
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, Business Practitioner
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---


# 多區域到單區域過渡{#multizone-to-singlezone-use-case}


## 使用案例說明{#use-case-description}

本節說明如何設定與單一區域配置頻道交替的多區域配置頻道的使用案例範例。 多區域渠道具有排序影像／視訊資產，它顯示如何設定從多區域切換至單一區域的專案，反之亦然。

### 先決條件{#preconditions}

開始此使用案例之前，請務必瞭解如何：

* **[建立和管理渠道](managing-channels.md)**
* **[建立和管理位置](managing-locations.md)**
* **[建立和管理計畫](managing-schedules.md)**
* **[裝置註冊](device-registration.md)**

### 主要操作者{#primary-actors}

內容作者

## 設定項目{#setting-up-the-project}

請依照下列步驟設定專案：

1. 建立名為&#x200B;**TakeoverLoop**&#x200B;的AEM Screens項目，如下所示。

   ![資產](assets/mz-to-sz1.png)


1. **建立多區域畫面頻道**

   1. 選擇&#x200B;**Channels**&#x200B;資料夾，然後從動作列按一下「建立&#x200B;**a3/>」以開啟精靈以建立頻道。**
   1. 從嚮導中選擇&#x200B;**左-L條分割螢幕通道**&#x200B;並建立名為&#x200B;**MultiZoneLayout**&#x200B;的通道。
   1. 新增內容至頻道。 將資產拖放至每個區域。 以下範例顯示&#x200B;**MultiZoneLayout**&#x200B;頻道，其中包含視訊、影像和文字橫幅（內嵌序列），如下所示。

   ![資產](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >若要進一步瞭解如何在頻道中建立多區域版面，請參閱[多區域版面](multi-zone-layout-aem-screens.md)。


1. 在&#x200B;**Channels**&#x200B;資料夾中建立另一個名為&#x200B;**TakeoverChannel**&#x200B;的頻道。

   ![資產](assets/mz-to-sz3.png)

1. 按一下動作列中的「編輯」，將內容新增至此頻道。 ****&#x200B;將&#x200B;**Channel**&#x200B;元件和要切換到的影像資產添加到此通道中，如下圖所示：

   ![資產](assets/mz-to-sz4.png)

1. 開啟Channel元件的設定，並指向您在&#x200B;*步驟2*&#x200B;中建立的&#x200B;**MultiZoneLayout**&#x200B;頻道。

   ![資產](assets/mz-to-sz5.png)

1. 將&#x200B;**序列**&#x200B;欄位的持續時間設定為&#x200B;**10000 ms**。

   ![資產](assets/mz-to-sz6.png)

1. 同樣地，請開啟影像（您新增的資產）的設定，並將其持續時間從&#x200B;**序列**&#x200B;欄位設定為&#x200B;**3000 ms**。

   ![資產](assets/mz-to-sz7.png)

## 勾選預覽{#checking-the-preview}

您可以檢視播放器所要的輸出，或只要按一下編輯器中的&#x200B;**預覽**&#x200B;即可。

輸出將示範多區域版面如何播放&#x200B;*10000 ms*，然後切換至播放持續時間為&#x200B;*3000 ms*&#x200B;的單一區域版面，然後切換回多區域版面。

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>您可以根據您的需求自訂通道轉換（從多區域到單區域版面配置，反之亦然）。
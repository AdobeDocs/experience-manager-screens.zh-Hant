---
title: MultiZone到SingleZone轉場使用案例
description: 請依照本頁瞭解MultiZone到SingleZone轉場使用案例。
seo-description: MultiZone to SingleZone轉變使用案例。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 6f770734941635a0cd404986c259022137355af3

---


# 多區域到單區域過渡 {#multizone-to-singlezone-use-case}


## 使用案例說明 {#use-case-description}

本節說明如何設定與單一區域配置頻道交替的多區域配置頻道的使用案例範例。 多區域渠道具有排序影像／視訊資產，它顯示如何設定從多區域切換至單一區域的專案，反之亦然。

### 先決條件 {#preconditions}

開始此使用案例之前，請務必瞭解如何：

* **[建立和管理渠道](managing-channels.md)**
* **[建立和管理位置](managing-locations.md)**
* **[建立和管理計畫](managing-schedules.md)**
* **[裝置註冊](device-registration.md)**

### 主要操作者 {#primary-actors}

內容作者

## 設定專案 {#setting-up-the-project}

請依照下列步驟設定專案：

1. 建立名為 **TakeoverLoop的AEM Screens專案**，如下所示。

   ![資產](assets/mz-to-sz1.png)


1. **建立多區域畫面頻道**

   1. 選取「 **Channels** 」檔案夾，然後按 **一下動作列中的「建立** 」，以開啟精靈以建立渠道。
   1. 從 **精靈中選取「左側列分割螢幕色版** 」，並建立名為「多區域 **配置」的色版**。
   1. 新增內容至頻道。 將資產拖放至每個區域。 下列範例顯示 **MultiZoneLayout** 頻道，包含視訊、影像和文字橫幅（內嵌序列），如下所示。
   ![資產](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >若要進一步瞭解如何在您的頻道中建立多區域版面，請參 [閱多區域版面](multi-zone-layout-aem-screens.md)。


1. 在您的Channels資料夾中建立另 **一個名為** TakeoverChannel **的渠道** 。

   ![資產](assets/mz-to-sz3.png)

1. 按一 **下動作列** 中的「編輯」，將內容新增至此頻道。 將 **Channel** 元件和您要切換至的影像資產新增至此頻道，如下圖所示：

   ![資產](assets/mz-to-sz4.png)

1. 開啟Channel元件的設定，並指向您在步驟2中建立 **的MultiZoneLayout***頻道*。

   ![資產](assets/mz-to-sz5.png)

1. 將「序列」( **Sequence** )欄位的持 **續時間設定為10000毫秒**。

   ![資產](assets/mz-to-sz6.png)

1. 同樣地，請開啟影像（您新增的資產）的設定，並將其持續時間從「序 **列** 」欄位設 **定為3000毫秒**。

   ![資產](assets/mz-to-sz7.png)

## 勾選預覽 {#checking-the-preview}

您可以檢視播放器所要的輸出，或只要按一下編輯器中的「 **預覽** 」即可。

輸出將示範多區域版面如何播放 *10000毫秒* ，然後切換至播放持續時間為 ** 3000毫秒的單一區域版面，然後切換回多區域版面。

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>您可以根據您的需求自訂通道轉換（從多區域到單區域版面配置，反之亦然）。
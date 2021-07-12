---
title: MultiZone到SingleZone過渡使用案例
description: 請參閱本頁，了解MultiZone到SingleZone轉變的使用案例。
seo-description: MultiZone到SingleZone過渡使用案例。
contentOwner: Jyotika Syal
feature: 製作畫面
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 2%

---

# 多區域到單區域過渡 {#multizone-to-singlezone-use-case}


## 使用案例說明 {#use-case-description}

本節將說明一個使用案例範例，重點說明如何設定與單一區域佈局通道交替的多區域佈局通道。 多區域管道具有排序的影像/視訊資產，它顯示如何設定從多區域到單區域交替的專案，反之亦然。

### 先決條件 {#preconditions}

開始此使用案例前，請務必了解如何：

* **[建立和管理管道](managing-channels.md)**
* **[建立和管理位置](managing-locations.md)**
* **[建立和管理排程](managing-schedules.md)**
* **[裝置註冊](device-registration.md)**

### 主要行為者 {#primary-actors}

內容作者

## 設定專案 {#setting-up-the-project}

請依照下列步驟來設定專案：

1. 建立名為&#x200B;**TakeoverLoop**&#x200B;的AEM Screens專案，如下所示。

   ![資產](assets/mz-to-sz1.png)


1. **建立多區域螢幕通道**

   1. 選擇&#x200B;**通道**&#x200B;資料夾，然後從操作欄按一下&#x200B;**建立**&#x200B;以開啟嚮導以建立通道。
   1. 從嚮導中選擇&#x200B;**L Left-L Bar Split Screen Channel**&#x200B;並建立標題為&#x200B;**MultiZoneLayout**&#x200B;的通道。
   1. 新增內容至頻道。 將資產拖放至每個區域。 以下示例顯示&#x200B;**MultiZoneLayout**&#x200B;通道，該通道由視頻、影像和文本橫幅（以嵌入序列）組成，如下所示。

   ![資產](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >要了解有關在通道中建立多區域佈局的詳細資訊，請參閱[多區域佈局](multi-zone-layout-aem-screens.md)。


1. 將另一個名為&#x200B;**TakeoverChannel**&#x200B;的渠道建立到&#x200B;**渠道**&#x200B;資料夾。

   ![資產](assets/mz-to-sz3.png)

1. 按一下動作列中的「**編輯**」 ，將內容新增至此頻道。 將&#x200B;**Channel**&#x200B;元件和要切換到此通道的影像資產添加到此通道，如下圖所示：

   ![資產](assets/mz-to-sz4.png)

1. 開啟通道元件的設定，並將其指向您在&#x200B;*步驟2*&#x200B;中建立的&#x200B;**MultiZoneLayout**&#x200B;通道。

   ![資產](assets/mz-to-sz5.png)

1. 將持續時間從&#x200B;**Sequence**&#x200B;欄位設定為&#x200B;**10000 ms**。

   ![資產](assets/mz-to-sz6.png)

1. 同樣地，請開啟影像（您新增的資產）的設定，並從&#x200B;**Sequence**&#x200B;欄位將其持續時間設為&#x200B;**3000 ms**。

   ![資產](assets/mz-to-sz7.png)

## 勾選預覽 {#checking-the-preview}

您可以從播放器檢視所需的輸出，或只需按一下編輯器中的&#x200B;**預覽**&#x200B;即可。

輸出將演示多區域佈局如何播放&#x200B;*10000 ms*，然後切換到播放持續時間為&#x200B;*3000 ms*&#x200B;的單個區域佈局，然後切換回多區域佈局。

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>您可以根據需求自訂通道轉變（從多區域配置到單區域配置，反之亦然）。

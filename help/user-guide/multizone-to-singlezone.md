---
title: MultiZone到SingleZone的轉換使用案例
description: 請依照本頁面的說明進行，以便您瞭解MultiZone to SingleZone Transitions使用案例。
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 1%

---

# 多區域到單一區域轉換 {#multizone-to-singlezone-use-case}

## 使用案例說明 {#use-case-description}

本節說明使用案例範例，著重說明如何設定與單一區域版面配置色版交替的多區域版面配置色版。 多區域管道有循序排列的影像/視訊資產，並顯示您如何設定可從多區域切換為單一區域，反之亦然。

### 先決條件 {#preconditions}

開始此使用案例前，請確定您瞭解如何：

* **[建立和管理頻道](managing-channels.md)**
* **[建立和管理位置](managing-locations.md)**
* **[建立和管理排程](managing-schedules.md)**
* **[裝置註冊](device-registration.md)**

### 主要執行者 {#primary-actors}

內容作者

## 設定專案 {#setting-up-the-project}

請依照下列步驟設定專案：

1. 建立名為&#x200B;**TakeoverLoop**&#x200B;的AEM Screens專案，如下所示。

   ![資產](assets/mz-to-sz1.png)


1. **建立多區域Screens頻道**

   1. 按一下「**管道**」資料夾，然後從動作列按一下「**建立**」並開啟精靈，以建立管道。
   1. 從精靈按一下&#x200B;**左側L列拆分畫面頻道**，並建立標題為&#x200B;**MultiZoneLayout**&#x200B;的頻道。
   1. 新增內容至頻道。 將資產拖放至每個區域。 下列範例顯示&#x200B;**MultiZoneLayout**&#x200B;色版，其中包含視訊、影像和文字橫幅（以內嵌順序顯示），如下所示。

   ![資產](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >若要進一步瞭解如何在您的頻道中建立多區域配置，請參閱[多區域配置](multi-zone-layout-aem-screens.md)。


1. 將標題為&#x200B;**TakeoverChannel**&#x200B;的另一個頻道建立到您的&#x200B;**Channel**&#x200B;資料夾。

   ![資產](assets/mz-to-sz3.png)

1. 按一下動作列中的&#x200B;**[編輯**]，即可新增內容至此頻道。 新增&#x200B;**色版**&#x200B;元件以及您要為此色版切換到的影像資產，如下圖所示：

   ![資產](assets/mz-to-sz4.png)

1. 開啟管道元件的設定，並將它指向您在&#x200B;*步驟2*&#x200B;中建立的&#x200B;**MultiZoneLayout**&#x200B;管道。

   ![資產](assets/mz-to-sz5.png)

1. 將期間從&#x200B;**序列**&#x200B;欄位設定為&#x200B;**10000毫秒**。

   ![資產](assets/mz-to-sz6.png)

1. 同樣地，請開啟影像（您新增的資產）的設定，並將其持續時間從&#x200B;**序列**&#x200B;欄位設定為&#x200B;**3000毫秒**。

   ![資產](assets/mz-to-sz7.png)

## 檢查預覽 {#checking-the-preview}

您可以從播放器檢視想要的輸出，或直接從編輯器選取&#x200B;**預覽**。

輸出示範多區域配置如何播放&#x200B;*10000毫秒*。 然後，它切換到播放持續時間為&#x200B;*3000毫秒*&#x200B;的單一區域配置。 最後，它會切換回多區域版面配置。

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>您可以根據需求自訂管道轉變（從多區域版面配置到單一區域版面配置或反之）。

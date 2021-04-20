---
title: 建立和管理即時副本
seo-title: 管理LiveCopy
description: 本頁說明如何建立和管理頻道的即時副本。
seo-description: 請依照本頁建立渠道的即時副本、檢視屬性、檢查狀態，並將變更從渠道傳播至其即時副本。
uuid: 78ec7219-95ab-44d1-9514-1b97aded5bf4
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 84085a03-1798-4f1d-858c-6014a3f6aff6
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---


# 建立和管理即時副本{#creating-and-managing-a-live-copy}

本頁說明如何建立和管理頻道的即時副本。

***即時副本***&#x200B;是與原始來源維持即時關係的特定網站內容的副本。 此即時關係可讓即時副本繼承來源的內容和頁面屬性。

本頁說明如何建立渠道的即時副本、檢視屬性、檢查狀態，以及將變更從渠道傳播至其即時副本。


## 建立即時副本{#creating-a-live-copy}

請依照下列步驟，在專案資料夾中建立渠道的即時副本。

1. 選擇Adobe Experience Manager連結（左上角），然後選擇&#x200B;**螢幕**。 或者，您也可以直接前往：`http://localhost:4502/screens.html/content/screens`。

1. 導覽至「畫面」專案，然後按一下「頻道」**。**
1. 按一下「建立&#x200B;****」並選取「即時副本&#x200B;**」以建立頻道的即時副本。**

1. 選擇目標並按一下&#x200B;**Next**。
1. 選擇即時副本的駐留位置。
1. 在&#x200B;**建立即時副本**&#x200B;頁面中輸入&#x200B;**Title**&#x200B;和&#x200B;**Name**。

1. 按一下&#x200B;**開啟**&#x200B;查看新即時副本的內容，或按一下&#x200B;**完成**&#x200B;返回首頁。

或者，請參閱下列步驟，以取得建立頻道新即時副本的視覺呈現。

以下示例說明為&#x200B;***空閒通道***&#x200B;建立即時副本(***IdleLiveCopy***)，目標資料夾為&#x200B;***通道***。

![chlimage_1-2](assets/chlimage_1-2.gif)

## 檢視即時副本頻道的內容{#viewing-content-of-the-live-copy-channel}

即時副本是已存在之渠道的副本。

若要檢視即時副本的內容，請參閱下列步驟：

1. 導覽至「畫面」專案，然後按一下您原始建立即時副本的位置，如上節所示。 （在這裡，此位置被選擇為&#x200B;**Channels**&#x200B;資料夾）

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. 按一下動作列中的「編輯」，檢視頻道中的內容。****

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >檢視即時副本頻道的內容時，您會以&#x200B;**即時副本狀態**&#x200B;的形式，在功能表中檢視額外項目。 如需詳細資訊，請參閱下方的章節。

### 查看即時副本的屬性{#viewing-properties-of-a-live-copy}

此外，您還可以檢視即時副本頻道的屬性。

1. 導覽至您的即時複製頻道，然後從動作列按一下「屬性&#x200B;****」。

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. 選擇&#x200B;**即時副本**&#x200B;標籤，以檢視頻道的詳細資訊。

   ![chlimage_1-21](assets/chlimage_1-21.png)

### 即時副本狀態 {#live-copy-status}

如下圖所示，模式&#x200B;**即時副本狀態**&#x200B;可讓您檢視渠道中所有資產的關係狀態。

1. 按一下「編輯&#x200B;****」以選擇「即時副本狀態」，並檢視頻道內容與原始頻道（即時副本從中產生）的關聯。****

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. 選擇&#x200B;**即時副本狀態**&#x200B;以顯示預覽頁面。

   所有含綠色邊框的資源都顯示內容繼承自原始頻道。

   ![chlimage_1-23](assets/chlimage_1-23.png)

### 中斷繼承{#breaking-the-inheritance}

您也可以取消對livecopy的繼承，使內容與原始分支獨立。

以下示例顯示您在編輯模式下選擇影像，然後按一下右上角的取消繼承符號。

![chlimage_1-24](assets/chlimage_1-24.png)

### 將更改傳播到即時複製通道{#propagating-changes-to-the-live-copy-channel}

如果您在原始通道中進行變更／更新，您也需要將這些變更傳播至即時副本通道。

請遵循下列步驟，確保您的變更從原始渠道傳播至即時複製渠道：

1. 選擇原始通道（***空閒通道***），然後從操作欄中按一下&#x200B;**編輯**。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 編輯此頻道內容。 例如，從此頻道刪除影像。

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. 選擇頻道的即時副本(***IdleLiveCopy***)，然後從動作列按一下「編輯」。 ****&#x200B;您會注意到，您刪除的影像仍會顯示在即時副本中。

   為了傳播這些更改，您需要同步該通道。

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. 若要將變更傳播至即時複製頻道，請導覽至控AEM制面板並選取即時複製頻道，然後從動作列按一下「屬性&#x200B;****」。

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. 選擇「即時副本」(Live Copy)頁籤，然後從操作欄中按一下「同步」(Synchronize)。********

   ![chlimage_1-21](assets/chlimage_1-29.png)

1. 按一下&#x200B;**Sync**&#x200B;確認更改。 按一下「儲存並關閉」，以返回控制面AEM板。****

   ![chlimage_1-30](assets/chlimage_1-30.png)

   您會注意到，影像現在也會從即時副本頻道中刪除。


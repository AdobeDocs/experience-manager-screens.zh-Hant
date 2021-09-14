---
title: Feature Pack 202109發行說明
description: 「如需2021年9月22日發行的AEM Screens Feature Pack 202105的相關資訊，請詳閱本頁。」
feature: Feature Pack
role: Developer
level: Intermediate
index: false
source-git-commit: e96c314ea7487932d2ab994ffc41ca8d2af61c5c
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 5%

---

# Feature Pack 202109發行說明 {#release-notes-for-feature-pack}

>[!CAUTION]
>建議您升級至最新版Adobe Experience Manager(AEM)。 Screens對AEM 6.3 Screens平台提供維護支援。

## 可用性 {#availability}

AEM Screens發行AEM 6.5 Feature Pack 9。

您可以使用Adobe ID，從[軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載AEM Screens 6.5.9版的最新Feature Pack。 導覽至「**Adobe Experience Manager**」標籤並搜尋「**Screens**」，以取得最新的Feature Pack，標題為「**AEM 6.5 Screens FP9**」。

## 發行日期 {#release-date}

AEM Screens Feature Pack 202109的發行日期為2021年9月9日。

### 新增功能 {#what-is-new}

* **在AEM Screens通道中鎖定頁面**

   AEM Screens現在支援&#x200B;*鎖定頁面*，如AEM Sites中已實作。 Adobe Experience Manager(AEM)可讓您鎖定頁面，讓其他人都無法修改內容。 當您對特定頁面進行許多編輯，或需要將頁面凍結一段時間時，這個功能會很實用。

* **命名AEM Screens播放器裝置**

   AEM Screens播放器現在包含傳送裝置名稱至Adobe Experience Manager(AEM)的功能。
預設情況下，當使用批量註冊註冊設備時，系統生成的用戶名將輸入到標題欄位中。 或者，客戶可能會使用資產標籤或其他好記的名稱，以便顯示在AEM中，並更輕鬆指派適當的內容。

   請參閱下列檔案，了解如何在每個支援的作業系統中設定名稱：

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [蒂森](/help/user-guide/tizen-player.md#name-tizen)
   * [Chrome OS](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **資訊清單產生**

   通過改進的效能（如在伺服器上分配較少的資源）加快通道清單的生成。

### 錯誤修正 {#bug-fixes}

* 播放器切換至包含動態內嵌序列的頻道時，會顯示黑屏。
* Screens播放器現在會封鎖切換至任何中斷的通道，進一步避免404錯誤或出現錯誤訊息的頁面。

### 發行的AEM Screens播放器 {#released-aem-screens-players}

已針對AEM 6.5 Feature Pack 8發行下列AEM Screens播放器：

* ChromeOS
* Windows
* 蒂森
* Android
* Linux

#### AEM Screens播放器下載  {#aem-screens-player-downloads}

若要下載最新的AEM Screens播放器並進一步了解錯誤修正，請參閱&#x200B;**[AEM Screens播放器下載](https://download.macromedia.com/screens/index.html)**。

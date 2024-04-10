---
title: Feature Pack 202105發行說明
description: 瞭解關於2021年6月4日發行的AEM Screens Feature Pack 202105。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 3%

---

# Feature Pack 202105發行說明 {#release-notes-for-feature-pack}

>[!CAUTION]
>建議您升級至最新版Adobe Experience Manager (AEM)。 AEM Screens提供AEM 6.3 Screens平台的維護支援。

## 可用性 {#availability}

AEM Screens已發行AEM 6.5 Feature Pack 8。

若要下載AEM Screens 6.5.8版的最新Feature Pack，請前往 [軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 使用您的Adobe ID。 瀏覽至 **Adobe Experience Manager** 標籤並搜尋 **Screens** 以取得標題為 **AEM 6.5 Screens FP8**.

>[!IMPORTANT]
>安裝AEM 6.5 Feature Pack 8的最低版本，以便在您安裝套件後讓AMS聯結器運作 `screens-cloud-ams-pkg-0.0.20`， `screens-cloud-ams-pkg-0.0.16`，以及 `screens core bundles`.

## 發行日期 {#release-date}

AEM Screens Feature Pack 202105的發行日期為2021年6月4日。

### 新增功能 {#what-is-new}

* **在AEM Screens頻道中鎖定頁面**

  AEM Screens現在支援 *鎖定頁面*，實作於AEM Sites。 Adobe Experience Manager (AEM)可讓您鎖定頁面，不讓其他人修改內容。 當您對某個特定頁面進行大量編輯，或必須凍結頁面一段時間時，此功能會很有用。

* **命名AEM Screens播放器裝置**

  AEM Screens播放器現在包含將裝置名稱傳送至Adobe Experience Manager (AEM)的功能。
根據預設，當使用大量註冊來註冊裝置時，系統產生的使用者名稱會輸入在標題欄位中。 另外，客戶可能會使用資產標籤或其他易記名稱，以便在AEM中可見，且更易於指派適當內容。

  請參閱下列檔案，瞭解如何在每個支援的作業系統中設定名稱：

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [Chrome作業系統](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **資訊清單產生**

  透過改善的效能（例如在伺服器上配置較少的資源）更快速地產生通道資訊清單。

### 錯誤修正 {#bug-fixes}

* 播放器切換到包含動態內嵌順序的頻道時顯示黑色熒幕。
* Screens播放器現在會封鎖切換至任何中斷頻道的功能，進而避免404錯誤或頁面出現錯誤訊息。

### 已發行的AEM Screens Players

下列AEM Screens Player已針對AEM 6.5 Feature Pack 8發行：

* Chrome OS
* Windows
* Tizen
* Android™
* Linux®

#### AEM Screens播放器下載

若要下載最新的AEM Screens播放器並深入瞭解錯誤修正，請參閱 **[AEM Screens播放器下載](https://download.macromedia.com/screens/index.html)**.

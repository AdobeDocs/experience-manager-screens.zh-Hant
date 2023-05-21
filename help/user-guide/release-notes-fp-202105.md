---
title: 功能包202105發行說明
description: 「按照本頁獲取2021年6月4日發佈的AEM Screens功能包202105的資訊。」
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 02bc399d61f5666918caad9fce3d69d63f0782d7
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 4%

---

# 功能包202105發行說明 {#release-notes-for-feature-pack}

>[!CAUTION]
>建議您升級到最新版本的Adobe Experience Manager(AEM)。 螢幕為6.3螢幕AEM平台提供維護支援。

## 可用性 {#availability}

AEM Screens發AEM布了6.5功能包8。

您可以從以下網站下載AEM Screens6.5.8版的最新功能包： [軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 用你的Adobe ID。 導航到 **Adobe Experience Manager** 頁籤和搜索 **螢幕** 獲取最新功能包的標題為 **FP8AEM 6.5螢幕**。

>[!IMPORTANT]
>安裝軟體包後，必AEM須安裝6.5 Feature Pack 8 for AMS連接器的最低版本才能工作 `screens-cloud-ams-pkg-0.0.20`。 `screens-cloud-ams-pkg-0.0.16` 和 `screens core bundles`。

## 發行日期 {#release-date}

AEM Screens功能包202105的發佈日期為2021年6月4日。

### 新增功能 {#what-is-new}

* **鎖定AEM Screens頻道中的頁面**

   AEM Screens *鎖定頁面*&#x200B;如已在AEM Sites實施。 Adobe Experience Manager(AEM)允許您鎖定頁面，以便其他人不能修改內容。 當您對一個特定頁面進行大量編輯或需要將頁面凍結一段時間時，此功能非常有用。

* **命名AEM Screens播放器設備**

   AEM Screens的玩家現在包括向Adobe Experience Manager(AEM)發送設備名稱的能力。
預設情況下，當使用批量註冊註冊設備時，系統生成的用戶名將輸入到標題欄位中。 作為替代方法，客戶可以使用資產標籤或其他友好名稱，以便在中可AEM見並更容易分配適當內容。

   請參閱以下文檔，瞭解如何在每個受支援的作業系統中配置名稱：

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [蒂森](/help/user-guide/tizen-player.md#name-tizen)
   * [Chrome作業系統](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **清單生成**

   通過改進的效能（例如在伺服器上分配更少的資源）加快通道清單生成。

### 錯誤修正 {#bug-fixes}

* 播放器在切換到包含動態嵌入序列的頻道時顯示黑屏。
* 螢幕播放器現在阻止切換到任何中斷的頻道，這進一步避免了404錯誤或出現錯誤消息的頁面。

### 已釋放AEM Screens球員 {#released-aem-screens-players}

以下AEM Screens玩家AEM將發佈6.5功能包8:

* ChromeOS
* Windows
* 蒂森
* Android
* Linux

#### AEM Screens播放器下載  {#aem-screens-player-downloads}

要下載最新的AEM Screens播放器並瞭解有關錯誤修復的詳細資訊，請參閱 **[AEM Screens播放器下載](https://download.macromedia.com/screens/index.html)**。

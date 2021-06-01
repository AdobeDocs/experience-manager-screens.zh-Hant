---
title: Feature Pack 202103發行說明
description: 「如需2021年3月5日發行的AEM Screens Feature Pack 202103的相關資訊，請詳閱本頁。」
feature: 功能套件
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 2%

---


# Feature Pack 202103 {#release-notes-for-feature-pack}發行說明

>[!CAUTION]
>建議您升級至最新版Adobe Experience Manager(AEM)。 Screens對AEM 6.3 Screens平台提供維護支援。

## 可用性 {#availability}

AEM Screens發行AEM 6.5 Feature Pack 7。

您可以使用Adobe ID，從[軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載AEM Screens 6.5.7版的最新Feature Pack。 導覽至「**Adobe Experience Manager**」標籤並搜尋「**Screens**」，以取得最新的Feature Pack，標題為「**AEM 6.5 Screens FP7**」。

## 發行日期 {#release-date}

AEM Screens Feature Pack 202103的發行日期為2021年3月5日。

### 新功能 {#what-is-new}

* **AEM Screens播放器自動註冊**

   手動大量註冊數千個播放器非常麻煩，而且會增加時間和成本。 為簡化此過程，「播放器自動註冊」功能允許您在AEM中指定預共用密鑰，該密鑰可以通過配置檔案或移動設備管理(MDM)解決方案被配置到播放器中。

   如需詳細資訊，請參閱[播放器自動註冊](/help/user-guide/auto-registration-players.md) 。


* **使用企業移動性管理來大量布建Android Player**

   大量部署Android播放器時，使用AEM手動註冊每個播放器將變得很麻煩。 強烈建議使用EMM（企業移動管理）解決方案（如VMWare Airwatch、MobileIron或Samsung Knox）來遠程調配和管理您的部署。 AEM Screens Android player支援業界標準的EMM AppConfig，以允許遠端布建。

   如需詳細資訊，請參閱[使用企業行動管理的Android Player大量布建](/help/user-guide/implementing-android-player.md#implementation) 。


### 錯誤修正 {#bug-fixes}

* 改善計算`clientlib`和`asset hashes`的效能。

* 如果快取未失效，SmartSync遷移將破壞播放器。

* 如果「分配」具有&#x200B;*OfflineConfig*，則未建立離線快取。

* 因不支援反向連結原則strict-origin-when-cross-origin而中斷的Tizen播放器更新。

* 更改指定通道的調度&#x200B;*重複*&#x200B;欄位會中斷UI。

* 更新離線內容失敗，出現查詢例外。

* 現在已修正互動式體驗中互動期間，轉換之間的時間延遲。

* 配置更新請求失敗導致出現空白螢幕。

### 已發行AEM Screens播放器{#released-aem-screens-players}

已針對AEM 6.5 Feature Pack 7發行下列AEM Screens播放器：

* Chrome OS
* Windows
* Linux

#### AEM Screens播放器下載{#aem-screens-player-downloads}

若要下載最新的AEM Screens播放器並進一步了解錯誤修正，請參閱&#x200B;**[AEM Screens播放器下載](https://download.macromedia.com/screens/index.html)**。

---
title: 功能套件202103發行說明
description: 本頁摘要說明Feature Pack 202103的發行說明。
translation-type: tm+mt
source-git-commit: dfbf904c1f23f7e41a9d65a270c5ca667ddcdb31
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 2%

---


# 功能套件版本注意事項202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>建議您升級至最新版的Adobe Experience Manager(AEM)。 畫面提供6.3畫AEM面平台的維護支援。

## 可用性 {#availability}

AEM ScreensAEM發行6.5功能套件7。

您可以使用您的Adobe ID，從[軟體散發入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載最新的AEM Screens6.5.7版功能套件。 導覽至「**Adobe Experience Manager**」標籤並搜尋「**畫面**」，以取得最新的功能套件，標題為「**AEM 6.5畫面FP7**」。

## 發行日期 {#release-date}

AEM Screens功能包202103的發行日期為2021年3月05日。

### 新功能 {#what-is-new}

* **AEM Screens球員自動註冊**

   手動大量註冊數千個播放器非常麻煩，而且會增加時間和成本。 為簡化此程式，「播放器自動註冊」功能允許您指定預共用密鑰，AEM該密鑰可通過配置檔案或移動設備管理(MDM)解決方案設定到播放器中。

   如需詳細資訊，請參閱[播放器自動註冊](/help/user-guide/auto-registration-players.md)。


* **使用企業行動管理大量布建Android Player**

   當大量部署Android播放器時，手動註冊每個播放器將變得很麻煩AEM。 強烈建議您使用EMM（企業行動力管理）解決方案，例如VMWare Airwatch、MobileIron或Samsung Knox，以遠端布建及管理您的部署。 AEM ScreensAndroid播放器支援業界標準EMM AppConfig，允許遠端布建。

   如需詳細資訊，請參閱「使用企業行動管理的Android Player大量布建」。[](/help/user-guide/using-emm-bulkprovision-android-player.md)


### 錯誤修正 {#bug-fixes}

* 已改善計算`clientlib`和`asset hashes`的效能。

* 如果快取未失效，SmartSync遷移將會中斷播放器。

* 如果Assignment具有&#x200B;*OfflineConfig*，則未建立離線快取。

* 由於不支援反向連結原則strict-origin-when-cross-origin而中斷的Tizen播放器更新。

* 變更指派頻道的排程&#x200B;*重複*&#x200B;欄位會中斷UI。

* 更新離線內容失敗，但有查詢例外。

* 互動式體驗互動期間的轉場時間延遲現已修正。

* 配置更新請求失敗導致空白螢幕。

### 獲釋的AEM Screens球員{#released-aem-screens-players}

下列AEM Screens播放器適用於AEM6.5功能套件7:

* Chrome OS
* Windows
* Linux

#### AEM Screens播放器下載{#aem-screens-player-downloads}

若要下載最新的AEM Screens播放器並進一步瞭解錯誤修正，請參閱&#x200B;**[AEM Screens播放器下載](https://download.macromedia.com/screens/index.html)**。

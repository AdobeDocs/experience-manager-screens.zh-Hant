---
title: 功能套件202103發行說明
description: 本頁摘要說明Feature Pack 202103的發行說明。
translation-type: tm+mt
source-git-commit: 56432654d0895b892223677c8a03f10181864271
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 功能套件版本注意事項202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>建議您升級至最新版的Adobe Experience Manager(AEM)。 畫面提供6.3畫AEM面平台的維護支援。

## 可用性 {#availability}

AEM ScreensAEM發行6.5功能套件7。

您可以使用您的Adobe ID，從[軟體散發入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載最新的AEM Screens6.5.7版功能套件。 導覽至「**Adobe Experience Manager**」標籤並搜尋「**畫面**」，以取得最新的功能套件，標題為「**AEM 6.5畫面FP7**」。

## 發行日期 {#release-date}

AEM Screens功能包202103的發行日期為2021年3月08日。

### 新功能 {#what-is-new}

* **AEM Screens大量註冊和分配**

   手動大量註冊數千個播放器非常麻煩，而且會增加時間和成本。 為簡化此程式，批量註冊功能允許您指定預先共用的密鑰，該密鑰可AEM通過配置檔案或移動設備管理(MDM)解決方案設定到播放器中。

* **使用企業行動管理大量布建Android Player**

   當大量部署Android播放器時，手動註冊每個播放器將變得很麻煩AEM。 強烈建議您使用EMM（企業行動力管理）解決方案，例如VMWare Airwatch、MobileIron或Samsung Knox，以遠端布建及管理您的部署。 AEM ScreensAndroid播放器支援業界標準EMM Appconfig，允許遠端布建。

* **在AEM Screens頻道中鎖定頁面**

   AEM Screens現在支援&#x200B;*鎖定頁面*，如AEM Sites已實施。 Adobe Experience ManagerAEM()可讓您鎖定頁面，讓其他人無法修改內容。 當您對特定頁面進行大量編輯或需要將頁面凍結一段時間時，這項功能會很有用。

### 錯誤修正 {#bug-fixes}

* 已改善計算`clientlib`和`asset hashes`的效能。

* 如果快取未失效，SmartSync遷移將會中斷播放器。

* 如果Assignment具有&#x200B;*OfflineConfig*，則未建立離線快取。

* 更新Tizen播放器問題，因為不支援反向連結原則strict-origin-when-cross-origin。

* 變更指派渠道的排程「重複」欄位會中斷UI。

* 更新離線內容失敗，但有查詢例外。

* 如果快取未失效，SmartSync遷移將中斷播放器


### 獲釋的AEM Screens球員{#released-aem-screens-players}

下列AEM Screens播放器適用於AEM6.5功能套件7:

* Chrome OS
* Windows
* Android
* 蒂岑
* Linux

#### AEM Screens播放器下載{#aem-screens-player-downloads}

若要下載最新的AEM Screens播放器並進一步瞭解錯誤修正，請參閱&#x200B;**[AEM Screens播放器下載](https://download.macromedia.com/screens/index.html)**。

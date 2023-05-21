---
title: 功能包202103發行說明
description: 「按照本頁獲取2021年3月5日發佈的AEM Screens功能包202103的資訊。」
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 4%

---

# 功能包202103發行說明 {#release-notes-for-feature-pack}

>[!CAUTION]
>建議您升級到最新版本的Adobe Experience Manager(AEM)。 螢幕為6.3螢幕AEM平台提供維護支援。

## 可用性 {#availability}

AEM Screens發AEM布了6.5功能包7。

您可以從以下網站下載AEM Screens6.5.7版的最新功能包： [軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 用你的Adobe ID。 導航到 **Adobe Experience Manager** 頁籤和搜索 **螢幕** 獲取最新功能包的標題為 **AEMFP7 6.5螢幕**。

## 發行日期 {#release-date}

AEM Screens功能包202103的發佈日期為2021年3月5日。

### 新增功能 {#what-is-new}

* **AEM Screens球員自動註冊**

   手動批量註冊數千個玩家非常繁瑣，並增加了時間和成本。 為簡化此過程，「玩家自動註冊」功能允許您在中指定預共用密鑰AEM，該密鑰可通過配置檔案或移動設備管理(MDM)解決方案預配置到播放器中。

   請參閱 [玩家自動註冊](/help/user-guide/auto-registration-players.md) 的子菜單。


* **使用企業移動管理的Android Player批量配置**

   當批量部署Android播放器時，手動註冊每個播放器就變得非常繁瑣AEM。 強烈建議使用EMM（企業移動管理）解決方案（如VMWare Airwatch、MobileIron或Samsung Knox）來遠程配置和管理您的部署。 AEM ScreensAndroid播放器支援行業標準EMM AppConfig，允許遠程配置。

   請參閱 [使用企業移動管理的Android Player批量配置](/help/user-guide/implementing-android-player.md#implementation) 的子菜單。


### 錯誤修正 {#bug-fixes}

* 提高計算效能 `clientlib` 和 `asset hashes`。

* 如果快取未失效，SmartSync遷移將中斷播放器。

* 如果Assignment已建立離線快取，則未建立離線快取 *離線配置*。

* 由於不支援引用策略「嚴格原點時交叉原點」而中斷的Tizen播放器的更新。

* 更改分配的渠道的計畫 *重複* 欄位正在斷開用戶介面。

* 更新離線內容失敗，出現查詢異常。

* 交互體驗中的交互期間之間的時間延遲現在已被固定。

* 配置更新請求失敗導致出現空白螢幕。

### 已釋放AEM Screens球員 {#released-aem-screens-players}

以下AEM Screens玩家AEM將發佈6.5功能包7:

* Chrome作業系統
* Windows
* Linux

#### AEM Screens播放器下載  {#aem-screens-player-downloads}

要下載最新的AEM Screens播放器並瞭解有關錯誤修復的詳細資訊，請參閱 **[AEM Screens播放器下載](https://download.macromedia.com/screens/index.html)**。

---
title: 實施遠程控制
seo-title: Impementing the Remote Control
description: 按照此頁瞭解螢幕遠程控制功能。
seo-description: Follow  this page to learn about using the Screens Remote Control Feature.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
source-git-commit: a256f624c4b647deb4cee7668665ad7b576932e7
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# 使用螢幕遙控器  {#implementing-remote-control}

遠程控制功能使訪問管理UI、通道切換器或功能（如清除快取和重新載入）更加容易。 此外，它還為您提供了查看播放器本地韌體版本和系統資訊的方法。 這特別有用，因為如果玩家已失去連接，就很難連接滑鼠並在無法觸及的生產設備上操作，甚至更AEM難。 這在使用Samsung RMS時也很有用，因為解析度差異會使用滑鼠查找和開啟管理用戶介面非常困難。

## 常見遙控鍵組合 {#using-common-remote-control}

在所有玩家中，您都可以在螢幕遙控器中使用以下鍵組合：

1. 切換管理員UI - CTRL + 1
1. 切換通道切換器 — CTRL + 2
1. 清除快取 — CTRL + ALT + 3
1. 重新載入播放器 — CTRL + 4

## Tizen特定遙控鍵組合 {#using-tizen-remote-control}

特定於Tizen播放器，您可以使用Samsung RMS中提供的硬體遠程或軟體遠程訪問以下功能：

1. A — 切換管理員UI
1. B — 切換通道切換器
1. C — 清除快取
1. D — 重新載入播放器

## 其他使用說明 {#using-additional-remote-control}

1. 開啟管理員UI後，可以使用向上箭頭和向下箭頭來導航頁籤，以查看頁籤中的資訊。
1. 開啟通道切換器後，可以使用向上和向下箭頭鍵來導航通道，並可以按Enter鍵（或遙控器上箭頭中心的按鈕）來切換通道。

下圖說明了Samsung遙控器的關鍵用法：
![影像](assets/tizen/remote.png)

>[!NOTE]
>如果將enableAdminUI和/或enableOSD的設備配置值設定為false，則遠程伺服器將不會切換admin UI和通道切換器。 您也無法使用箭頭鍵導航管理員UI或通道。 但是，您仍然可以清除快取並重新載入播放器。 如果任何鍵盤組合與您的交互內容發生衝突，則可以使用以下代碼禁用遠程控制功能：

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```

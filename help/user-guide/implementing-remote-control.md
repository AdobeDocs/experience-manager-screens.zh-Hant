---
title: 實作遠端控制
description: 瞭解AEM Screens中的Screens遠端控制功能。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 6cb2705e-83e6-46f3-bd71-6688d7edc11f
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 使用Screens遠端控制 {#implementing-remote-control}

遠端控制功能可讓您更輕鬆地存取管理員UI、頻道切換器或功能，例如清除快取和重新載入。 此外，它提供您檢視本機韌體版本和播放器系統資訊的方法。 這項功能特別有用，因為連線滑鼠可能很困難。 或者，在無法存取的生產裝置上操作，如果播放器失去與AEM的連線，更是如此。 使用Samsung RMS時，它也很有用，因為解析度的差異可能會讓使用者難以找到並使用滑鼠開啟Admin UI。

## 通用遠端修飾鍵組合 {#using-common-remote-control}

在所有播放器上，您都可以在Screens遠端控制中使用下列按鍵組合：

1. 切換管理員UI - CTRL + 1
1. 切換頻道切換器 — CTRL + 2
1. 清除快取 — CTRL + ALT + 3
1. 重新載入播放器 — CTRL + 4

## 啟動特定的遠端修飾鍵組合 {#using-tizen-remote-control}

特定於Tizen播放器，您可以使用Samsung RMS提供的硬體遠端或軟體遠端來存取這些功能：

1. A — 切換管理員UI
1. B — 切換頻道切換器
1. C — 清除快取
1. D — 重新載入播放器

## 更多使用說明 {#using-additional-remote-control}

1. 在Admin UI開啟的狀態下，您可以使用向上和向下箭頭來瀏覽標籤，以檢視各標籤上的資訊。
1. 在頻道切換器開啟的情況下，您可以使用向上鍵和向下鍵來導覽頻道。 您也可以按下`Enter`鍵（或遙控器箭號中央的按鈕）來切換頻道。

下圖說明Samsung遠端的主要使用方式：
![影像](assets/tizen/remote.png)

>[!NOTE]
>如果您將enableAdminUI和/或enableOSD的裝置設定值設為false，遠端不會切換管理員UI和頻道切換器。 您無法使用方向鍵來導覽Admin UI或管道。 不過，您仍可清除快取並重新載入播放器。 如果有任何鍵盤組合與使用下列程式碼的互動式內容衝突，您可以停用遠端控制功能：

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```

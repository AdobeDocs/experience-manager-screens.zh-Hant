---
title: 安裝 Screens 播放器
seo-title: Installing Screens Player
description: 請按照本頁瞭解可用AEM Screens播放器的安裝。
seo-description: Installing Screens Player
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: c6506ca62e806ec11d3380d6ac7670bcfcf13adb
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 1%

---

# 安裝AEM Screens播放器 {#installing-player}

本頁介紹如何安裝AEM Screens播放器。

## 可用螢幕播放器 {#available-players}

該AEM Screens播放器可用於Android、Chrome作業系統和Windows。

下載 **AEM Screens選手**，訪問 [6AEM.5播放器下載](https://download.macromedia.com/screens/) 的子菜單。

>[!NOTE]
>
>下載最新播放器(*.exe*)，按照播放器上的步驟完成即席安裝：
>
>1. 長按左上角以開啟管理面板。
>1. 導航到 **配置** 從左側操作菜單中，輸入實例的位AEM置地址 **伺服器** 按一下 **保存**。
>1. 按一下 **註冊** 從左側操作菜單和下面的步驟連結，以完成設備註冊過程。


## 基本播放監視 {#playback-monitoring}

播放器報告各個播放度量 `ping` 預設為30秒。 基於這些指標，我們可以檢測各種邊緣情況，如停滯體驗、空白螢幕和調度問題。 這樣，我們便能瞭解和排除設備上的問題，從而加快您的調查和糾正措施。

在AEM Screens播放器中進行基本播放監視，可以：

* 如果播放器正在正確播放內容，則遠程監視。

* 提高對空白螢幕或現場破壞經驗的反應性。

* 降低向最終用戶顯示中斷體驗的風險。

### 瞭解屬性 {#understand-properties}

以下屬性包括在 `ping`:

| 屬性 | 說明 |
|---|---|
| id {string} | 播放器標識符 |
| activeChannel {string} | 當前正在播放通道路徑，如果未計畫任何內容，則為空 |
| activeElements {string} | 逗號分隔的字串，當前所有播放序列通道中的可見元素（多區域佈局時為多個） |
| isDefaultContent {boolean} | 如果播放頻道被視為預設或回退頻道（即優先順序為1且無計畫），則為true |
| 有ContentChanged {boolean} | 如果內容在過去5分鐘內更改為true，否則為false |
| lastContentChange {string} | 上次內容更改的時間戳 |

>[!NOTE]
>可選地，可以從播放器首選項（啟用回放監視）啟用更高級的屬性，即：
>|屬性|說明|
>|—|
>如果GPU能確認其正在播放實際內容（基於像素分析），則|isContentRendering {boolean}|true

### 限制 {#limitations}

下面列出了基本播放監視的幾個限制：

* 播放器向伺服器報告自己的播放狀態，因此需要活動連接。

* 的 `isContentRendering` 檢查GPU的屬性當前資源過於密集，預設情況下無法啟用，並且需要從播放器首選項中明確選擇加入。 建議不要將其與視頻一起用於製作。

* 此功能僅支援序列通道，尚不涵蓋交互通道(SPA)使用情形。

* 這些指標尚未完全向客戶公開，我們正在努力在不久的將來啟用類似於儀表板的報告和警報機制。

### 其他資源 {#additional-resources}

有關詳細資訊，請參閱以下主題：

* 要下載Android Player，請訪問 **Google Play**。 要瞭解如何實施Android Watchdog，請參閱 [實現Android播放器](implementing-android-player.md)。

* 要實施Chrome OS Player，請參閱 [Chrome管理控制台](implementing-chrome-os-player.md) 的子菜單。

* 要配置AEM ScreensWindows播放器，請參閱 [實施Windows Player](implementing-windows-player.md)。

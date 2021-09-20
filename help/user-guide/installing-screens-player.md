---
title: 安裝Screens Player
seo-title: Installing Screens Player
description: 請詳閱本頁，了解如何安裝可用的AEM Screens Player。
seo-description: Installing Screens Player
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: c6506ca62e806ec11d3380d6ac7670bcfcf13adb
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# 安裝AEM Screens Player {#installing-player}

本頁說明如何安裝AEM Screens播放器。

## 可用螢幕播放器 {#available-players}

AEM Screens播放器適用於Android、Chrome OS和Windows。

若要下載&#x200B;**AEM Screens Player**，請造訪[AEM 6.5 Player下載](https://download.macromedia.com/screens/)頁面。

>[!NOTE]
>
>下載最新的播放器(*.exe*)後，請依照播放器上的步驟完成臨機安裝：
>
>1. 長按左上角以開啟「管理面板」。
>1. 從左側操作菜單導航到&#x200B;**Configuration**，並在&#x200B;**Server**&#x200B;中輸入AEM實例的位置地址，然後按一下&#x200B;**Save**。
>1. 按一下左側操作菜單中的&#x200B;**註冊**&#x200B;連結以及以下步驟以完成設備註冊過程。


## 基本播放監控 {#playback-monitoring}

播放器會報告各種播放量度，每個`ping`預設為30秒。 根據這些量度，我們可以偵測各種邊緣案例，例如體驗停滯、空白畫面和排程問題。 這可讓我們了解和疑難排解裝置上的問題，進而加速與您一起進行調查和採取糾正措施。

AEM Screens播放器中的基本播放監控可讓我們：

* 如果播放器正確播放內容，則遠程監視。

* 改善欄位中空白畫面或體驗損毀的反應性。

* 降低向使用者顯示中斷體驗的風險。

### 了解屬性 {#understand-properties}

每個`ping`中都包含下列屬性：

| 屬性 | 說明 |
|---|---|
| id {string} | 播放器識別碼 |
| activeChannel {string} | 當前正在播放通道路徑；如果未計畫任何內容，則為null |
| activeElements {string} | 逗號分隔字串，所有播放序列頻道中目前可見的元素（若為多區域版面，則為多個元素） |
| isDefaultContent {boolean} | 如果播放管道被視為預設或後援管道，則為true（亦即，優先順序1且無排程） |
| hasContentChanged {boolean} | 如果內容在過去5分鐘內變更，則為true；否則為false |
| lastContentChange {string} | 上次內容變更的時間戳記 |

>[!NOTE]
>您可以選擇從播放器偏好設定（啟用播放監控）啟用更進階的屬性，這是：
>|屬性|說明|
>|—|—|
>如果GPU可確認其正在播放實際內容（基於像素分析），則|isContentRendering {boolean}|true

### 限制 {#limitations}

以下列出基本播放監控的幾項限制：

* 播放器會向伺服器報告自己的播放狀態，因此需要使用中的連線。

* 檢查GPU的`isContentRendering`屬性當前佔用的資源太多，預設情況下無法啟用，需要從播放器首選項中明確選擇加入。 建議您不要將其與生產中的影片搭配使用。

* 此功能僅支援序列管道，不涵蓋互動式管道(SPA)使用案例。

* 這些量度尚未完全公開給客戶，我們正在努力在不久的將來啟用類似控制面板的報表和警報機制。

### 其他資源 {#additional-resources}

如需詳細資訊，請參閱下列主題：

* 若要下載Android Player，請造訪&#x200B;**Google Play**。 若要了解如何實作Android監視程式，請參閱[實作Android播放器](implementing-android-player.md)。

* 若要實作Chrome OS Player，請參閱[Chrome管理控制台](implementing-chrome-os-player.md)以取得詳細資訊。

* 要配置AEM Screens Windows Player，請參閱[實作Windows Player](implementing-windows-player.md)。

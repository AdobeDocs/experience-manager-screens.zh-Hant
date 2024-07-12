---
title: 安裝 Screens 播放器
description: 瞭解如何正確安裝AEM Screens Player。
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 1%

---

# 安裝AEM Screens Player {#installing-player}

本頁說明如何安裝AEM Screens Player。

## 可用的Screens Player {#available-players}

AEM Screens Player適用於Android™、Chrome作業系統和Windows。

若要下載&#x200B;**AEM Screens Player**，請造訪[AEM 6.5播放器下載](https://download.macromedia.com/screens/)頁面。

>[!NOTE]
>
>下載最新的播放器(*.exe*)之後，請依照播放器上的步驟進行，以便完成臨機安裝：
>
>1. 長按左上角以開啟「管理」面板。
>1. 從左側動作功能表瀏覽至&#x200B;**組態**，並在&#x200B;**伺服器**&#x200B;中輸入AEM執行個體的位置位址，然後按一下&#x200B;**儲存**。
>1. 按一下左側動作功能表的&#x200B;**註冊**&#x200B;連結，然後依照下列步驟完成裝置註冊程式。

## 基本播放監視 {#playback-monitoring}

播放器會報告每個`ping`預設為30秒的各種播放量度。 根據這些量度，它可以偵測各種邊緣情況，例如停滯體驗、空白畫面和排程問題。 它可讓我們瞭解裝置的問題並進行疑難排解，為您加快調查和修正措施。

AEM Screens Player中的基本播放監視可讓您進行下列工作：

* 遠端監視（如果播放器正確播放內容）。

* 改善對空白畫面或欄位中中斷體驗的反應能力。

* 降低向一般使用者顯示中斷體驗的風險。

### 瞭解屬性 {#understand-properties}

下列屬性包含在每個`ping`中：

| 屬性 | 說明 |
|---|---|
| 識別碼{string} | 播放器識別碼 |
| activeChannel {string} | 目前播放管道路徑，或若未排定任何專案，則為null |
| activeElements {string} | 以逗號分隔的字串，目前所有播放順序頻道中可見的元素（多區域版面配置中有多個） |
| isDefaultContent {boolean} | 如果播放頻道被視為預設或遞補頻道（即優先順序為1且沒有排程），則為true |
| hasContentChanged {boolean} | 如果內容在過去5分鐘內變更，則為true ；否則為false |
| lastContentChange {string} | 上次內容變更的時間戳記 |

>[!NOTE]
>或者，您也可以從播放器偏好設定（啟用播放監視）啟用更進階的屬性，即：
>
>| 屬性 | 說明 |
>|---|---|
>| isContentRendering {boolean} | 如果GPU可以確認正在播放實際內容（根據畫素分析），則為true |

### 限制 {#limitations}

基本播放監視的幾個限制列於下方：

* 播放器會向伺服器報告自己的播放狀態，因此需要使用中的連線。

* 檢查GPU的`isContentRendering`屬性在預設情況下會更耗用資源，而且需要播放器偏好設定中的明確選擇加入。 Adobe建議您不要在生產環境中的影片中使用。

* 此功能僅支援序列頻道，尚未涵蓋互動式頻道(SPA)使用案例。

* 這些量度尚未完整開放給客戶，但Adobe正在努力儘快啟用類似控制面板的報告和警報機制。

### 其他資源 {#additional-resources}

如需深入資訊，請參閱下列主題：

* 若要下載Android™ Player，請造訪&#x200B;**Google Play**。 若要瞭解如何實作Android™ Watchdog，請參閱[實作Android™播放器](implementing-android-player.md)。

* 若要實作Chrome OS Player，請參閱[Chrome管理主控台](implementing-chrome-os-player.md)以取得詳細資訊。

* 若要設定AEM Screens Windows Player，請參閱[實作Windows Player](implementing-windows-player.md)。

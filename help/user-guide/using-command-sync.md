---
title: 使用命令同步
seo-title: 使用命令同步
description: 請依照本頁瞭解如何使用命令同步。
seo-description: 請依照本頁瞭解如何使用命令同步。
translation-type: tm+mt
source-git-commit: 7b842534e00e50aa1f066e73539edfa3915aa5e6

---


# 命令同步 {#command-sync}

以下頁介紹如何使用命令同步。 命令同步允許在不同播放器之間同步播放。 玩家可以播放不同的內容，但每個資產需要有相同的持續時間。

>[!IMPORTANT]
>此功能不支援內嵌序列、動態內嵌序列、應用程式頻道或轉場。

## 概覽 {#overview}

數位標牌解決方案需要支援視訊牆和同步播放，以支援例如新年計數或大型視訊分割為多個螢幕來播放的場景，而這正是指令同步的開始。

若要使用「命令同步」，一個播放器充當主 *播* ，並傳送命令，而所有其他播放器則當它們收到命令時 ** ，充當用戶端並播放。

當主 *程式* (Master)要開始播放項目時，會向所有註冊的客戶端發送命令。 此項目的裝載可以是要播放的項目的索引和／或要播放的元素的外部html。

## 實作命令同步 {#using-command-sync}

下節說明如何在AEM Screens專案中使用「命令同步」。

>[!NOTE]
>對於同步播放，要求所有硬體設備具有相同的硬體規格，最好是相同的作業系統。 不建議在不同的硬體和作業系統之間同步。

### 設定專案 {#setting-up}

在使用「命令同步」功能之前，請確定您有專案和頻道，並為專案設定內容。

1. 下列範例將展示名為 **CommandSyncDemo的示範專案** ，以及序列頻道 **ChannelLobby**。

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >如要瞭解如何建立頻道或新增內容至頻道，請參閱建立 [和管理頻道](/help/user-guide/managing-channels.md)

   頻道包含下列內容，如下圖所示。

   ![image1](assets/command-sync/command-sync2-1.png)

1. 在「位置」資料 **夾中** ，建立顯示，如下圖所示。
   ![image1](assets/command-sync/command-sync3-1.png)

1. 將channelLobby指 **派給您的** LobbyDisplay ****。
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >若要瞭解如何指派渠道給顯示，請參閱建立 [和管理顯示](/help/user-guide/managing-displays.md)。

1. 導覽至「 **裝置** 」檔案夾，然後從動作列按 **一下「裝置管理員** 」以註冊裝置。

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >若要瞭解如何指派渠道給顯示，請參閱建立 [和管理顯示](/help/user-guide/managing-displays.md)

1. 為進行示範，此範例會將chrome裝置和Windows播放器分別顯示為兩部裝置。 這兩個裝置都指向相同的顯示。
   ![image1](assets/command-sync6.png)

### 更新頻道設定

1. 導覽至 **ChannelLobby** ，然後按一 **下動作列中的「編輯** 」以更新頻道設定。

1. 選擇整個渠道，如下圖所示。
   ![image1](assets/command-sync/command-sync7-1.png)

1. 按一下扳手圖示以開啟「頁 **面** 」對話方塊。
   ![image1](assets/command-sync/command-sync8-1.png)

1. 在「策 *略* 」欄位中輸入 **同步關鍵字** 。

   ![image1](assets/command-sync/command-sync9-1.png)


### 設定主版 {#setting-up-master}

1. 從 **CommandSyncDemo** —> **Locations** —> **Lobby** — **Lobby Display And****** click on Dashboard on Dashboard on the Action the Locations
您將在 **DEVICES面板中看到這兩種裝置（chrome和windows player）** ，如下圖所示。
   ![image1](assets/command-sync/command-sync10-1.png)

1. 從「裝 **置** 」面板中，選取您要設為主版的裝置。 下列範例示範將Chrome裝置設為主版。 按一下「 **設為主裝置」**。

   ![image1](assets/command-sync/command-sync11-1.png)

1. 在「設為主設備」 **中輸入IP地址** ，然後按一下「 **保存」**。

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
> 您可以將多個裝置設為主裝置。

### 與Master同步 {#sync-up-master}

1. 將Chrome裝置設為主版後，您就可以同步其他裝置（在本例中為Windows播放器），以與主版同步。
從「 **DEVICES** 」面板中選擇其他設備（在本例中為Windows Player），然後按一下「 **Sync to master device**」（同步到主設備），如下圖所示。

   ![image1](assets/command-sync/command-sync13-1.png)

1. 從清單中選擇設備，然後按一下「 **保存**」。

   >[注意:]
   > 「同 **步至主設備** 」對話框將顯示主設備清單。 您可以選取想要的偏好設定。

1. 當裝置（Windows播放器）與主版（Chrome播放器）同步後，您就會在「裝置」面板中看到同步的 **裝置** 。

   ![image1](assets/command-sync/command-sync14-1.png)

### 取消與主版同步 {#desync-up-master}

將設備或設備同步到主設備後，可以從該設備中取消同步分配。

>[!NOTE]
>如果您取消同步主設備，它也會取消連結與該主設備關聯的所有客戶端設備。

若要從主裝置移除同步，請遵循下列步驟：

1. 導覽至「裝 **置** 」面板並選取裝置。

1. 按一下「 **Desync device(s)** 」 ，將客戶機與主設備取消同步。

   ![image1](assets/command-sync/command-sync15-1.png)

1. 按一下 **確認** ，從主設備中取消同步所選設備。

   >[注意:]
   > 如果您選擇主設備並使用去同步選項，則所有連接到主設備的設備都將在一個步驟中取消同步。

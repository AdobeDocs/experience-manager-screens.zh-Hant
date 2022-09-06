---
title: 使用命令同步
seo-title: Using Command Sync
description: 請按照本頁了解如何使用命令同步。
seo-description: Follow this page to learn about how to use Command Sync.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: 43ac19cf7ef63ec17611cf19ca357f791dca6e87
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 2%

---

# 命令同步 {#command-sync}

以下頁介紹如何使用命令同步。 命令同步允許在不同播放器之間同步播放。 播放器可以播放不同的內容，但每個資產需要有相同的持續時間。

>[!IMPORTANT]
>
>此功能不支援內嵌序列、動態內嵌序列、應用程式通道或轉變。

## 總覽 {#overview}

數位看板解決方案需要支援視訊牆和同步播放，以支援新年計數或大型視訊切割到多個螢幕來播放等情況，而命令同步就是在這裡開始發揮作用的。

若要使用「命令同步」，一個播放器可 *主要* 併發送命令，其他所有玩家 *客戶* 當他們收到命令時播放。

此 *主要* 在要開始播放項時向所有註冊客戶端發送命令。 此項目的有效負載可以是要播放之項目的索引和/或要播放之元素的外部html。

## 實作命令同步 {#using-command-sync}

以下章節說明如何在AEM Screens專案中使用命令同步。

>[!NOTE]
>
>對於同步播放，要求所有硬體設備具有相同的硬體規範，最好是相同的作業系統。 不建議在不同的硬體和作業系統之間同步。

### 設定專案 {#setting-up}

使用「命令同步」功能之前，請確保您有項目和通道，其中已為項目設定了內容。

1. 下列範例將展示名為的示範專案 **CommandSyncDemo** 和序列頻道 **ChannelLobby**.

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >若要了解如何建立管道或將內容新增至管道，請參閱 [建立和管理管道](/help/user-guide/managing-channels.md)

   管道包含下列內容，如下圖所示。

   ![image1](assets/command-sync/command-sync2-1.png)

1. 建立位置 **大堂** 然後，將標題為 **LobbyDisplay** 在 **位置** ，如下圖所示。
   ![image1](assets/command-sync/command-sync3-1.png)

1. 指派管道， **ChannelLobby** 至 **LobbyDisplay**. 您現在可以從顯示控制面板檢視指派給顯示的管道。
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >若要了解如何指派管道給顯示器，請參閱 [建立和管理顯示](/help/user-guide/managing-displays.md).

1. 導覽至 **裝置** 資料夾，按一下 **裝置管理員** 從動作列註冊裝置。

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >若要了解如何註冊裝置，請參閱 [設備註冊](/help/user-guide/device-registration.md)

1. 為了示範，此範例將Chrome裝置和Windows播放器示範為兩個不同的裝置。 這兩個裝置都指向相同的顯示器。
   ![image1](assets/command-sync6.png)

### 更新通道設定

1. 導覽至 **ChannelLobby** 按一下 **編輯** 從動作列更新通道設定。

1. 選取整個通道，如下圖所示。
   ![image1](assets/command-sync/command-sync7-1.png)

1. 按一下扳手圖示以開啟 **頁面** 對話框。
   ![image1](assets/command-sync/command-sync8-1.png)

1. 輸入 *同步* 關鍵字 **策略** 欄位。

   ![image1](assets/command-sync/command-sync9-1.png)


### 設定主要 {#setting-up-primary}

1. 從導覽至顯示控制面板 **CommandSyncDemo** —> **位置**  —> **大堂** —> **LobbyDisplay** 按一下 **控制面板** 從動作列。
您會在 **裝置** ，如下圖所示。
   ![image1](assets/command-sync/command-sync10-1.png)

1. 從 **裝置** 面板中，選擇要設定為主設備的設備。 下列範例示範如何將Chrome裝置設為主要裝置。 按一下 **設定為主設備**.

   ![image1](assets/command-sync/command-sync11-1.png)

1. 在 **設定為主設備** 按一下 **儲存**.

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>您可以將多個裝置設定為主要裝置。

### 與主要同步 {#sync-up-primary}

1. 將Chrome裝置設為主要裝置後，您就可以同步其他裝置（在此例中是Windows播放器）以與主要裝置同步。
從 **裝置** 並按一下 **同步到主設備**，如下圖所示。

   ![image1](assets/command-sync/command-sync13-1.png)

1. 從清單中選擇設備，然後按一下 **儲存**.

   >[注意:]
   > 此 **同步到主設備** 對話框將顯示主設備的清單。 您可以選取想要的偏好設定。

1. 將裝置（Windows播放器）同步至主要（Chrome播放器）後，您會在 **裝置** 中。

   ![image1](assets/command-sync/command-sync14-1.png)

### 與主要伺服器取消同步 {#desync-up-primary}

將設備或設備同步到主設備後，可以從該設備取消同步分配。

>[!NOTE]
>
>如果取消同步主設備，它還會取消與該主設備關聯的所有客戶端設備的連結。

若要從主要裝置移除同步，請遵循下列步驟：

1. 導覽至 **裝置** 面板，然後選取裝置。

1. 按一下 **取消同步設備** 將客戶端與主設備取消同步。

   ![image1](assets/command-sync/command-sync15-1.png)

1. 按一下 **確認** 將選定設備與主設備取消同步。

   >[注意:]
   > 如果您選取主要裝置並使用取消同步選項，則所有連線至主要裝置的裝置都會在一個步驟中取消同步。

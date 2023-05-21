---
title: 使用命令同步
seo-title: Using Command Sync
description: 按照此頁瞭解如何使用命令同步。
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

以下頁介紹如何使用命令同步。 命令同步允許在不同播放器之間同步播放。 玩家可以播放不同的內容，但每種資產需要具有相同的持續時間。

>[!IMPORTANT]
>
>此功能不支援嵌入序列、動態嵌入序列、應用程式通道或過渡。

## 概觀 {#overview}

數字標牌解決方案需要支援視頻牆和同步播放，以支援新年倒計時或在多個螢幕上進行大視頻切片播放等場景，而Command Sync正是在這些場景中發揮作用的。

要使用命令同步，一個播放器充當 *主* 發出指令，其他所有玩家 *客戶* 當他們收到命令時播放。

的 *主* 當所有註冊的客戶端都要開始回放項目時，向其發送命令。 此項的有效負載可以是要播放的項的索引和/或要播放的元素的外部html。

## 實現命令同步 {#using-command-sync}

下節介紹如何在AEM Screens項目中使用命令同步。

>[!NOTE]
>
>對於同步播放，要求所有硬體設備具有相同的硬體規格，最好是相同的作業系統。 不建議在不同硬體和作業系統之間同步。

### 設定專案 {#setting-up}

在使用「命令同步」功能之前，請確保您有一個項目和一個頻道，該頻道為項目設定了內容。

1. 以下示例展示了一個名為 **CommandSyncDemo** 和序列頻道 **渠道大堂**。

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >要瞭解如何建立頻道或向頻道添加內容，請參閱 [建立和管理渠道](/help/user-guide/managing-channels.md)

   該頻道包含以下內容，如下圖所示。

   ![image1](assets/command-sync/command-sync2-1.png)

1. 建立位置 **大堂** 然後顯示標題為 **大廳顯示** 的 **位置** 資料夾，如下圖所示。
   ![image1](assets/command-sync/command-sync3-1.png)

1. 分配通道， **渠道大堂** 到 **大廳顯示**。 現在，您可以從顯示操控板查看指定到顯示的通道。
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >要瞭解如何為顯示器分配通道，請參閱 [建立和管理顯示](/help/user-guide/managing-displays.md)。

1. 導航到 **設備** 資料夾，按一下 **設備管理器** 的子菜單。

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >要瞭解如何註冊設備，請參閱 [設備註冊](/help/user-guide/device-registration.md)

1. 為了進行演示，此示例將chrome設備和windows播放器作為兩個獨立的設備進行演示。 兩個設備指向同一顯示器。
   ![image1](assets/command-sync6.png)

### 更新通道設定

1. 導航到 **渠道大堂** 按一下 **編輯** 的子菜單。

1. 選擇下圖所示的整個通道。
   ![image1](assets/command-sync/command-sync7-1.png)

1. 按一下扳手錶徵圖以開啟 **頁面** 對話框。
   ![image1](assets/command-sync/command-sync8-1.png)

1. 輸入 *已同步* 關鍵字 **策略** 的子菜單。

   ![image1](assets/command-sync/command-sync9-1.png)


### 設定主 {#setting-up-primary}

1. 導航到顯示儀表板 **CommandSyncDemo** —> **位置**  —> **大堂** —> **大廳顯示** 按一下 **儀表板** 按鈕。
您將在中看到兩個設備（chrome和windows播放器） **設備** 面板，如下圖所示。
   ![image1](assets/command-sync/command-sync10-1.png)

1. 從 **設備** 面板，選擇要設定為主設備的設備。 以下示例演示將Chrome設備設定為主設備。 按一下 **設定為主設備**。

   ![image1](assets/command-sync/command-sync11-1.png)

1. 在中輸入IP地址 **設定為主設備** 按一下 **保存**。

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>可以將多個設備設定為主設備。

### 正在與主同步 {#sync-up-primary}

1. 一旦將Chrome設備設定為主設備，就可以同步其他設備（在本例中為windows播放器）以與主設備同步。
從 **設備** 並按一下 **同步到主設備**，如下圖所示。

   ![image1](assets/command-sync/command-sync13-1.png)

1. 從清單中選擇設備，然後按一下 **保存**。

   >[注意:]
   > 的 **同步到主設備** 對話框將顯示主設備清單。 可以選擇所需的首選項之一。

1. 設備（Windows播放器）同步到主（Chrome播放器）後，您將看到在 **設備** 的子菜單。

   ![image1](assets/command-sync/command-sync14-1.png)

### 取消與主同步 {#desync-up-primary}

將設備或設備同步到主設備後，可以從該設備中取消分配同步。

>[!NOTE]
>
>如果取消同步主設備，它還會取消與該主設備關聯的所有客戶端設備的連結。

要從主設備中刪除同步，請執行以下步驟：

1. 導航到 **設備** 並選擇設備。

1. 按一下 **取消同步設備** 從主設備中取消同步客戶端。

   ![image1](assets/command-sync/command-sync15-1.png)

1. 按一下 **確認** 從主設備中取消同步選定設備。

   >[注意:]
   > 如果選擇主設備並使用取消同步選項，則所有連接到主設備的設備將在一個步驟中取消同步。

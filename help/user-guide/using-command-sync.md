---
title: 使用命令同步
seo-title: 使用命令同步
description: 請依照本頁瞭解如何使用命令同步。
seo-description: 請依照本頁瞭解如何使用命令同步。
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 2%

---


# 命令同步{#command-sync}

以下頁介紹如何使用命令同步。 命令同步允許在不同播放器之間同步播放。 玩家可以播放不同的內容，但每個資產需要有相同的持續時間。

>[!IMPORTANT]
>
>此功能不支援內嵌序列、動態內嵌序列、應用程式頻道或轉場。

## 概覽 {#overview}

數位標牌解決方案需要支援視訊牆和同步播放，以支援例如新年計數或大型視訊分割為多個螢幕來播放的場景，而這正是指令同步的開始。

若要使用命令同步，一個播放器充當&#x200B;*master*&#x200B;併發送命令，而所有其他播放器充當&#x200B;*客戶端*，當他們收到命令時播放。

當&#x200B;*master*&#x200B;要開始播放項目時，會向所有註冊的客戶端發送命令。 此項目的裝載可以是要播放的項目的索引和／或要播放的元素的外部html。

## 實施命令同步{#using-command-sync}

下節說明如何在AEM Screens專案中使用「命令同步」。

>[!NOTE]
>
>對於同步播放，要求所有硬體設備具有相同的硬體規格，最好是相同的作業系統。 不建議在不同的硬體和作業系統之間同步。

### 設定項目{#setting-up}

在使用「命令同步」功能之前，請確定您有專案和頻道，並為專案設定內容。

1. 以下示例展示名為&#x200B;**CommandSyncDemo**&#x200B;的演示項目和序列頻道&#x200B;**ChannelLobby**。

   ![影像1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >若要瞭解如何建立頻道或新增內容至頻道，請參閱[建立和管理頻道](/help/user-guide/managing-channels.md)

   頻道包含下列內容，如下圖所示。

   ![影像1](assets/command-sync/command-sync2-1.png)

1. 在&#x200B;**Locations**資料夾中建立顯示，如下圖所示。
   ![影像1](assets/command-sync/command-sync3-1.png)

1. 將渠道&#x200B;**ChannelLobby**&#x200B;分配給您的&#x200B;**LobbyDisplay**。
   ![影像1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >要瞭解如何為顯示器分配通道，請參閱[建立和管理顯示](/help/user-guide/managing-displays.md)。

1. 導航到&#x200B;**設備**&#x200B;資料夾，然後按一下操作欄中的&#x200B;**設備管理器**&#x200B;註冊設備。

   ![影像1](assets/command-sync5.png)

   >[!NOTE]
   >
   >要瞭解如何為顯示器分配通道，請參閱[建立和管理顯示](/help/user-guide/managing-displays.md)

1. 為進行示範，此範例會將chrome裝置和Windows播放器分別顯示為兩部裝置。 這兩個裝置都指向相同的顯示。
   ![影像1](assets/command-sync6.png)

### 更新頻道設定

1. 導覽至&#x200B;**ChannelLobby**，然後從動作列按一下「編輯」以更新頻道設定。****

1. 選擇整個渠道，如下圖所示。
   ![影像1](assets/command-sync/command-sync7-1.png)

1. 按一下扳手圖示以開啟&#x200B;**Page**對話方塊。
   ![影像1](assets/command-sync/command-sync8-1.png)

1. 在&#x200B;**策略**&#x200B;欄位中輸入&#x200B;*synced*&#x200B;關鍵字。

   ![影像1](assets/command-sync/command-sync9-1.png)


### 設定主{#setting-up-master}

1. 從&#x200B;**CommandSyncDemo** —> **Locations** —> **Lobby** —> **LobbyDisplay**&#x200B;導覽至顯示控制面板，然後從操作欄按一下&#x200B;**Dashboard**。
您將在**DEVICES**面板中看到兩個裝置（chrome和windows player），如下圖所示。
   ![影像1](assets/command-sync/command-sync10-1.png)

1. 從&#x200B;**DEVICES**&#x200B;面板中，選擇要設定為主設備的設備。 下列範例示範將Chrome裝置設為主版。 按一下「Set as master device **（設定為主設備&lt;a1/>）」。**

   ![影像1](assets/command-sync/command-sync11-1.png)

1. 在&#x200B;**Set as master device**&#x200B;中輸入IP地址，然後按一下&#x200B;**Save**。

   ![影像1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>您可以將多個裝置設為主裝置。

### 與主版{#sync-up-master}同步

1. 將Chrome裝置設為主版後，您就可以同步其他裝置（在本例中為Windows播放器），以與主版同步。
從**DEVICES**&#x200B;面板中選擇其他設備（在本例中為windows player），然後按一下&#x200B;**同步到主設備**，如下圖所示。

   ![影像1](assets/command-sync/command-sync13-1.png)

1. 從清單中選擇設備，然後按一下「保存」。****

   >[注意:]
   > **同步至主設備**&#x200B;對話框將顯示主設備清單。 您可以選取想要的偏好設定。

1. 當裝置（Windows播放器）與主版（Chrome播放器）同步後，您會在&#x200B;**DEVICES**&#x200B;面板中看到同步的裝置。

   ![影像1](assets/command-sync/command-sync14-1.png)

### 與主版{#desync-up-master}取消同步

將設備或設備同步到主設備後，可以從該設備中取消同步分配。

>[!NOTE]
>
>如果您取消同步主設備，它也會取消連結與該主設備關聯的所有客戶端設備。

若要從主裝置移除同步，請遵循下列步驟：

1. 導覽至&#x200B;**DEVICES**&#x200B;面板並選取裝置。

1. 按一下&#x200B;**取消同步設備** ，將客戶機與主設備取消同步。

   ![影像1](assets/command-sync/command-sync15-1.png)

1. 按一下&#x200B;**確認** ，將選定設備與主設備取消同步。

   >[注意:]
   > 如果您選擇主設備並使用去同步選項，則所有連接到主設備的設備都將在一個步驟中取消同步。

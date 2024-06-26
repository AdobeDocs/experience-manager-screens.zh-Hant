---
title: 使用命令同步
description: 進一步瞭解如何使用AEM Screens中的Command Sync。
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 0%

---

# 命令同步 {#command-sync}

以下頁面說明如何使用「命令同步」。 Command Sync允許跨不同播放器同步處理播放。 播放器可播放不同內容，但每個資產必須具有相同的持續時間。

>[!IMPORTANT]
>
>此功能不支援內嵌序列、動態內嵌序列、應用程式通道或轉接。

## 概觀 {#overview}

數位看板解決方案必須支援視訊牆面與同步播放。 如果您嘗試支援新年倒數或大型影片片段在多個熒幕播放等情境，則此情境為真。 在這些情況下，「命令同步」就會發揮作用。

若要使用Command Sync，單一播放器可充當 *主要* 並傳送指令，而所有其他播放器則充當 *使用者端* 並在收到指令時播放。

此 *主要* 即將開始播放專案時，會傳送命令給所有已註冊的使用者端。 此動作的裝載可以是要播放專案的索引、要播放的元素的外部HTML，或兩者皆有。

## 實作命令同步 {#using-command-sync}

下節說明如何在AEM Screens專案中使用「Command Sync」。

>[!NOTE]
>
>若要進行同步播放，所有硬體裝置都必須具備相同的硬體規格，而且最好是相同的作業系統。 不建議在不同的硬體與作業系統之間同步處理。

### 設定專案 {#setting-up}

使用「命令同步」功能之前，請確定您擁有專案和管道，且管道中有專案設定的內容。

1. 以下範例示範專案 **CommandSyncDemo** 和順序頻道 **頻道大廳**.

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >若要瞭解如何建立管道或新增內容至管道，請參閱 [建立和管理管道](/help/user-guide/managing-channels.md)

   此頻道包含下列內容，如下圖所示。

   ![image1](assets/command-sync/command-sync2-1.png)

1. 建立位置 **大廳** 然後顯示標題為 **LobbyDisplay** 在 **位置** 資料夾，如下圖所示。
   ![image1](assets/command-sync/command-sync3-1.png)

1. 指派管道， **頻道大廳** 至您的 **LobbyDisplay**. 您現在可以從顯示控制面板檢視指派給顯示的管道。
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >若要瞭解如何將頻道指派給顯示區，請參閱 [建立和管理顯示器](/help/user-guide/managing-displays.md).

1. 導覽至 **裝置** 資料夾。
1. 按一下 **裝置管理員** 從動作列移除。

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >若要瞭解如何註冊裝置，請參閱 [裝置註冊](/help/user-guide/device-registration.md)

1. 為了示範，此範例將Chrome裝置和Windows Player顯示為兩個獨立的裝置。 兩個裝置都指向相同的顯示器。
   ![image1](assets/command-sync6.png)

### 更新頻道設定

1. 瀏覽至 **頻道大廳**.
1. 按一下 **編輯** 從動作列移除。
1. 按一下整個通道，如下圖所示。
   ![image1](assets/command-sync/command-sync7-1.png)

1. 按一下扳手圖示。
   ![image1](assets/command-sync/command-sync8-1.png)

1. 在 **頁面** 對話方塊中，輸入 *已同步* 中的關鍵字 **策略** 欄位。
   ![image1](assets/command-sync/command-sync9-1.png)


### 設定主要 {#setting-up-primary}

1. 從以下位置導覽至顯示控制面板： **CommandSyncDemo** > **位置**  > **大廳** > **LobbyDisplay**. 然後按一下 **儀表板** 從動作列移除。
請注意中的兩個裝置（Chrome和Windows Player） **裝置** 面板，如下列所示：
   ![image1](assets/command-sync/command-sync10-1.png)

1. 從 **裝置** 面板，按一下要設定為主要裝置的裝置。 下列範例示範如何將Chrome裝置設定為主要裝置。 按一下 **設為主要裝置**.

   ![image1](assets/command-sync/command-sync11-1.png)

1. 在中輸入IP位址 **設為主要裝置** 並按一下 **儲存**.

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>您可以將多個裝置設定為主要裝置。

### 正在與主要播放器同步 {#sync-up-primary}

1. 將Chrome裝置設為主要裝置後，請同步處理其他裝置（在此例中為Windows Player），以便與主要裝置同步。
按一下上的另一個裝置（在此例中為Windows Player） **裝置** 面板並按一下 **同步處理至主要裝置**.

   ![image1](assets/command-sync/command-sync13-1.png)

1. 從清單中按一下裝置，然後按一下 **儲存**.

   >[注意：]
   > 此 **同步處理至主要裝置** 對話方塊會顯示主要裝置的清單。 選取偏好的專案。

1. 當裝置(Windows Player)同步至主要裝置(Chrome Player)時，您會在中看到已同步的裝置 **裝置** 面板。

   ![image1](assets/command-sync/command-sync14-1.png)

### 正在與主要播放器取消同步 {#desync-up-primary}

將一或多個裝置同步至主要裝置後，即可從該裝置解除同步指派。

>[!NOTE]
>
>如果您取消同步處理主要裝置，它也會取消連結與該主要裝置相關聯的所有使用者端裝置。

若要從主要裝置移除同步處理，請遵循下列步驟：

1. 導覽至 **裝置** 面板，然後按一下裝置。

1. 按一下 **取消同步處理裝置** 以便從主要裝置取消同步處理使用者端。

   ![image1](assets/command-sync/command-sync15-1.png)

1. 按一下 **確認** 將選取的裝置從主要裝置取消同步。

   >[注意：]
   > 如果您按一下主要裝置並使用「取消同步」選項，則所有連線至主要裝置的裝置都會在單一步驟中取消同步。

---
title: AEM畫面中的語音識別
description: 此頁面說明AEM Screens中的語音識別功能。
translation-type: tm+mt
source-git-commit: c46cd26f5067468aadf80a822fffce1d5f0b5d9a
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 1%

---


# AEM畫面中的語音識別 {#voice-recognition}

## 概覽 {#overview}

語音辨識功能可讓AEM Screens頻道中由語音互動驅動的內容變更。

內容作者可以將顯示設為啟用語音。 這允許根據顯示器註冊的所有播放器理解語音。 您必須啟用「顯示」的語音識別，並將每個頻道與唯一標籤建立關聯，以觸發頻道轉換。

>[!NOTE]
>播放器硬體必須支援語音輸入，例如麥克風。

>[!IMPORTANT]
> 語音識別功能僅適用於Chrome和電子播放器。

## 實施語音識別 {#implementing}

以下章節說明如何在AEM Screens專案中啟用和使用「語音辨識」功能。

### 設定專案 {#setting-up}

在使用語音識別功能之前，請確定您有專案和頻道，並為專案設定內容。

1. 下列範例展示名為 **VoiceDemo** 的示範專案，以及3種 **Main**、 **ColdDrinks**&#x200B;和 **** HotDrinks，如下圖所示。

   >[!NOTE]
   >
   >如要瞭解如何建立頻道或新增內容至頻道，請參閱建立 [和管理頻道](/help/user-guide/managing-channels.md)

1. 導覽至每個頻道並新增內容。 例如，導覽至 **VoiceDemo** —> **Channels** —> **Main** ，然後選取頻道。 按一 **下動作列的** 「編輯」以開啟編輯器，並視需要新增內容（影像／視訊）。 同樣地，您也可將內容 **加入ColdDrinks** 和 **HotDrinks頻道** 。

   頻道現在包含下列內容，如下圖所示。

   **主要**:

   **ColdDrinks**:

   **熱飲**:

### 設定渠道的標籤 {#setting-tags}

在將內容新增至頻道後，您必須導覽至每個頻道，並新增適當的標籤，以觸發語音辨識。

請依照下列步驟，將標籤新增至您的渠道：

1. 導覽至每個頻道並新增內容。 例如，導覽至 **VoiceDemo** —> **Channels** —> **Main** ，然後選取頻道。

1. 從動 **作列按一下** 「屬性」。

1. 導覽至「 **基本** 」索引標籤，並從「標籤」欄位中選取已有的標籤 **** ，或建立新標籤。

1. 完成 **後，按一下「儲存** 並關閉」。


### 將頻道指派給顯示 {#channel-assignment}

1. 在「位置」資料 **夾中** ，建立顯示，如下圖所示。

   >[!NOTE]
   >
   >若要瞭解如何指派渠道給顯示，請參閱建立 [和管理顯示](/help/user-guide/managing-displays.md)。

1. 將頻道Main **、** ColdDrinks **和** HotDrinks指派給您的LobbyDisplay **(大******&#x200B;堂展示)。


1. 將下列屬性設為每個頻道。

   >[!NOTE]
   >
   >若要瞭解如何指派渠道給顯示，請參閱建立 [和管理顯示](/help/user-guide/managing-displays.md)。

1. 將頻道指派給顯示器後，請導覽至 **LobbyDisplay** ，然後選取顯示器。 從操 **作欄中** ，選擇屬性。

1. 導覽至「顯 **示** 」索引標籤，並在「內容」下啟用 **「語音** 」 **選項**。

   >[!NOTE]
   >必須從顯示器中啟用語音識別功能。

## 在Chrome Player中檢視內容 {#viewing-content}

完成上述步驟後，您就可以註冊您的chrome裝置並檢視輸出。

請遵循下列步驟：

1. 導覽至「 **裝置** 」檔案夾，然後從動作列按 **一下「裝置管理員** 」以註冊裝置。







---
title: AEM畫面中的語音識別
description: 此頁面說明AEM Screens中的語音識別功能。
translation-type: tm+mt
source-git-commit: b7d7d4ec200d3eb7cd7bac4253c8664e5bd4de81
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 3%

---


# AEM畫面中的語音識別 {#voice-recognition}

>[重要]
>**重要隱私權資訊**
>使用語音識別功能時，請遵循您所在地區的所有適用法律與道德准則（包括但不限於向使用者顯示播放器使用語音識別）。 Adobe Inc.不會接收、儲存或處理任何語音相關資訊。 AEM Screens播放器會使用瀏覽引擎內建的標準網頁語音API。 在幕後，您的語音波形會傳送至Google的伺服器，以從語音轉換為文字，而播放器會比對設定的關鍵字。
>
>如需詳細 [資訊，請參閱網頁語音API的Google隱私權白皮書](https://www.google.com/chrome/privacy/whitepaper.html#speech) 。


## 概覽 {#overview}

語音辨識功能可讓AEM Screens頻道中由語音互動驅動的內容變更。

內容作者可以將顯示設為啟用語音。 這項功能的目的是讓客戶運用語音作為與顯示器互動的方式。 一些類似的使用案例包括在商店中尋找產品建議、在用餐者和餐廳訂購功能表項目。 此功能可提高使用者的協助功能，並可大幅提升客戶體驗。


>[!NOTE]
>播放器硬體必須支援語音輸入，例如麥克風。

>[!IMPORTANT]
> 語音識別功能僅適用於Chrome和電子播放器。

## 實施語音識別 {#implementing}


若要在AEM Screens專案中實作語音識別，您必須啟用「顯示」的語音識別，並將每個頻道與唯一標籤建立關聯，以觸發頻道轉換。

以下章節說明如何在AEM Screens專案中啟用和使用「語音辨識」功能。

### 設定專案 {#setting-up}

在使用語音識別功能之前，請確定您有專案和頻道，並為專案設定內容。

1. 下列範例展示名為 **VoiceDemo** 的示範專案，以及3種 **Main**、 **ColdDrinks**&#x200B;和 **** HotDrinks，如下圖所示。

   ![影像](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >如要瞭解如何建立頻道或新增內容至頻道，請參閱建立 [和管理頻道](/help/user-guide/managing-channels.md)

1. 導覽至每個頻道並新增內容。 例如，導覽至 **VoiceDemo** —> **Channels** —> **Main** ，然後選取頻道。 按一 **下動作列的** 「編輯」以開啟編輯器，並視需要新增內容（影像／視訊）。 同樣地，您也可將內容 **加入ColdDrinks** 和 **HotDrinks頻道** 。

   頻道現在包含資產（影像），如下圖所示。

   **主要**:

   ![影像](assets/voice-recognition/vr-4.png)

   **ColdDrinks**:

   ![影像](assets/voice-recognition/vr-3.png)

   **熱飲**:

   ![影像](assets/voice-recognition/vr-2.png)

### 設定渠道的標籤 {#setting-tags}

在將內容新增至頻道後，您必須導覽至每個頻道，並新增適當的標籤，以觸發語音辨識。

請依照下列步驟，將標籤新增至您的渠道：

1. 導覽至每個頻道並新增內容。 例如，導覽至 **VoiceDemo** —> **Channels** —> **Main** ，然後選取頻道。

1. 從動 **作列按一下** 「屬性」。

   ![影像](assets/voice-recognition/vr-5.png)

1. 導覽至「 **基本** 」索引標籤，並從「標籤」欄位中選取已有的標籤 **** ，或建立新標籤。

   您可以輸入新的標籤名稱並按鍵，以建立新的標 `return` 簽，如下圖所示：

   ![影像](assets/voice-recognition/vr-6.png)

   或,

   您可以事先從AEM例項建立專案的標籤，並選取這些標籤。 遵循「建立標籤」中說明的步驟後 [](#creating-tags)，您就可從位置選取標籤並將其新增至您的渠道，如下圖所示：

   ![影像](assets/voice-recognition/vr-tag1.png)

1. 完成 **後，按一下「儲存** 並關閉」。

同樣地，將標題為 **hot的標籤** ，新增 **至HotDrinks頻道** 。

#### 建立標籤 {#creating-tags}

請依照下列步驟建立標籤：

1. 導覽至您的AEM例項。
1. 按一下工具—>標 **記**。
   ![影像](assets/voice-recognition/vr-7.png)
1. 按一下 **建立** —>創 **建命名空間**。
   ![影像](assets/voice-recognition/vr-7.png)
1. 輸入專案名稱，例如： **VoiceDemo** ，然後按一下「建立」。
1. 選取 **VoiceDemo專案** ，然後從動作列按 **一下「建立標籤** 」。
1. 按一 **下提交**。


### 為顯示器分配頻道並啟用語音識別 {#channel-assignment}

1. 在「位置」資料 **夾中** ，建立顯示，如下圖所示。

   ![影像](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >若要瞭解如何指派渠道給顯示，請參閱建立 [和管理顯示](/help/user-guide/managing-displays.md)。

1. 將頻道Main **、** ColdDrinks **和** HotDrinks指派給您的LobbyDisplay **(大******&#x200B;堂展示)。

1. 在指派渠道時，請為每個渠道設定下列屬性。

   | **頻道名稱** | **優先順序** | **支援的事件** |
   |---|---|---|
   | 主要 | 2 | 初始載入、空閒螢幕、計時器 |
   | 熱飲 | 1 | 使用者互動 |
   | ColdDrinks | 1 | 使用者互動 |

   >[!NOTE]
   >
   >若要瞭解如何指派渠道給顯示，請參閱建立 [和管理顯示](/help/user-guide/managing-displays.md)。

1. 將頻道指派給顯示器後，請導覽至 **LobbyDisplay** ，然後選取顯示器。 從操 **作欄中** ，選擇屬性。

1. 導覽至「顯 **示** 」索引標籤，並在「內容」下啟用 **「語音** 」 **選項**。

   ![影像](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >必須從顯示器中啟用語音識別功能。

#### 在Chrome Player中檢視內容 {#viewing-content}

完成上述步驟後，您就可以註冊您的chrome裝置並檢視輸出。

>[!NOTE]
>請參閱「 [裝置註冊](device-registration.md) 」以瞭解如何在AEM Screens播放器上註冊裝置。

此範例將展示Chrome Player的輸出。

![新影像](assets/voice-recognition/voice-video.gif)













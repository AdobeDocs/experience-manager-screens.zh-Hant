---
title: AEM Screens語音識別
description: 本頁說明AEM Screens語音識別功能。
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 3%

---


# AEM Screens語音識別{#voice-recognition}

>[!IMPORTANT]
>
>**重要隱私權資訊**
>
>使用語音識別功能時，請遵循您所在地區的所有適用法律與道德准則（包括但不限於向使用者顯示播放器使用語音識別）。 Adobe Inc，不接收、儲存或處理任何語音相關資訊。 AEM Screens播放器使用內建於瀏覽引擎的標準網路語音API。 在幕後，此API會將您的語音波形傳送至Google的伺服器，以便從語音轉換為文字，而且此文字會由播放器與設定的關鍵字相符。
>
>如需詳細資訊，請參閱Web語音API的[Google隱私權白皮書](https://www.google.com/chrome/privacy/whitepaper.html#speech)。


語音識別功能允許由語音交互驅動的AEM Screens頻道中的內容改變。

內容作者可以將顯示設為啟用語音。 這項功能的目的是讓客戶運用語音作為與顯示器互動的方式。 一些類似的使用案例包括在商店中尋找產品建議、在用餐者和餐廳訂購功能表項目。 此功能可提高使用者的協助功能，並可大幅提升客戶體驗。

>[!NOTE]
>播放器硬體必須支援語音輸入，例如麥克風。

## 實施語音識別{#implementing}

>[!IMPORTANT]
> 語音識別功能僅適用於Chrome OS和Windows播放器。

若要在AEM Screens專案中實作語音識別，您必須啟用「顯示」的語音識別，並將每個頻道與唯一標籤建立關聯，以觸發頻道轉換。

下節說明如何在AEM Screens項目中啟用和使用語音識別功能。

## 在全螢幕或分割螢幕頻道切換器中檢視內容{#sequence-channel}

在使用語音識別功能之前，請確定您有專案和頻道，並為專案設定內容。

1. 下列範例展示名為&#x200B;**VoiceDemo**&#x200B;的示範專案，以及3個序列頻道&#x200B;**Main**、**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**，如下圖所示。

   ![影像](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >若要瞭解如何建立頻道或新增內容至頻道，請參閱[建立和管理頻道](/help/user-guide/managing-channels.md)

   或,

   您可以建立三個順序頻道&#x200B;**Main**、**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**，以及另一個1x2 SplitScreen頻道&#x200B;**SplitScreen**，如下圖所示。

   ![影像](assets/voice-recognition/vr-emb-1.png)

1. 導覽至每個頻道並新增內容。 例如，導覽至&#x200B;**VoiceDemo** —> **Channels** —> **Main**&#x200B;並選取頻道。 按一下動作列中的「編輯」****，以開啟編輯器並視需要新增內容（影像／視訊）。 同樣地，將內容新增至&#x200B;**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**&#x200B;頻道。

   頻道現在包含資產（影像），如下圖所示。

   **主要**:

   ![影像](assets/voice-recognition/vr-4.png)

   **ColdDrinks**:

   ![影像](assets/voice-recognition/vr-3.png)

   **熱飲**:

   ![影像](assets/voice-recognition/vr-2.png)

   如果您已將「分割畫面」頻道新增至專案，請導覽至&#x200B;**SplitScreen**，並拖放兩個內嵌的序列，並新增至&#x200B;**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**頻道的路徑，如下圖所示。
   ![影像](assets/voice-recognition/vr-emb-6.png)


### 設定頻道的標籤{#setting-tags}

在將內容新增至頻道後，您必須導覽至每個頻道，並新增適當的標籤，以觸發語音辨識。

請依照下列步驟，將標籤新增至您的渠道：

1. 導覽至每個頻道並新增內容。 例如，導覽至&#x200B;**VoiceDemo** —> **Channels** —> **Main**&#x200B;並選取頻道。

1. 從操作欄按一下&#x200B;**屬性**。

   ![影像](assets/voice-recognition/vr-5.png)

1. 導覽至&#x200B;**Basics**&#x200B;標籤，並從&#x200B;**Tags**&#x200B;欄位中選取現有的標籤，或建立新的標籤。

   您可以輸入新的標籤名稱並點選`return`鍵，以建立新標籤，如下圖所示：

   ![影像](assets/voice-recognition/vr-6.png)

   或,

   您也可以事先從您的專案例AEM項建立標籤，並選取這些標籤。 遵循[建立標籤](#creating-tags)中說明的步驟後，您就可以從位置選取標籤並將它新增至您的頻道，如下圖所示：

   ![影像](assets/voice-recognition/vr-tag1.png)

1. 同樣地，將標題為&#x200B;**hot**&#x200B;的標籤新增至&#x200B;**HotDrinks**&#x200B;頻道。

1. 如果您使用分割畫面頻道，請將標籤（**hot**&#x200B;和&#x200B;**cold**）新增至&#x200B;**SplitScreen**&#x200B;頻道屬性，如下圖所示。

   ![影像](assets/voice-recognition/vr-emb-7.png)

1. 完成後，按一下「保存並關閉」。****


### 建立標籤{#creating-tags}

請依照下列步驟建立標籤：

1. 導覽至您的AEM例項。

1. 按一下工具表徵圖—> **標籤**。
   ![影像](assets/voice-recognition/vr-7.png)

1. 按一下「**建立** —> **建立命名空間**」。
   ![影像](assets/voice-recognition/vr-tag3.png)

1. 輸入專案名稱，例如&#x200B;**VoiceDemo**，然後按一下&#x200B;**Create**。

1. 選擇&#x200B;**VoiceDemo**&#x200B;專案，然後從動作列按一下「建立標籤」。****
   ![影像](assets/voice-recognition/vr-tag4.png)

1. 輸入標籤的名稱，然後按一下&#x200B;**Submit**。
   ![影像](assets/voice-recognition/vr-tag5.png)

現在，您可以在AEM Screens專案中使用這些標籤。

### 為顯示器分配頻道並啟用語音識別{#channel-assignment}

1. 在&#x200B;**Locations**&#x200B;資料夾中建立顯示，如下圖所示。

   ![影像](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >要瞭解如何為顯示器分配通道，請參閱[建立和管理顯示](/help/user-guide/managing-displays.md)。

1. 將渠道&#x200B;**Main**、**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**&#x200B;指派給&#x200B;**LobbyDisplay**。 此外，如果您正在專案中使用&#x200B;**SplitScreen**&#x200B;頻道，請務必將它指派給顯示器。

   >[!NOTE]
   >如果您已建立分割畫面頻道，請將&#x200B;**SplitScreen**&#x200B;頻道指派給您的顯示器。

1. 在指派渠道時，請為每個渠道設定下列屬性。

   | **頻道名稱** | **優先順序** | **支援的事件** |
   |---|---|---|
   | 主要 | 2 | 初始載入、空閒螢幕、計時器 |
   | 熱飲 | 1 | 使用者互動 |
   | ColdDrinks | 1 | 使用者互動 |
   | SplitScreen | 1 | 使用者互動 |

   >[!NOTE]
   >
   >要瞭解如何為顯示器分配通道，請參閱[建立和管理顯示](/help/user-guide/managing-displays.md)。

1. 將頻道指派給顯示器後，請導覽至&#x200B;**LobbyDisplay**&#x200B;並選取顯示器。 從操作欄中選擇&#x200B;**屬性**。

1. 導覽至&#x200B;**Display**&#x200B;標籤，並啟用&#x200B;**Content**&#x200B;下的&#x200B;**Voice enabled**&#x200B;選項。

   ![影像](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >必須從顯示器中啟用語音識別功能。

### 在Chrome Player中檢視內容{#viewing-content}

完成上述步驟後，您就可以註冊您的chrome裝置以檢視輸出。

>[!NOTE]
>請參閱[裝置註冊](device-registration.md)以瞭解如何在AEM Screens播放器上註冊裝置。

**序列頻道的所需輸出**

**Main**&#x200B;頻道正在播放其內容，但當您使用關鍵字&#x200B;**hot**&#x200B;的字詞例如&#x200B;*我想擁有熱飲*&#x200B;時，頻道開始播放&#x200B;**HotDrinks**&#x200B;頻道的內容。

同樣地，如果您使用關鍵字&#x200B;**cold**&#x200B;的字詞，例如&#x200B;*I想要提供cold*，則頻道會開始播放&#x200B;**ColdDrinks**&#x200B;頻道的內容。

**分割畫面色版所需的輸出**

**Main**&#x200B;頻道正在播放其內容，但當您搭配使用關鍵字&#x200B;**hot**&#x200B;和&#x200B;**cold**&#x200B;的字詞時，如&#x200B;*I想看到冷熱飲料的功能表，頻道開始播放&#x200B;**SplitScreen**的內容頻道。*&#x200B;如果您說&#x200B;*返回主菜單*，則它將切換回主通道。






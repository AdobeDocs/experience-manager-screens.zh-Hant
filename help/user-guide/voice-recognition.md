---
title: AEM Screens語音識別
description: 本頁說明AEM Screens中的語音識別功能。
feature: 製作畫面
role: Administrator, Developer
level: Intermediate
exl-id: 6cf0aa9f-7bac-403f-a113-51727c1f5374
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 3%

---

# AEM Screens語音識別{#voice-recognition}

>[!IMPORTANT]
>
>**重要隱私權資訊**
>
>使用語音識別功能時，請遵循您所在地區的所有適用法律與道德准則（包括但不限於向使用者提供播放器使用語音識別的可見通知）。 Adobe Inc.不會接收、儲存或處理任何語音相關資訊。 AEM Screens播放器使用內建於瀏覽引擎中的標準網路語音API。 在幕後，此API會將您的語音波形傳送至Google的伺服器，以從語音轉換為文字，而此文字會由播放器比對所設定的關鍵字。
>
>如需詳細資訊，請參閱網路語音API](https://www.google.com/chrome/privacy/whitepaper.html#speech)上的[Google隱私權白皮書。


語音識別功能允許在由語音交互驅動的AEM Screens通道中更改內容。

內容作者可將顯示設定為啟用語音。 此功能的目的是讓客戶將語音作為與其顯示器互動的方法。 某些類似的使用案例包括在商店中尋找產品建議、在用餐者和餐廳訂購菜單項。 此功能可增加使用者的協助工具，並可大幅增強客戶體驗。

>[!NOTE]
>播放器硬體必須支援語音輸入，如麥克風。

## 實施語音識別 {#implementing}

>[!IMPORTANT]
> 語音識別功能僅適用於Chrome OS和Windows播放器。

若要在您的AEM Screens專案中實作語音辨識，您必須啟用「顯示」的語音辨識，並將每個頻道與一個唯一標籤建立關聯，以觸發頻道轉變。

以下章節說明如何在AEM Screens專案中啟用和使用語音辨識功能。

## 在全螢幕或分屏通道交換機中查看內容{#sequence-channel}

使用語音識別功能之前，請確定您有專案和管道，且已為您的專案設定內容。

1. 下列範例將展示一個名為&#x200B;**VoiceDemo**&#x200B;的示範專案，以及三個序列頻道&#x200B;**Main**、**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**，如下圖所示。

   ![影像](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >若要了解如何建立頻道或將內容新增至頻道，請參閱[建立和管理頻道](/help/user-guide/managing-channels.md)

   或,

   您可以建立三個序列通道&#x200B;**Main**、**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**，以及一個附加的1x2 SplitScreen通道&#x200B;**SplitScreen**，如下圖所示。

   ![影像](assets/voice-recognition/vr-emb-1.png)

1. 導覽至每個頻道並新增內容。 例如，導航到&#x200B;**VoiceDemo** —> **通道** —> **主**&#x200B;並選擇通道。 按一下動作列中的&#x200B;**Edit**&#x200B;以開啟編輯器，並視需要新增內容（影像/影片）。 同樣地，將內容新增至&#x200B;**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**&#x200B;頻道。

   管道現在包含資產（影像），如下圖所示。

   **主要**:

   ![影像](assets/voice-recognition/vr-4.png)

   **冷飲**:

   ![影像](assets/voice-recognition/vr-3.png)

   **熱飲**:

   ![影像](assets/voice-recognition/vr-2.png)

   如果您已將「分割螢幕」管道新增至專案，請導覽至&#x200B;**SplitScreen**&#x200B;並拖放兩個內嵌序列，並新增路徑至&#x200B;**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**管道，如下圖所示。
   ![影像](assets/voice-recognition/vr-emb-6.png)


### 設定通道的標籤{#setting-tags}

將內容新增至頻道後，您必須導覽至每個頻道，並新增適當標籤以觸發語音辨識。

請依照下列步驟，將標籤新增至管道：

1. 導覽至每個頻道並新增內容。 例如，導航到&#x200B;**VoiceDemo** —> **通道** —> **主**&#x200B;並選擇通道。

1. 按一下動作列中的&#x200B;**屬性**。

   ![影像](assets/voice-recognition/vr-5.png)

1. 導覽至&#x200B;**Basics**&#x200B;標籤，並從&#x200B;**Tags**&#x200B;欄位中選取已存在的標籤，或建立新標籤。

   您可以為標籤輸入新名稱並點擊`return`索引鍵，以建立新標籤，如下圖所示：

   ![影像](assets/voice-recognition/vr-6.png)

   或,

   您也可以預先為專案從AEM例項建立標籤，並選取這些標籤。 按照[建立標籤](#creating-tags)中所述的步驟操作後，您就可以從位置選取標籤，並將其新增至通道，如下圖所示：

   ![影像](assets/voice-recognition/vr-tag1.png)

1. 同樣地，將標題為&#x200B;**hot**&#x200B;的標籤新增至&#x200B;**HotDrinks**&#x200B;頻道。

1. 如果您使用「分割螢幕」通道，請將標籤（**hot**&#x200B;和&#x200B;**cold**）同時新增至&#x200B;**SplitScreen**&#x200B;通道屬性，如下圖所示。

   ![影像](assets/voice-recognition/vr-emb-7.png)

1. 完成後，按一下「**儲存並關閉**」。


### 建立標籤{#creating-tags}

請依照下列步驟建立標籤：

1. 導覽至您的AEM例項。

1. 按一下「工具」表徵圖 — > **「標籤**」。
   ![影像](assets/voice-recognition/vr-7.png)

1. 按一下「**建立** —> **建立命名空間**」。
   ![影像](assets/voice-recognition/vr-tag3.png)

1. 輸入項目名稱，例如&#x200B;**VoiceDemo**，然後按一下&#x200B;**Create**。

1. 選擇&#x200B;**VoiceDemo**&#x200B;專案，然後從動作列按一下&#x200B;**建立標籤**。
   ![影像](assets/voice-recognition/vr-tag4.png)

1. 輸入標籤的名稱，然後按一下&#x200B;**Submit**。
   ![影像](assets/voice-recognition/vr-tag5.png)

現在，您可以在AEM Screens專案中使用這些標籤。

### 為顯示器分配通道並啟用語音識別{#channel-assignment}

1. 在&#x200B;**Locations**&#x200B;資料夾中建立顯示，如下圖所示。

   ![影像](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >要了解如何將通道分配給顯示器，請參閱[建立和管理顯示器](/help/user-guide/managing-displays.md)。

1. 將通道&#x200B;**Main**、**ColdDrinks**&#x200B;和&#x200B;**HotDrinks**&#x200B;指派給您的&#x200B;**LobbyDisplay**。 此外，如果您使用專案的&#x200B;**SplitScreen**&#x200B;頻道，請務必將該頻道指派給顯示。

   >[!NOTE]
   >如果已建立分割螢幕通道，請將&#x200B;**SplitScreen**&#x200B;通道分配給顯示器。

1. 在指派管道時，為每個管道設定下列屬性。

   | **頻道名稱** | **優先順序** | **支援的事件** |
   |---|---|---|
   | 主要 | 2 | 初始載入、空閒螢幕、計時器 |
   | 熱飲 | 1 | 使用者互動 |
   | 冷飲 | 3 | 使用者互動 |
   | SplitScreen | 3 | 使用者互動 |

   >[!NOTE]
   >
   >要了解如何將通道分配給顯示器，請參閱[建立和管理顯示器](/help/user-guide/managing-displays.md)。

1. 將通道分配給顯示器後，導航至&#x200B;**LobbyDisplay**&#x200B;並選擇顯示器。 從操作欄中選擇&#x200B;**屬性**。

1. 導覽至&#x200B;**Display**&#x200B;標籤，並在&#x200B;**Content**&#x200B;下啟用&#x200B;**Voice enabled**&#x200B;選項。

   ![影像](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >必須從顯示器啟用語音識別功能。

### 在Chrome播放器{#viewing-content}中檢視內容

完成上述步驟後，您可以註冊Chrome裝置以檢視輸出。

>[!NOTE]
>請參考[裝置註冊](device-registration.md)，了解如何在AEM Screens播放器上註冊裝置。

**序列通道所需的輸出**

**Main**&#x200B;頻道正在播放其內容，但當您使用關鍵字&#x200B;**hot**&#x200B;的字詞（例如&#x200B;*I想要熱飲*）時，頻道開始播放&#x200B;**HotDrinks**&#x200B;頻道的內容。

同樣地，如果使用關鍵字&#x200B;**cold**(例如&#x200B;*I想獲得某種冷*&#x200B;的字，則管道開始播放&#x200B;**ColdDrinks**&#x200B;管道的內容。

**分割螢幕通道所需的輸出**

**Main**&#x200B;頻道正在播放其內容，但是當您將關鍵字&#x200B;**hot**&#x200B;和&#x200B;**cold**&#x200B;等單詞一起使用時，如&#x200B;*I想查看熱飲和冷飲的菜單*，頻道開始播放&#x200B;**SplitScreen**&#x200B;頻道的內容。 若您說&#x200B;*返回主功能表*，則會切換回主通道。

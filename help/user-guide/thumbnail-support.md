---
title: AEM Screens影片的縮圖支援
description: 瞭解如何在AEM Screens中新增影片的縮圖支援。
exl-id: d2d87807-1699-47e3-b241-07c5b7e56f15
source-git-commit: 6b4fc934c31640168528fa3e72cf634773f4f8e6
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 2%

---

# 影片的縮圖支援 {#thumbnail-support-videos}

## 簡介 {#introduction}

內容作者可以定義影片的縮圖，好讓影像可當做預留位置使用。 這能正確地測試內容播放和目標定位，同時由適當的團隊完成實際的視訊。 如果影片播放失敗，也可以使用該影像。

在視訊元件上新增對縮圖影像的支援，可讓客戶在頻道中正確新增包含實際內容的有效元件，並在視訊傳送前執行任何目標定位設定。

>[!NOTE]
>如果在視訊元件上設定了縮圖影像，則當播放器發生視訊播放失敗時就會播放。 此遞補功能可讓您傳遞所需訊息給對象（透過播放內容），而非完全略過。

縮圖支援可讓您：

* 影片尚未準備就緒，或您不想要測試播放器上的大型資產下載時，請準備管道體驗

* 設定後援機制，以防止裝置上發生播放問題。

## 在視訊中使用縮圖 {#using-thumbnails}

請依照下列步驟，在視訊中使用縮圖：

1. 導覽至現有的AEM Screens頻道或建立頻道。

1. 按一下頻道，然後按一下 **編輯** 從動作列移除。

   ![影像](/help/user-guide/assets/thumbnails/thumbnail-1.png)

1. 新增或編輯現有的視訊元件，如下圖所示。

   ![影像](/help/user-guide/assets/thumbnails/thumbnail-2.png)

1. 按一下視訊，然後按一下 *扳手* 圖示。

   ![影像](/help/user-guide/assets/thumbnails/thumbnail-3.png)

1. 此 **視訊** 對話方塊開啟，您可以在其中檢視 **縮圖** 拖放區域。

   ![影像](/help/user-guide/assets/thumbnails/thumbnail-4.png)

1. 將影像從資產選擇器拖放至 **縮圖** 放置區域並按一下 **完成**.

   ![影像](/help/user-guide/assets/thumbnails/thumbnail-5.png)

1. 按一下 **預覽**.

1. 若已在元件上設定視訊，則會播放視訊。 如果沒有，且已設定縮圖，則會播放縮圖。 否則，元件會視為未設定並略過。

## 在視訊中使用縮圖時的支援使用案例 {#understand-use-case}

影片中的縮圖支援下列使用案例：

* 未跳過任何設定的視訊元件。

* 只有縮圖集的視訊元件會播放縮圖。

* 同時具有視訊（如果視訊具有正確的轉譯）和縮圖集的視訊元件會播放視訊。

* 如果發生播放錯誤，包含視訊集的視訊元件會播放縮圖，如果未設定縮圖，則會跳至下一個專案。

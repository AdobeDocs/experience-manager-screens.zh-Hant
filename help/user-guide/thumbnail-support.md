---
title: AEM Screens中影片的縮圖支援
description: 本頁面說明如何在Screens中新增影片的縮圖支援。
exl-id: d2d87807-1699-47e3-b241-07c5b7e56f15
source-git-commit: ec58cd9171e359b451eaad7015d42b41ef1bff3f
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 1%

---

# 影片的縮圖支援 {#thumbnail-support-videos}

## 簡介 {#introduction}

內容作者可以定義視訊的縮圖，以便影像可作為預留位置，並在適當團隊完成實際視訊時，正確測試內容播放和鎖定目標。 當視訊播放失敗時，也可以使用影像。

新增對視訊元件上縮圖影像的支援，讓客戶能在頻道中正確新增有效的元件（含實際內容），並在實際傳送視訊前執行任何鎖定目標設定。

>[!NOTE]
>如果在視訊元件上設定縮圖影像，則會在播放器上視訊播放失敗時播放。 這可讓您將所需的訊息傳送給對象（透過播放內容），而非完全略過訊息。

縮圖支援可讓您：

* 當影片尚未準備好，或您不一定想要在播放器上測試大型資產下載時，準備管道體驗

* 如果裝置上發生播放問題，請設定後援機制。

## 在影片中使用縮圖 {#using-thumbnails}

請依照下列步驟，在影片中使用縮圖：

1. 導覽至現有的Screens頻道或建立新頻道。

1. 選取通道，然後按一下動作列中的&#x200B;**Edit**&#x200B;以開啟編輯器。

   ![影像](/help/user-guide/assets/thumbnails/thumbnail-1.png)

1. 添加或編輯現有視頻元件，如下圖所示。

   ![影像](/help/user-guide/assets/thumbnails/thumbnail-2.png)

1. 選取影片，然後按一下&#x200B;*扳手*&#x200B;圖示以開啟影片屬性。

   ![影像](/help/user-guide/assets/thumbnails/thumbnail-3.png)

1. 將開啟&#x200B;**Video**&#x200B;對話框，您將在其中查看&#x200B;**縮圖**&#x200B;拖放區域。

   ![影像](/help/user-guide/assets/thumbnails/thumbnail-4.png)

1. 將影像從資產選擇器拖放至&#x200B;**縮圖**&#x200B;拖放區域，然後按一下&#x200B;**完成**。

   ![影像](/help/user-guide/assets/thumbnails/thumbnail-5.png)

1. 按一下&#x200B;**預覽**。

1. 如果元件上設定了視訊，則視訊會播放。 如果沒有，且已設定縮圖，則會播放縮圖。 否則，系統會將元件視為未設定，且會略過。

## 在影片中使用縮圖時支援的使用案例 {#understand-use-case}

影片中的縮圖支援下列使用案例：

* 系統會略過未設定任何內容的視訊元件。

* 只設定縮圖的視訊元件會播放縮圖。

* 同時設定視訊（如果視訊有正確的轉譯）和縮圖的視訊元件會播放視訊。

* 如果發生播放錯誤，設定了視訊的視訊元件會播放縮圖，如果未設定縮圖，則只會跳至下一個項目。

---
title: Kickstart指南
seo-title: Kickstart指南
description: 請依照本頁建立示範AEM Screens專案。 它可協助您建立數位招牌體驗，從安裝和設定新專案開始，到在AEM Screens播放器中檢視您的內容。
translation-type: tm+mt
source-git-commit: 78ddd2b45f39d69b66f740910327eef475bcdcac
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 1%

---


# Kickstart指南 {#kickstart-guide}

本節是AEM Screens的啟動，並示範如何設定和執行AEM Screens專案。 它會逐步引導您設定基本的數位標牌體驗，並將資產和／或視訊等內容新增至每個頻道，並進一步將內容發佈至AEM Screens播放器。

>[!NOTE]
>開始處理專案詳細資訊之前，請確定您已安裝最新的功能套件。 您可以使用Adobe ID從「軟體散發入口網站」下載AEM Screens 6.5.5 [版本的最新功能套件](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 。

## 在5分鐘內建立數位標牌體驗 {#creating-a-digital-signage-experience-in-minutes}

請依照下列步驟建立AEM Screens的範例專案，並進一步將內容發佈至Screens播放器。

>[!NOTE]
>下列教學課程將展示在Chrome OS播放器中播放您頻道的內容。

>[!IMPORTANT]
>**OSGi配置設定**
>您必須啟用空的反向連結，以允許裝置將資料張貼至伺服器。 例如，如果停用空的反向連結屬性，裝置就無法將螢幕擷取張貼回去。 目前，部分功能僅在OSGi設定中啟用Apache Sling Referrer Filter Allow Empty時才可用。 控制面板可能會顯示警告，指出安全性設定可能會使部分功能無法運作。
>請依照下列步驟來啟用 ***Apache Sling Referrer Filter Allow Empty***:


## 允許空的反向連結請求 {#allow-empty-referrer-requests}

1. 透過 **AEM例項** —> hammer圖示—> **Operations** —> **Web Console導覽至Adobe Experience Manager Web Console Configuration**。

   ![影像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web Console設定隨即開啟** 。 搜尋sling referrer。

   若要搜尋sling referrer屬性，請按 **Command+F** for **Mac** , **Control+F** for **** Windows。

1. 勾選「 **允許空白** 」選項，如下圖所示。

   ![影像](assets/config/empty-ref2.png)

1. 按一 **下「儲存** 」以啟用Apache Sling Referrer Filter Allow Empty。


## 教學課程 {#tutorial}

### Creating an AEM Screens Project {#creating-project}

第一個步驟是建立新的AEM畫面專案。

1. 導覽至您的Adobe Experience Manager(AEM)例項，然後按一下「畫 **面」**。 或者，您也可以直接從導覽 `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`。

1. 按一 **下「建立畫面專案** 」以建立新的畫面專案。 將標題輸入為 **DemoScreens** ，然後按一 **下Save**。

   ![影像](assets/kickstart/demo-1.png)

   >[!NOTE]
   >建立專案後，就會回到「畫面專案」首頁。 您現在可以選取專案。 在項目中，有5個不同的資料夾，名為 **「應用程式」、「渠道**」、「設 **備**」、「位置」 ************&#x200B;和「計畫」。


### 建立渠道 {#creating-channel}

一旦您的專案就位後，您就需要建立新的管道來管理內容。

請依照下列步驟，為您的專案建立新的管道：

1. 建立專案後，請選取 **DemoScreens** 專案，然後選取 **Channels資料夾**，如下圖所示。 從動 **作列按一下** 「+建立」。

   ![影像](assets/kickstart/demo-2.png)

1. 從嚮導中 **選擇「序列渠道** 」，然後按一下「 **下一步」**。
   ![影像](assets/kickstart/demo-3.png)

1. 將標題輸 **入為** TestChannel *，然後按一* 下Create ****。

   ![影像](assets/kickstart/demo-4.png)

TestChannel *會建立* ，並新增至您的頻道資料夾，如下圖所示。

![影像](assets/kickstart/demo-5.png)

### 新增內容至頻道 {#adding-content}

在您的頻道就位後，您需要將內容新增至頻道，讓螢幕播放器顯示。

請依照下列步驟，將內容新增至專案中&#x200B;*的頻道*(TestChannel):

1. 導覽至您建 **立的DemoProject** ，然後選取「 **Channels** 」檔案夾。

1. 從動 **作列按一下** 「編輯」(Edit)（請參閱下圖）。 TestChannel的編輯 **器隨即開** 啟。

   ![影像](assets/kickstart/demo-6.png)

1. 按一下切換動作列左側側面板的圖示，以開啟資產和元件。

1. 拖放您要新增至渠道的元件。

   ![影像](assets/kickstart/demo-7.png)

### 建立位置 {#creating-location}

當您的渠道到位後，您需要建立位置。

>[!NOTE]
>***位置*** ，將您的各種數位標牌體驗加以區隔，並根據不同螢幕的位置，包含顯示器的組態。

請依照下列步驟，為您的專案建立新位置：

1. 導覽至您建 **立的DemoProject** ，並選取「位置 **」檔案夾** 。

1. 從動 **作列按一下** 「+建立」。

1. 從向 **導中選擇** 「位置」，然後按一下「 **下一步」**。

1. 輸入您 **所在位置的** 「名稱」(輸入標題為 *TestLocation*)，然後按一下「 **建立**」。

TestLocation **會建立** ，並新增至您的 **Locations資料** 夾。


### 建立位置顯示 {#creating-display}

在建立位置後，您需要為位置建立新的顯示。

>[!NOTE]
>***顯示*** ，代表在一或多個螢幕上執行的數位體驗。

1. 導覽至 **TestLocation** ，然後選取它。

1. 從動 **作列按一下** 「建立」。

1. 從「創 **建** 」嚮導中選擇「顯 **示」** ，然後按一下「 **下一步**」。

1. 將標題輸 **入為** LobbyDisplay **，然後單** 擊Create ****。

現在會將名為 **TestDisplay** 的新顯示新增至您的 **TestLocation**，如下圖所示。

### 指派渠道 {#assigning-channel}

專案設定完成後，您必須將頻道指派給顯示器，才能檢視內容。

1. 導覽至所需的顯示，例如 **DemoScreens** —> **Locations** —> **TestLocation** —> **LobbyDisplayDisplay**。

1. 從動作列點選/ **按一下** 「指派渠道」。

   或,

   從動作列點選/ **按一下** 「儀表板」，然後從「已指派的頻道與排程」面板按一 **下+「指派頻道」****** 。

1. 「渠 **道分配** 」對話框開啟。

1. 從「設 **定** 」選項中，您可以 **按路徑選擇渠道** , **或按名稱進入Channel Name**、Channel Role、 **************** ChannelPriorityEvents、Ching Repority Adjusted Chiraction Alignment。 此外，您也可以從此對話方塊啟用吸引工具提示。


   >[!NOTE]
   >請參閱 [渠道屬性](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) ，以進一步瞭解渠道指派屬性。

1. 從「計 **划** 」選項中，選 **擇「激活窗口** 」和「 **定期計畫**」。

1. 設定好 **偏好設定後** ，按一下「儲存」。

### 註冊設備 {#registering-device}

您必須使用AEM儀表板註冊裝置。

### 在Chrome Player中檢視內容 {#viewing-content-output}

此範例將展示Chrome Player的輸出。 將頻道指派給顯示器後，您必須將裝置註冊到播放器。




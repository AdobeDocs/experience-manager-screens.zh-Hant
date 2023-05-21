---
title: Kickstart指南
seo-title: Kickstart Guide
description: 按照本頁建立演示AEM Screens項目。 它幫助您建立數字標牌體驗，從安裝和設定新項目開始，到在AEM Screens播放器中查看您的內容。
feature: Overview, Digital Signage
role: User
level: Beginner
exl-id: 9b7c7f50-2846-4727-a0ec-0220b4cd52c4
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 2%

---

# Kickstart指南 {#kickstart-guide}

AEM Screens的啟動演示了如何設定和運行一個AEM Screens項目。 它指導您設定基本的數字標牌體驗，將資產和/或視頻等內容添加到每個渠道，並進一步向AEM Screens播放器發佈內容。

>[!NOTE]
>在開始處理項目詳細資訊之前，請確保已安裝最新的AEM Screens功能包。 可以從 [軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 用你的Adobe ID。

## 必備條件 {#prerequisites}

按照以下步驟為AEM Screens建立示例項目，並進一步將內容發佈到Screens播放器。

>[!NOTE]
>以下教程將在Chrome OS播放器中播放您的頻道內容。

>[!IMPORTANT]
>**OSGi配置設定**
>必須啟用空引用器，才能允許設備將資料發佈到伺服器。 例如，如果禁用了空引用器屬性，則設備無法將螢幕截圖發回。 目前，只有在OSGi配置中啟用了Apache Sling引用程式篩選器允許空時，這些功能中的某些功能才可用。 儀表板可能顯示警告，安全設定可能會阻止某些功能正常工作。
>按照以下步驟啟用 ***Apache Sling引用篩選器允許空***:


## 允許空引用者請求 {#allow-empty-referrer-requests}

1. 導航到 **Adobe Experience ManagerWeb控制台配置** 通AEM過實例 — >錘表徵圖 —  **操作** —> **Web控制台**。

   ![影像](assets/config/empty-ref1.png)

1. **Adobe Experience ManagerWeb控制台配置** 的上界。 搜索Sling引用者。

   要搜索吊具引用屬性，請按 **命令+F** 為 **Mac** 和 **控制項+F** 為 **窗口**。

1. 檢查 **允許空** 的下界。

   ![影像](assets/config/empty-ref2.png)

1. 按一下 **保存** 啟用Apache Sling引用過濾器允許空。

## 在5分鐘內建立數字標牌體驗 {#creating-a-digital-signage-experience-in-minutes}

### 建立AEM Screens項目 {#creating-project}

第一步是建立一個AEM Screens項目。

1. 導航到您的Adobe Experience Manager(AEM)實例，然後按一下 **螢幕**。 或者，可以直接從 `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`。

1. 按一下 **建立螢幕項目** 建立新螢幕項目。 輸入標題為 **演示螢幕** 按一下 **保存**。

   ![影像](assets/kickstart/demo-1.png)

   >[!NOTE]
   >建立項目後，它將返回「螢幕項目」首頁。 您現在可以選擇項目。 在項目中，有五個不同的資料夾 **應用程式**。 **頻道**。 **設備**。 **位置**, **計畫**。

### 建立通道 {#creating-channel}

建立AEM Screens項目後，您需要建立一個新渠道來管理內容。

按照以下步驟為項目建立新渠道：

1. 建立項目後，選擇 **演示螢幕** 項目，然後選擇 **頻道** 資料夾，如下圖所示。 按一下 **+建立** 按鈕。

   ![影像](assets/kickstart/demo-2.png)

1. 選擇 **序列通道** ，然後按一下 **下一個**。
   ![影像](assets/kickstart/demo-3.png)

1. 輸入 **標題** 如 **測試通道** 按一下 **建立**。

   ![影像](assets/kickstart/demo-4.png)

   的 **測試通道** 現在已添加到您的通道資料夾中，如下圖所示。

   ![影像](assets/kickstart/demo-5.png)

### 將內容添加到渠道 {#adding-content}

在您的頻道就位後，您需要將內容添加到您的頻道中，AEM Screens播放器將顯示這些內容。

按照以下步驟將內容添加到頻道(**測試通道**)中：

1. 導航到 **演示項目** 建立並選擇 **測試通道** 從 **頻道** 的子菜單。

1. 按一下 **編輯** 按鈕（請參見下圖）。 編輯 **測試通道** 的上界。

   ![影像](assets/kickstart/demo-6.png)

1. 按一下切換操作欄左側側面板的表徵圖以開啟資產和元件。

1. 拖放要添加到通道的元件。

   ![影像](assets/kickstart/demo-7.png)

### 建立位置 {#creating-location}

一旦您的渠道就位，您需要建立一個位置。

>[!NOTE]
>***位置*** 將您的各種數字標牌體驗劃分為不同的類別，並根據不同螢幕的位置包含顯示器的配置。

按照以下步驟為項目建立新位置：

1. 導航到 **演示項目** 建立並選擇 **位置** 的子菜單。

1. 按一下 **+建立** 按鈕。

1. 選擇 **位置** ，然後按一下 **下一個**。

1. 輸入 **名稱** 為您的位置(輸入標題為 **測試位置**) **建立**。

的 **測試位置** 建立並添加到 **位置** 的子菜單。


### 為位置建立顯示 {#creating-display}

建立位置後，需要為位置建立新顯示。

>[!NOTE]
>***顯示*** 表示在一個或多個螢幕上運行的數字型驗。

1. 導航到 **測試位置** 選擇它。

1. 按一下 **建立** 按鈕。

   ![影像](assets/kickstart/demo-disp1.png)

1. 選擇 **顯示** 從 **建立** 嚮導 **下一個**。

   ![影像](assets/kickstart/demo-disp2.png)

1. 輸入 **標題** 如 **大廳顯示** 按一下 **建立**。

   ![影像](assets/kickstart/demo-disp3.png)

   標題為 **測試顯示** 現在已添加到您的位置 **測試位置**，如下圖所示。

   ![影像](assets/kickstart/demo-disp4.png)

### 分配通道 {#assigning-channel}

項目設定完成後，必須將頻道分配給顯示器才能查看內容。

1. 導航至所需顯示 **演示螢幕** —> **位置** —> **測試位置** —> **大廳顯示**。

1. 點擊/按一下 **分配通道** 按鈕。

   ![影像](assets/kickstart/demo-assign1.png)

   或,

   點擊/按一下 **儀表板** 按一下 **+分配通道** 從 **分配的渠道和計畫** 的子菜單。

   ![影像](assets/kickstart/demo-assign2.png)

1. 的 **渠道分配** 對話框。

1. 從 **設定** 選項 **按路徑**  和 **支援的事件** 如 **初始載入** 和 **空閒螢幕**。

   >[!NOTE]
   >
   >的 **渠道角色**。 **優先順序**, **中斷方法** 全部填充。 請參閱 [通道屬性](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) 的子菜單。

   ![影像](assets/kickstart/demo-assign3.png)

   此外，您還可以 **激活窗口** 和 **定期計畫**。

   >[!NOTE]
   >的 *定期計畫* 允許您為渠道設定循環計畫。 您為渠道設定了多個重複計畫。
   >請參閱 [定期計畫](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule) 的子菜單。

1. 按一下 **保存** 配置首選項後。

### 註冊設備並將設備分配給顯示器 {#registering-device}

您需要使用儀表板註冊設AEM備。

>[!IMPORTANT]
>Chrome OS播放器可以在開發模式下作為Chrome瀏覽器插件安裝，而無需實際的Chrome播放器設備。 要安裝，請執行以下步驟：
>
>1. 按一下 [這裡](https://download.macromedia.com/screens/) 下載最新的Chrome播放器。
>1. 解壓縮並將其保存到磁碟上。
>1. 開啟Chrome瀏覽器並選擇 **擴展** 或直接導航到 ***chrome://extensions***。
>1. 開啟 **開發人員模式** 右上角。
>1. 按一下 **載入已解壓縮** 從左上角裝載已解壓的Chrome播放器。
>1. 檢查 **AEM Screens克羅姆球員** 插件（如果擴展清單中可用）。
>1. 開啟新頁籤，然後按一下 **應用** 表徵圖，或直接導航到 ***chrome://apps***。
>1. 按一下 **AEM Screens** 啟動Chrome Player的插件。 預設情況下，播放器以全屏模式啟動。 按 **esc** 退出全屏模式。


開啟Chrome OS播放器後，請按照以下步驟註冊Chrome設備。

1. 導航到 **設備** 實例中的項目文AEM件夾。

1. 點擊/按一下 **設備管理器** 按鈕。

   ![影像](assets/kickstart/demo-register1.png)

1. 點擊/按一下 **設備註冊** 右上角。

1. 選擇所需設備並點擊/按一下 **寄存器設備**。

   ![影像](assets/kickstart/demo-register2.png)

1. 等待設備發送其註冊代碼並同時檢查 **註冊代碼** 從Chrome設備中。
   ![影像](assets/kickstart/demo-register3.png)

1. 如果 **註冊代碼** 在兩台電腦上都相同，點擊/按一下 **驗證** 的上AEM界。

1. 將所需名稱設定為 **ChromeDeviceforDemo** ，然後按一下 **註冊**。

   ![影像](assets/kickstart/demo-register4.png)

1. 按一下 **分配顯示** 從 **設備註冊成功** 對話框。

   ![影像](assets/kickstart/demo-register5.png)

1. 選擇顯示路徑為 **演示螢幕** —> **位置** —> **測試位置** —> **大廳顯示** 按一下 **分配**。

   ![影像](assets/kickstart/demo-device6.png)

1. 成功分配設備後，您將看到以下確認資訊。

   ![影像](assets/kickstart/demo-register8.png)

1. 點擊/按一下 **完成** 完成註冊過程。 您應該能夠從顯示面板查看註冊的設備。

   ![影像](assets/kickstart/demo-register9.png)

### 在Chrome Player中查看內容 {#viewing-content-output}

您頻道中的所有資產現在都在您的Chrome OS播放器上播放。

祝賀您現在在AEM Screens頻道播放內容！

![影像](assets/kickstart/demo-video-screens.gif)

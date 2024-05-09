---
title: 實作Cloud Player
description: 瞭解Cloud Player的實作。
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 6720e20f5254e869bde814bd167730e426d0f8fe
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 0%

---

# 實作Cloud Player {#implementing-cloud-player}

AEM Screens傳統上提供各種平台專屬的原生播放器應用程式，包括ChromeOS、Windows™Android和 `Tizen`. 然而，為因應使用者不斷變化的需求，Adobe推出了創新解決方案 — AEM Screens Cloud Player。

Cloud Player與Adobe先前的原生應用程式有很大差異。 這是漸進式網頁應用程式(PWA)，由伺服器託管。 這種變革性的方法讓客戶擁有可在網頁瀏覽器中直接執行的獨立平台播放器。

存取Cloud Player就像造訪 `https://player.adobescreens.com`. 無論使用何種平台，使用者都可將其安裝在裝置上，並享受順暢的數位看板體驗。 Cloud Player的相容性取決於是否具備支援PWA的現代化瀏覽器，確保各種裝置間的一致效能。 向自動提供修正和功能的播放器說再見吧，打招呼吧！確保您隨時都能擁有最新功能。 這次轉換至以PWA為基礎的Cloud Player，標誌著Adobe數位招牌服務取得令人振奮的演化，使其比以往更容易存取、用途更豐富且更方便使用。

本節說明如何實作Cloud Player。

>[!NOTE]
>
>Cloud Player的相容性需要具備PWA支援的現代化瀏覽器，以確保跨不同裝置的一致效能。

## 安裝Cloud Player {#installing-cloud-player}

Cloud Player的安裝可能因平台而異。 一般而言，任何具有現代化瀏覽器的平台，都可以依照以下步驟執行雲端播放器應用程式：

1. 開啟瀏覽器並輸入 [雲端播放器URL](https://player.adobescreens.com/content/dam/universal-player/firmware.html) 位址列中的。
1. 瀏覽器會檢查Cloud Player是否可安裝，然後在位址列中顯示安裝圖示。

   ![影像](/help/user-guide/assets/cloud-player-install.png)

1. 在確認對話方塊中，按一下安裝圖示和安裝按鈕。 Cloud Player是以獨立應用程式的形式安裝在您的裝置上，並可使用圖示啟動。

>[!NOTE]
>
>### Cloud Player安裝選項 {#cloud-player-install-option}
>
1. PWA的安裝選項也稱為「新增至主畫面」或A2HS功能。 支援從Web安裝PWA的方式因瀏覽器和平台而異。
1. 每個瀏覽器都有不同的條件可檢查PWA應用程式是否可安裝。 一般而言，瀏覽器可以檢查（更多詳細資訊請參閱此處）：
>
* 如果應用程式具有資訊清單json檔案，且具備在平台上安裝應用程式所需的最低金鑰，即名稱、圖示、start_url、顯示
* 如果應用程式的Service Worker檔案具有擷取事件監聽器
* 應用程式必須透過https提供
>
1. 安裝選項可能會顯示在不同瀏覽器和裝置型別的不同位置。 有些瀏覽器可能會隱藏選項功能表列中的安裝圖示。

## 大量布建雲端播放器 {#bulk-provisioning}

若要在多部裝置上大量布建Cloud Player：

1. 選擇支援在資訊站模式下執行具有URL的瀏覽器的MDM解決方案。
1. 您可以依照以下步驟將相同的設定套用至所有裝置：

   1. 將config.json託管在伺服器上，使其可供存取，例如： `https://<config_server_host>/config.json`
   1. 若要安裝雲端播放器並套用託管設定，請使用雲端播放器URL，例如： `https://player.adobescreens.com?playerConfigAddress=https://<config_server_host>`
   1. Cloud Player應用程式會在的根目錄中尋找config.json &lt;config_server_host>，然後解析config.json以取得自訂設定並套用這些設定。
   1. 這些設定會套用到播放器的每次重新載入。

## 在Chrome作業系統上大量布建 {#bulk-provisioning-chrome}

深入瞭解Chrome作業系統上的大量布建。 另請參閱 [在Chrome作業系統上安裝Cloud Player](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/chromeos-install-cloud-player). &lt;!-- `https://www.adobe.com/go/aem_screens_cloud_player_en` >

## AEM執行個體上所需的設定 {#bulk-provisioning-config-aem}

根據AEM執行個體的型別，按一下以下其中一項指南，以啟用AEM和Cloud Player下的CORS：

* [AEM On-Premises/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams) <!-- `https://www.adobe.com/go/aem_screens_cors_ams_en` -->

* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs) <!-- `https://www.adobe.com/go/aem_screens_cors_aemaacs_en` -->


>[!NOTE]
>
## Google淘汰Chrome應用程式
>
1. Chrome作業系統硬體上的Chrome應用程式：
>
Google已主動淘汰Chrome應用程式而改用PWA應用程式，並計畫在2025年1月前進行移轉。 因此，Chrome作業系統上的AEM Screens Player應用程式將無法根據共用時間軸正常運作。 Adobe敦促目前生產中使用Chrome Player的使用者，為轉換至Screens Cloud Player做好規劃。
>
1. Mac、Windows和Linux®上的Chrome擴充功能播放器：
>
由於Google的淘汰程式，從Google Chrome 114版開始，不再支援Screens Chrome擴充功能播放器。 Adobe建議您轉換至其Screens Cloud Player，以符合所有開發和測試需求。

## 外部內容擷取的離線支援 {#offline-support}

在各種使用案例中，管道可能會要求從本身無法提供離線支援的外部來源(例如，天氣小工具或Commerce整合式單頁應用程式)擷取內容。 為了針對這些特定使用案例啟用離線功能，Cloud Player提供對自訂標題的支援。

Cloud Player採用「網路優先」快取策略，這表示它會嘗試從網路擷取內容（然後以最新內容更新快取），如果有的話，會退回快取內容。 若要針對這類內容擷取實作離線支援，要求中必須包含自訂標頭。 接著，具有自訂標頭的請求會在播放器上快取，方便離線存取內容，同時維持「網路優先」快取策略。

```
// Sample fetch request with the 'X-Cache-Strategy' header
fetch(externalUrl, {
  headers: {
    'X-Cache-Strategy': 'external-cache'
  }
})
  .then(response => {
    // Handle the response, which may be from the network or cache.
    // Your logic here.
  })
  .catch(error => {
    // Handle any errors that may occur during the fetch operation.
    // Your error handling logic here.
  }); 
```

## 意見回饋

Adobe重視您的意見反應。 透過此分享您的想法 [表單](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4TFE0b_GjstOj6I1uGs9vLpURVdWWklQQTZZRTFVNEhRVlBWWldMWlJXOC4u).

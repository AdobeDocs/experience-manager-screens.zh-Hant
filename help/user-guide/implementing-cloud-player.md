---
title: 實作Cloud Player
seo-title: Implementing Cloud Player
description: 請依照本頁所述來瞭解Cloud Player的實作。
seo-description: Follow  this page to learn about the implementation of the Cloud Player.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 8d1b955e54650daf3a09b5f1c16f92f2e1143f2c
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# 實作Cloud Player  {#implementing-cloud-player}

本節說明如何實作Cloud Player。

>[!NOTE]
>
>Cloud Player的相容性需要具備PWA支援的現代化瀏覽器，以確保跨不同裝置的一致效能。

## 安裝Cloud Player {#installing-cloud-player}

Cloud Player的安裝可能因平台而異。 一般而言，任何具有現代化瀏覽器的平台，都可以依照以下步驟執行雲端播放器應用程式：

1. 開啟瀏覽器並輸入 [雲端播放器URL](https://player.adobescreens.com) 位址列中的。
1. 瀏覽器會檢查雲端播放器是否可安裝，然後在位址列中顯示安裝圖示。

![影像](/help/user-guide/assets/cloud-player-install.png)

1. 在確認對話方塊上，按一下安裝圖示和安裝按鈕。 Cloud Player將以獨立應用程式的形式安裝在您的裝置上，並可使用圖示啟動。

### Cloud Player安裝選項 {#cloud-player-install-option}

1. PWA的安裝選項也稱為「新增至主畫面」或A2HS功能。  支援從網頁安裝PWA，因瀏覽器和平台而異。
1. 每個瀏覽器都有不同的條件可檢查PWA應用程式是否可安裝。 通常瀏覽器會檢查這些專案（如需詳細資訊，請參閱此處）：
   * 如果應用程式具有資訊清單json檔案，且具備在平台上安裝應用程式所需的最低金鑰，例如，名稱、圖示、start_url、顯示
   * 如果應用程式的Service Worker檔案具有擷取事件監聽器。
   * 應用程式必須透過https提供。
1. 安裝選項可能會顯示在不同瀏覽器和裝置型別的不同位置。 有些瀏覽器可能會隱藏選項功能表列中的安裝圖示。

## 大量布建雲端播放器 {#bulk-provisioning}

若要在多部裝置上大量布建Cloud Player：

1. 選擇支援在資訊站模式下執行具有URL的瀏覽器的MDM解決方案。
1. 您可以依照以下步驟將相同的設定套用至所有裝置：
   1. 將config.json託管在伺服器上使其可供存取，例如： https://&lt;config_server_host>/config.json
   1. 若要安裝雲端播放器並套用託管設定，請使用雲端播放器URL，例如：https://player.adobescreens.com?playerConfigAddress=https://&lt;config_server_host>
   1. Cloud Player應用程式會在的根目錄中尋找config.json &lt;config_server_host>，剖析config.json以取得自訂設定並套用這些設定。
   1. 這些設定將套用到播放器的每次重新載入。

## 在Chrome作業系統上大量布建 {#bulk-provisioning-chrome}

若要進一步瞭解Chrome作業系統上的大量布建，請參閱： [在Chrome作業系統上安裝Cloud Player](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player).

## AEM執行個體上所需的設定 {#bulk-provisioning-config-aem}

根據AEM執行個體的型別，選取下列其中一項指南，以啟用AEM和雲端上的CORS播放器：
* [AEM On-Premises/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams)
* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs)

## 外部內容擷取的離線支援 {#offline-support}

在各種使用案例中，管道可能要求從本身無法提供離線支援的外部來源（例如，天氣小工具或商務整合式單頁應用程式）擷取內容。 為了針對這些特定使用案例啟用離線功能，Cloud Player提供對自訂標題的支援。
Cloud Player採用「網路優先」快取策略，這表示它會嘗試從網路擷取內容（然後使用最新內容更新快取），如果有的話，會退回快取內容。 若要針對這類內容擷取實作離線支援，要求中必須包含自訂標頭。 隨後，具有自訂標頭的請求將在播放器上快取，以便在保持網路優先快取策略的同時便於離線存取內容。

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

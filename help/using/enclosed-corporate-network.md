---
title: 封閉的公司網路
description: 封閉的公司網路
exl-id: b8c52e72-86da-4089-ba02-0c643862419f
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---

# 封閉的公司網路（有線/無線） {#enclosed-corporate-networks}

所封閉的企業網路設定適用於規模較小、規模較大和企業性的企業。 理論上可能更複雜，邏輯設定如下圖所示。

![](/help/using/assets/enclosed-network-1.png)


## 將AEM Screens播放器連接到直接Internet訪問 {#connecting-aem-screens-players}

按照以下步驟確保此配置中的螢幕播放AEM器正確連接：

1. 確保每個螢幕播放AEM器都連接到路由器網路。
1. 通過在系統瀏覽器中調用URLtestInternet連接。

   >[!NOTE]
   >如果收到錯誤，請檢查網路設定。對於正確的網路連接，基本上有兩個選項：
   >* DHCP
   >* 手動IP配置


1. 確保「Network Adapter Setting（網路適配器設定）」與「Router Settings（路由器設定）」匹配，並檢查網路中是否未達到最大可用IP地址數。

1. 檢查路由器是否正確連接到ISP廣域網（Internet鏈路）。 也可以使用標準路由器上的信號LED來識別這一點。
1. 如果URL調用成功，則可以繼續安裝AEM Screens並註冊。 啟動AEM Screens。

   >[!NOTE]
   >**故障排除提示**
   >如果AEM Screens連接不正確，並且未顯示預期內容：
   >
   >1. 如果對Internet路由器防火牆有任何限制，請簽入 `TCP/IP Port 80/443`。
   >1. 確保允許所有所需的埠。


## 設定封閉的公司網路 {#requirements-enclosed-networks}

封閉的公司網路設定可以在邏輯上分成兩個塊：

* 廣域網(WAN)
* 內部區域網路(LAN)。

### 廣域網 {#wan-connection}

除了網路可達性外，網際網路連接的效能還必須提供足夠的頻寬，以便順利地運行AEM Screens內容更新。
*足夠的頻寬* 取決於已連接螢幕的AEM數量以及網路內其他消費者的使用情況，如智慧電話、平板電腦、收銀機、電腦或來賓Wi-Fi網路。

>[!NOTE]
>
>所有設備都可同時訪問Internet連接，當向網路添加更多用戶或電腦時，頻寬會線性下降。

### 區域網路 {#lan-connection}

區域網路(LAN)的效能除了網路可達性外，還必須提供足夠的頻寬，以便順利地運行AEM Screens內容更新。

企業組織內的LAN網路通常至少為1000 MBit/秒，因此有足夠的頻寬將許多效能良好的設備連接到系統。 在使用其他活動網路元件時，必須將所有元件都與網路頻寬要求相匹配。

例如，網路元件應至少與100 Mbps標準匹配，並與Internet訪問/路由器規範提供的頻寬匹配。

### 其他公司網路詳情 {#other-networks}

公司網路具有多個連接的設備，被分成不同的子網路，並具有冗餘或多路復用的網際網路連接，以為數千個併發訪問提供足夠的效能。
此模式被簡化，並適用於客戶機可用的環境。

如果設想使用Wi-Fi解決方案將螢幕連接到Internet Link，建議使用現代Wi-Fi標準，如 `IEEE 802.11g` 最起碼。 此標準支援高達54 Mbps的連接。 任意 *新* 標準如 `802.11h-n` 質量更好。 如果需要Wi-Fi中繼器，我們強烈建議使用Mesh Wi-Fi接入點技術，如GoogleNest Mesh Wi-Fi或類似技術。
其他Wi-Fi重複技術最終導致整個網路的頻寬大量丟失。

## 下載媒體和資產 {#download}

AEM Screens為數字標牌用戶提供了巨大優勢。 它下載並本地保存所有必要的媒體檔案，如影像和視頻。 當在特定顯示器上顯示新內容時，會發生主要網路流量。

例如，對於正常操作，定義的在一天中頻繁更新的播放清單在所有檔案都保存到播放器上後，提供接近網路獨立操作。

對於與感測器或觸發器以及動態內容交互較多的場景，快速而可靠的網路連接對於立即進行螢幕反應以確保盡可能獲得最佳客戶體驗至關重要。

下表概述了網路連接密鑰資料。

>[!NOTE]
>該資訊允許您查看請求和下載網際網路源的網路中每個設備的消耗。 每個請求都會添加並延長下載時間。

![](/help/using/assets/enclosed-network-download.png)

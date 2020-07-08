---
title: 封閉的公司網路
description: 封閉的公司網路
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---


# 封閉的公司網路（有線／無線） {#enclosed-corporate-networks}

封閉的公司網路設定適用於小型，大型和企業。 理論上可能更複雜，邏輯設定如下圖所示。

![](/help/using/assets/enclosed-network-1.png)


## 將AEM Screens Player連線至Direct Internet Access {#connecting-aem-screens-players}

請依照下列步驟，確保在此設定中正確連線AEM Screen Player:

1. 請確定每個AEM Screen播放器都已連線至Routers Network。
1. 在您的系統瀏覽器中呼叫URL以測試網際網路連線。

   >[!NOTE]
   >如果收到錯誤，請檢查網路設定。正常網路連接基本上有兩個選項：
   >* DHCP
   >* 手動IP配置


1. 請確定「Network Adapter Setting（網路適配器設定）」與「Router Settings（路由器設定）」匹配，並檢查網路中是否未達到最大可用IP地址數。

1. 檢查路由器是否正確連接到ISP廣域網（Internet鏈路）。 此外，還可使用標準路由器上的信號LED來識別。
1. 如果URL呼叫成功，您可以繼續安裝AEM畫面並註冊。 開始AEM Screens。

   >[!NOTE]
   >**疑難排解提示**
   >如果AEM畫面未正確連線，且預期的內容未顯示：
   >
   >1. 如果Internet路由器防火牆有任何限制，請檢查該防火牆 `TCP/IP Port 80/443`。
   >1. 確保允許所有必需的埠。


## 設定封閉的公司網路 {#requirements-enclosed-networks}

封閉的公司網路設定可在邏輯上分成兩個塊：

* 廣域網(WAN)
* 內部區域網路(LAN)。

### 廣域網 {#wan-connection}

除了網路連線的效能外，網際網路連線還必須提供足夠的頻寬，以順暢地執行AEM Screens內容更新。
*足夠的頻寬* ，視連線的AEM螢幕數量以及網路內其他消費者（例如智慧型手機、平板電腦、收銀機、電腦或來賓Wi-Fi網路）的使用情況而定。

>[!NOTE]
>
>所有設備都可同時訪問網際網路連接，當您向網路添加更多消費者或電腦時，頻寬會線性下降。

### 區域網路 {#lan-connection}

區域網路(LAN)的效能除了網路連線能力外，還必須提供足夠的頻寬，以順暢地執行AEM Screens內容更新。

企業組織內的LAN網路通常至少為1000 MBit/秒網路，因此有足夠的頻寬將許多效能良好的設備連接到系統。 使用其他活動網路元件時，必須確保所有元件都符合網路頻寬要求。

例如，網路元件至少應符合100 Mbps標準，並與Internet訪問／路由器規範提供的頻寬相匹配。

### 其他公司網路詳情 {#other-networks}

公司網路具有多個連接的設備，被分成各種子網路，並具有冗餘或多路復用的網際網路連接，為數千個併發訪問提供足夠的效能。
此架構已簡化，並適用於客戶端的可用環境。

如果設想使用Wi-Fi解決方案將螢幕連接到Internet Link，建議使用現代Wi-Fi標準， `IEEE 802.11g` 如最低標準。 此標準支援高達54 Mbps的連接。 任何 *較新的* 「標準」 `802.11h-n` 都能提供更佳的品質。 如果需要Wi-Fi Repeater，我們強烈建議使用Mesh Wi-Fi接入點技術，例如Google Nest Mesh Wi-Fi或類似技術。
其他Wi-Fi重複技術最終導致整個網路的頻寬嚴重丟失。

## 下載媒體和資產 {#download}

AEM Screens為數位標牌使用者提供了絕大優勢。 它會下載並本機儲存所有必要的媒體檔案，例如影像和視訊。 當特定顯示器上顯示新內容時，會發生主要網路流量。

例如，對於一般作業，定義的播放清單會在一天中頻繁更新——當所有檔案都儲存在播放器上後，就會提供接近網路獨立的作業。

對於與感測器或觸發器和動態內容互動較多的情形，快速可靠的網路連線是立即進行螢幕反應以確保最佳客戶體驗的關鍵。

下表概述了網路連接關鍵資料。

>[!NOTE]
>
>該資訊允許您查看請求和下載網際網路源的網路中每個設備的使用情況。 每個請求都會加總並延長下載時間。

![](/help/using/assets/enclosed-network-download.png)

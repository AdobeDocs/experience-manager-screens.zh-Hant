---
title: 直接網際網路存取
description: 直接網際網路存取
translation-type: tm+mt
source-git-commit: ed683a86b7e8c6ec06309577bd0a8690a9cc4684
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 0%

---


# 直連網際網路（有線／無線） {#direct-internet-access}

Direct Internet Network包含可存取網際網路的入口存取點，以便存取AEM Screens所需的AEM Cloud服務。

AEM Screens通訊的標準埠包括：
* `http (TCP Port 80)`

   <br>或,</br>

* `ssl-secured https (TCP Port 443)`

埠可能因您專用AEM組態設定的組態而異。 在此SetUp中，所有設備都直接連接到您的Internet路由器，如下圖所示。

![](/help/assets/direct-access-2.png)

此組態還包括任何網際網路服務供應商(ISP)及其網際網路線路所提供的網際網路連線。 大部分的ISP都提供網際網路路由器，涵蓋網際網路調制解調器、網路交換機、Wi-Fi存取點、防火牆和其他網路功能（視製造商和機型而定）。

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


## 設定直接接入網路的要求 {#requirements-direct}

Direct Internet Network邏輯上分為兩個塊：

* 廣域網

* 區域網路

### 廣域網 {#wan-connection}

除了網路的可達性外，網際網路連線的效能是提供足夠的頻寬，以運作AEM畫面。

*足夠* ，視連線的AEM螢幕數量以及網路內其他消費者的使用情況而定，例如智慧型手機、平板電腦、收銀機、電腦或來賓Wi-Fi網路。

>[!NOTE]
>上述所有裝置都可同時存取網際網路連線，而且當您新增更多消費者或電腦至網路時，頻寬會線性降低。

### 區域網路 {#lan-connection}

區域網路(LAN)的效能，除了網路的可達性外，還提供足夠的頻寬，以運作AEM畫面。

LAN網路通常至少與100 Mbps網路匹配，因此有足夠的頻寬將許多效能良好的設備連接到系統。
如果設想使用Wi-Fi解決方案將AEM Screens連線至網際網路連結，建議您至少使用現代Wi-Fi `IEEE 802.11g` 標準。 此標準支援高達54 Mbps的連接。 任何 *較新的* 「標準」 `802.11h-n` 都能提供更佳的品質。

>[!NOTE]
>如果需要Wi-Fi Repeater，強烈建議使用Mesh Wi-Fi接入點，如Google Nest Mesh Wi-Fi或類似的接入點。 其他Wi-Fi重複技術最終導致整個網路的頻寬嚴重丟失。

## 下載媒體和資產 {#download}

AEM Screens為數位標牌使用者提供了絕大優勢。 它會下載並本機儲存所有必要的媒體檔案，例如影像和視訊。 當特定顯示器上顯示新內容時，會發生主要網路流量。

例如，對於一般作業，定義的播放清單會在一天中頻繁更新——當所有檔案都儲存在播放器上後，就會提供接近網路獨立的作業。

對於與感測器或觸發器和動態內容互動較多的情形，快速可靠的網路連線是立即進行螢幕反應以確保最佳客戶體驗的關鍵。

下表概述了網路連接關鍵資料。

>[!NOTE]
>該資訊允許您查看請求和下載網際網路源的網路中每個設備的使用情況。 每個請求都會加總並延長下載時間。

![](/help/assets/download-times-direct.png)


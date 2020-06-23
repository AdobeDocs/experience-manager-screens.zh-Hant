---
title: 直接網際網路存取
description: 直接網際網路存取
translation-type: tm+mt
source-git-commit: 70dddffd46ebf1bd83b25515be548bc442e45fea
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---


# 直接網際網路存取 {#direct-internet-access}

Direct Internet Access SetUp包含網際網路存取的入口存取點，以便存取AEM Screens所需的AEM Cloud服務。

AEM Screens通訊的標準埠包括：
* `http (TCP Port 80)`
或,
* `ssl-secured https (TCP Port 443)`

埠可能因您專用AEM組態設定的組態而異。 在此SetUp中，所有設備都直接連接到您的Internet路由器，如下圖所示。

![](/help/assets/direct-access-2.png)

此組態也包含任何網際網路服務供應商(ISP)及其網際網路連線所提供的網際網路存取功能。 大部分的ISP都提供網際網路路由器，涵蓋網際網路調制解調器、網路交換機、WIFI存取點、防火牆和其他網路功能（視製造商和機型而定）。

## 將AEM Screens Player連線至Direct Internet Access {#connecting-aem-screens-players}

請依照下列步驟，在此設定中連線AEM Screen Player:

1. 請確定每個AEM Screen播放器都已連線至Routers Network。
1. 在您的系統瀏覽器中呼叫URL以測試網際網路連線。

   >[!NOTE]
   >如果收到錯誤消息，請檢查網路設定。正常網路連接基本上有兩個選項：
   >* DHCP
   >* 手動IP配置


1. 確保「Network Adapter Setting（網路適配器設定）」與「Router Setting（路由器設定）」匹配，並檢查是否未到達網路中的「Maximum of available IP addresses（最大可用IP地址數量）」。

1. 檢查路由器是否正確連接到ISP廣域網（Internet鏈路）。這通常也可以使用標準路由器上的信號LED來標識。
1. 如果URL呼叫成功，您可以繼續安裝AEM畫面並依此註冊。 開始AEM Screens。

   >[!NOTE]
   >**疑難排解提示**
   >如果AEM畫面未正確連線，且未顯示預期的內容：
   >
   >1. 如果Internet路由器防火牆有任何限制，請檢查該防火牆 `TCP/IP Port 80/443`。
   >1. 確保允許所有需要的埠。


## 設定直接接入網路的要求 {#requirements-direct}

直接訪問網路設定可以在邏輯上分成兩個塊：

* 廣域網

* 區域網路

### 廣域網 {#wan-connection}

除了網路連線外，網際網路連線的效能是提供足夠的頻寬，讓AEM Screens順暢地運作。

*足夠* ，視連線的AEM螢幕數量以及網路內其他消費者的使用情況而定，例如智慧型手機、平板電腦、收銀機、電腦或來賓WIFI網路。

>[!NOTE]
>所有設備都可同時訪問網際網路連接，而頻寬通常在向網路添加更多消費者／電腦時線性下降。

### 區域網路 {#lan-connection}

區域網路(LAN)的效能除了網路連線能力外，還提供足夠的頻寬，讓AEM畫面順暢運作。

LAN網路通常至少與100 MBit/s網路匹配，因此有足夠的頻寬將許多效能良好的設備連接到系統。
如果設想使用WIFI解決方案將AEM畫面連接至網際網路連結，建議您至少使用IEEE 802.11g等現代WIFI標準。 此標準支援高達54 Mbps的連接。 任何 *較新的* 「標準」（例如802.11h-n）都能提供更佳的品質。

>[!NOTE]
>如果需要WIFI中繼器，我們強烈建議使用Mesh WIFI存取點技術，例如Google Nest Mesh WIFI或類似技術。 其他WiFi重複技術最終導致整個網路的頻寬大量丟失。

## 下載媒體和資產 {#download}

AEM Screens為數位標牌使用者提供了絕大優勢。 它會下載並本機儲存所有必要的媒體檔案，例如影像和視訊。 由於這個概念，當特定螢幕上顯示新內容時，就會發生主要網路流量。
例如，在正常作業中，定義的播放清單在一天中不會經常變更，當所有檔案都儲存在播放器上後，這可提供接近網路獨立作業。
對於與感測器或其他觸發器互動較多且內容動態的使用案例，快速可靠的網路連線是立即進行螢幕反應以確保最佳客戶體驗的關鍵。

下表概述了網路連接關鍵資料。

>[!NOTE]
>該資訊允許您查看網路中請求和下載網際網路源的每台設備的使用情況。 每個請求都會加總並延長下載時間。

![](/help/assets/download-times-direct.png)


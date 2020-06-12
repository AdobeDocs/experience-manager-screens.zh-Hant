---
title: 直接網際網路存取
description: 直接網際網路存取
translation-type: tm+mt
source-git-commit: 3527dd38898399e692e114edb492825b18b28f86
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---


# 直接網際網路存取 {#direct-internet-access}

Direct Internet Access SetUp包含網際網路存取的入口存取點，以便存取AEM Screens所需的AEM Cloud服務。

AEM Screens通訊的標準埠包括：
* `http (TCP Port 80)`
或,
* `ssl-secured https (TCP Port 443)`

埠可能因您的專用AEM配置而異。 在此SetUp中，所有設備都直接連接到您的Internet路由器，如下圖所示。

![](/help/assets/direct-access-2.png)

此組態也包含任何網際網路服務供應商所提供的網際網路存取功能，以及其網際網路連線。 大部分的ISP都提供網際網路路由器，涵蓋網際網路調制解調器、網路交換機、WIFI存取點、防火牆和其他網路功能（視製造商和機型而定）。

>[!NOTE]
>**疑難排解提示&#x200B;**>如果AEM畫面無法正確連線，並顯示預期的內容：
>
>1. 如果Internet路由器防火牆有任何限制，請檢查該防火牆 `TCP/IP Port 80/443`。
>1. 請確定允許所有需要的埠並重試。


## 設定直接接入網路的要求 {#requirements-direct}

直接訪問網路設定可以在邏輯上分成兩個塊。 WAN/Outer World/Internet連接塊和內部LAN/區域網路。

### WAN / Internet連接 {#wan-connection}

除了已描述的網路連線能力外，網際網路連線的效能還提供足夠的頻寬，讓AEM Screens順暢地運作。 詳細說明，「足夠」取決於連線的AEM螢幕數量，以及網路內其他消費者的使用情形，例如智慧型手機、平板電腦、收銀機、電腦或來賓WIFI網路。
請記住，所有裝置都可同時存取網際網路連線，而且頻寬通常會線性降低，同時增加更多消費者／電腦至網路。

### LAN連接 {#lan-connection}

除了已描述的網路連線能力外，LAN的效能還提供足夠的頻寬，讓AEM Screens順暢地運作。 如今，LAN網路通常至少與100MBit/s網路匹配，因此應該有足夠的頻寬將許多效能良好的設備連接到系統。
如果設想使用WIFI解決方案將螢幕連接到Internet Link，建議使用IEEE 802.11g等現代WIFI標準作為最低標準。 此標準支援高達54Mb的連接。 任何 *較新的* 「標準」（例如802.11h-n）都能提供更佳的品質。 如果需要WIFI中繼器，我們強烈建議使用Mesh WIFI存取點技術，例如Google Nest Mesh WIFI或類似技術。
其他WiFi重複技術最終導致整個網路的頻寬大量丟失。

## 下載媒體和資產 {#download}

AEM Screens為數位標牌使用者提供了絕大優勢。 它會下載並儲存所有必要的媒體檔案，例如影像和視訊。 由於這個概念，當特定螢幕上顯示新內容時，會發生主要網路流量。
例如，在正常作業中，定義的播放清單在一天中不會經常變更，當所有檔案都儲存在播放器上後，這可提供接近網路獨立作業。
對於與感測器或其他觸發器互動較多且內容動態的使用案例，快速可靠的網路連線是立即進行螢幕反應以確保最佳客戶體驗的關鍵。

下表概述了網路連接關鍵資料：

![](/help/assets/direct-access-1.png)

>[!NOTE]
>該資訊允許您查看網路中請求和下載網際網路源的每台設備的使用情況。 因此，每個請求都會加總並延長下載時間。
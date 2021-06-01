---
title: 直接網際網路存取
description: 直接網際網路存取
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---


# 直接Internet網路（有線/無線）{#direct-internet-access}

「直接網際網路」包含進入點，可存取網際網路，以便存取AEM Screens需要連線的AEM雲端服務。

AEM Screens通信的標準埠為：
* `ssl-secured https (TCP Port 443)`

   <br>或,</br>

* `http (TCP Port 80)`，若您的特定使用案例不需要該等級的安全性。

埠可能會因您專用AEM組態設定的組態而異。 在此SetUp中，所有設備都直接連接到Internet路由器，如下圖所示。

![](/help/assets/direct-access-2.png)

此配置還包括任何Internet服務提供商(ISP)及其Internet線路的Internet接入。 大多數ISP提供的Internet路由器涵蓋Internet資料機、網路交換機、Wi-Fi接入點、防火牆和其他網路功能（取決於製造商和型號）。

## 將AEM Screens Player連接到直接Internet訪問{#connecting-aem-screens-players}

請依照下列步驟，確保在此設定中正確連線AEM螢幕播放器：

1. 確保每個AEM螢幕播放器都連接到路由器的網路。
1. 通過調用系統瀏覽器中的URL來測試Internet連接。

   >[!NOTE]
   >如果收到錯誤，請檢查網路設定。對於正確的網路連接，基本上有兩個選項：
   >* DHCP
   >* 手動IP配置


1. 確保網路適配器設定與路由器設定匹配，並檢查網路中的可用IP地址的最大數量是否未達到。

1. 檢查路由器是否正確連接到ISP廣域網(Internet Link)。 這也可以使用標準路由器上的信號LED來識別。
1. 如果URL呼叫成功，您可以繼續安裝AEM Screens並註冊。 啟動AEM Screens。

   >[!NOTE]
   >**疑難排解提示**
   >如果AEM Screens未正確連線，且未顯示預期的內容：
   >
   >1. 如果`TCP/IP Port 80/443`有任何限制，請檢查您的Internet路由器防火牆。
   >1. 請確保允許所有必要的埠。


## 設定直接訪問網路{#requirements-direct}

直接網際網路在邏輯上分為兩個區塊：

* 廣域網

* 區域網路

### 廣域網{#wan-connection}

除了網路的可達性外，Internet連接的效能是提供足夠的頻寬來運行AEM Screens。

** 充分取決於連接的AEM螢幕的數量以及網路內其他消費者（如智慧手機、平板電腦、收銀機、電腦或來賓Wi-Fi網路）的使用情況。

>[!NOTE]
>
>上述所有設備均可同時訪問Internet連接，並且當您向網路添加更多消費者或電腦時，頻寬會線性減少。

### 區域網路{#lan-connection}

區域網路(LAN)的效能，除了網路的可達性之外，還提供了足夠的頻寬來運行AEM Screens。

區域網路通常至少與100 Mbps的網路匹配，因此有足夠的頻寬將許多效能良好的設備連接到系統。
如果設想使用Wi-Fi解決方案將AEM Screens連接到Internet Link，則建議至少使用`IEEE 802.11g`等現代Wi-Fi標準。 此標準支援高達54 Mbps的連接。 任何&#x200B;*較新的*&#x200B;標準（如`802.11h-n`）的品質都較佳。

>[!NOTE]
>
>如果需要Wi-Fi中繼器，強烈建議使用Mesh Wi-Fi存取點，例如Google Nest Mesh Wi-Fi或類似的存取點。 其他Wi-Fi重複技術最終導致整個網路的頻寬大量丟失。

## 下載媒體和資產 {#download}

AEM Screens為數位看板使用者提供絕大優勢。 它會下載並在本機儲存所有必要的媒體檔案，例如影像和視訊。 當特定顯示器上顯示新內容時，會發生主要網路流量。

對於正常操作，例如，定義的播放清單在一天中經常更新 — 提供接近網路的獨立操作，一旦所有檔案都保存在播放器上。

對於與感測器或觸發器以及動態內容有更多互動的情況，快速而可靠的網路連接對於立即進行螢幕反應來確保最佳客戶體驗至關重要。

下表概述了網路連接密鑰資料。

>[!NOTE]
>
>該資訊允許您查看請求和下載網際網路源的網路中每個設備的消耗。 每個請求都會加總並延長下載時間。

![](/help/assets/download-times-direct.png)


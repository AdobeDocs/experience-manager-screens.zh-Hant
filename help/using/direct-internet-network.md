---
title: 直接Internet訪問
description: 直接Internet訪問
exl-id: a393ce2f-b774-4cd5-9001-c5cc24d445ae
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---

# 直接Internet網路（有線/無線） {#direct-internet-access}

Direct Internet Network包含一個用於Internet接入的入口接入點，以便訪問AEM Screens需要連接的AEM雲服務。

AEM Screens通信的標準埠為：
* `ssl-secured https (TCP Port 443)`

   <br>或,</br>

* `http (TCP Port 80)`，如果您的特定使用案例不需要該級別的安全性。

埠可能因專用配置設定的AEM配置而異。 在此SetUp中，所有設備都直接連接到您的Internet路由器，如下圖所示。

![](/help/assets/direct-access-2.png)

該配置還包括任何網際網路服務提供商(ISP)及其網際網路線路的網際網路接入。 大多數ISP提供的Internet路由器涵蓋Internet調制解調器、網路交換機、Wi-Fi接入點、防火牆和其他網路功能（取決於製造商和型號）。

## 將AEM Screens播放器連接到直接Internet訪問 {#connecting-aem-screens-players}

按照以下步驟確保此配置中的螢幕播放AEM器正確連接：

1. 確保每個螢幕播放AEM器都連接到路由器的網路。
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


## 設定直接訪問網路 {#requirements-direct}

Direct Internet Network邏輯上分為兩個塊：

* 廣域網

* 區域網路

### 廣域網 {#wan-connection}

除了網路的可達性外，網際網路連接的效能是提供足夠的頻寬來運行AEM Screens。

*足夠* 取決於已連接螢幕的AEM數量以及網路內其他消費者的使用情況，如智慧電話、平板電腦、收銀機、電腦或來賓Wi-Fi網路。

>[!NOTE]
>
>上述所有設備都可同時訪問Internet連接，並且當您向網路添加更多用戶或電腦時，頻寬會線性下降。

### 區域網路 {#lan-connection}

區域網路(LAN)的效能，除了網路的可達性外，還提供了足夠的頻寬來運行AEM Screens。

LAN網路通常至少與100 Mbps的網路匹配，因此有足夠的頻寬將許多效能良好的設備連接到系統。
如果設想使用Wi-Fi解決方案將AEM Screens連接到Internet Link，建議使用現代Wi-Fi標準，如 `IEEE 802.11g` 最起碼。 此標準支援高達54 Mbps的連接。 任意 *新* 標準如 `802.11h-n` 質量更好。

>[!NOTE]
>
>如果需要Wi-Fi中繼器，強烈建議使用Mesh Wi-Fi接入點，如GoogleNest Mesh Wi-Fi或類似的接入點。 其他Wi-Fi重複技術最終導致整個網路的頻寬大量丟失。

## 下載媒體和資產 {#download}

AEM Screens為數字標牌用戶提供了巨大優勢。 它下載並本地保存所有必要的媒體檔案，如影像和視頻。 當在特定顯示器上顯示新內容時，會發生主要網路流量。

例如，對於正常操作，定義的在一天中頻繁更新的播放清單在所有檔案都保存到播放器上後，提供接近網路獨立操作。

對於與感測器或觸發器以及動態內容交互較多的場景，快速而可靠的網路連接對於立即進行螢幕反應以確保盡可能獲得最佳客戶體驗至關重要。

下表概述了網路連接密鑰資料。

>[!NOTE]
>
>該資訊允許您查看請求和下載網際網路源的網路中每個設備的消耗。 每個請求都會添加並延長下載時間。

![](/help/assets/download-times-direct.png)

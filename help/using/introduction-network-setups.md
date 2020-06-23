---
title: 標準網路設定簡介
seo-title: 標準網路設定簡介
description: 此頁介紹標準網路設定
seo-description: 此頁介紹標準網路設定
translation-type: tm+mt
source-git-commit: 0be82fcc46166ec0613bd658a0caeab83bd72551
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---


# 管理網路流量 {#managing-network-traffic}

網路設定可以有各種結構。 本節概述在環境中部署的網路結構。 有些不同的設定，有時從頭開始實作。

本節重點介紹在不同組織中設定的不同網路結構之後的代理伺服器。

>[!NOTE]
>**AEM Screens網路需求&#x200B;**>AEM畫面會直接與AEM Cloud服務通訊，因此需要在這兩個節點之間建立穩定的連線。 對於商業Internet訪問，防火牆是絕對必備的，客戶需要知道哪些通信埠需要在防火牆中開啟，以及與IT安全相關的其他網路元件，這些元件由客戶控制。

## 代理伺服器 {#proxy-servers}

代理伺服器是運行在電腦上的專用電腦或軟體系統，它充當終端設備（如電腦）和用戶或客戶端請求服務的另一伺服器之間的中介。 代理伺服器可以與防火牆伺服器位於同一台電腦中，也可以位於單獨的伺服器上，後者通過防火牆轉發請求。

代理伺服器的優勢在於，它的快取可以為所有用戶服務。 如果經常要求一或多個網際網路網站，這些網站可能會位於Proxy的快取中，這將改善使用者的回應時間。 Proxy也可記錄其互動，這有助於疑難排解。

## 瞭解標準網路設定 {#network-setups}

要實施網路設定，您必須參考以下具有優勢和部署詳細資訊的方案。

網路設定有三種主要類型：

1. [直連網際網路（有線／無線）](/help/using/direct-internet-network.md)
1. [直接行動網路](/help/using/mobile-network.md)
1. [具有移動資料路由器和活動網路元件的移動網路](/help/using/mobile-network-router.md)
1. [封閉的公司網路（有線／無線）](/help/using/enclosed-corporate-network.md)

下表列出了各種網路設定的優缺點：

<table>
 <tbody>
  <tr>
   <td><strong>網路設定</strong></td>
   <td><strong>優勢</strong></td>
   <td><strong>缺點</strong></td>
  </tr>
  <tr>
   <td><strong>直接網際網路存取</strong></td>
   <td>輕鬆而直接地向SetUp<br>選擇中型或大型安裝<br>專用網路可封裝少<br>數故障點相對<br>便宜<br>良好的可擴充性</td>
   <td>必要的適當Internet資料計畫</td>
  </tr>
    <tr>
   <td><strong>直接行動網路</strong></td>
   <td>輕鬆直接使用SetUp<br>適合中型或大型安裝良好的選擇良好的可擴充性<br>封裝<br>的螢幕
</td>
   <td>必須有適當的網際網路連線</td>
  </tr>
    <tr>
<tr>
   <td><strong>具有移動資料路由器和活動網路元件的移動網路</strong></td>
   <td>輕鬆直接向SetUp<br>適合中型或大型安裝<br>專用網路可封裝少<br>數故障點<br>相對便宜<br>良好</br></td>
   <td>必要的適當Internet資料計畫</td>
  </tr>
    <tr>

<td><strong>封閉的公司網路</strong></td>
   <td>高靈活性和可擴<br>展性由於不同的防線封裝網路<br><br>，高度安全易於監<br>控和維護可靠</td>
   <td>建議使用複雜且<br>昂貴的網路專家或系統整合商</td>
  </tr>
  </tr>
 </tbody>
</table>



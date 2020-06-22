---
title: 瞭解代理伺服器
seo-title: 瞭解代理伺服器
description: 該頁介紹代理伺服器
seo-description: 該頁介紹代理伺服器
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# 標準網路設定簡介 {#intro-standard-networks}

網路設定可以有各種結構。 本節概述在環境中部署的網路結構。 有些不同的設定，有時從頭開始實作。

本節重點介紹在不同組織中設定的不同網路結構之後的代理伺服器。

## 代理伺服器 {#proxy-servers}

代理伺服器是運行在電腦上的專用電腦或軟體系統，它充當終端設備（如電腦）和用戶或客戶端請求服務的另一伺服器之間的中介。 代理伺服器可以與防火牆伺服器位於同一台電腦中，也可以位於單獨的伺服器上，後者通過防火牆轉發請求。

代理伺服器的優勢在於，它的快取可以為所有用戶服務。 如果經常要求一或多個網際網路網站，這些網站可能會位於Proxy的快取中，這將改善使用者的回應時間。 Proxy也可記錄其互動，這有助於疑難排解。

## 瞭解網路設定 {#network-setups}

要實施網路設定，您必須參考以下具有正反兩方面的情況。

網路設定有三種主要類型：

1. Internet訪問設定
1. 行動網路設定
1. 封閉的公司網路設定

下表列出了各種網路設定的優缺點：

<table>
 <tbody>
  <tr>
   <td><strong>網路設定</strong></td>
   <td><strong>優勢</strong></td>
   <td><strong>缺點</strong></td>
  </tr>
  <tr>
   <td><strong>Internet訪問設定</strong></td>
   <td>輕鬆而直接地向SetUp<br>選擇中型或大型安裝<br>專用網路可封裝少<br>數故障點相對<br>便宜<br>良好的可擴充性</td>
   <td>必要的適當Internet資料計畫</td>
  </tr>
    <tr>
   <td><strong>行動網路設定</strong></td>
   <td>輕鬆直接向SetUp<br>適合中型或大型安裝<br>專用網路可封裝少<br>數故障點<br>相對便宜<br>良好</br></td>
   <td>必須有適當的網際網路連線</td>
  </tr>
    <tr>
   <td><strong>封閉的公司網路</strong></td>
   <td>高靈活性和可擴<br>展性由於不同的防線封裝網路<br><br>，高度安全易於監<br>控和維護可靠</td>
   <td>建議使用複雜且<br>昂貴的網路專家或系統整合商</td>
  </tr>
  </tr>
 </tbody>
</table>



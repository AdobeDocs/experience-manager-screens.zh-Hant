---
title: 標準網路設定簡介
seo-title: 標準網路設定簡介
description: 此頁介紹標準網路設定
seo-description: 此頁介紹標準網路設定
translation-type: tm+mt
source-git-commit: 77cf87cbce39a00528b2690d9689861b91e61fc5
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# 管理網路流量 {#managing-network-traffic}

網路設定可以有各種結構。 本節介紹組織網路設定中最常用的網路設定。

本指南重點介紹代理伺服器，然後介紹在不同組織內設定的各種網路結構。

>[!NOTE]
>**AEM Screens網路需求&#x200B;**>AEM Screens會以雲端服務的形式直接與AEM通訊，因此需要在兩個節點之間建立穩定的連線。 防火牆對於商業Internet訪問是絕對必備的，作為客戶，您必須瞭解在防火牆和其他與IT安全相關的網路元件中需要開啟哪些通信埠。

## 代理伺服器概述 {#proxy-servers}

網際網路連線需仰賴使用Proxy伺服器。 代理伺服器是在電腦上運行的專用電腦或軟體系統，它充當終端設備（如電腦）和用戶或客戶端請求服務的另一伺服器之間的中介。 代理伺服器可以與防火牆伺服器位於同一台電腦中，也可以位於單獨的伺服器上，後者通過防火牆轉發請求。

代理伺服器的優勢在於，它的快取可以為所有用戶服務。 如果經常要求一或多個網際網路網站，這些網站可能位於Proxy的快取中，可改善使用者回應時間。 Proxy也可記錄其互動，用於疑難排解。

## 瞭解標準網路設定 {#network-setups}

要實施網路設定，您必須參考以下方案及其優勢和部署詳細資訊。

網路設定有四種主要類型：

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
   <td><strong>直連網際網路（有線／無線）</strong></td>
   <td>輕鬆直接地向SetUp<br>適合中型或大型安裝<br>專用網路可封裝少<br>數故障點相對<br>便宜<br>的擴展</td>
   <td>強制性網際網路資料計畫 </td>
  </tr>
    <tr>
   <td><strong>直接行動網路</strong></td>
   <td>易於設定<br>適合中型或大型安裝的好選擇良好的可擴充性<br>封裝<br>的螢幕
</td>
   <td>強制性網際網路連線</td>
  </tr>
    <tr>
<tr>
   <td><strong>具有移動資料路由器和活動網路元件的移動網路</strong></td>
   <td>易於設定<br>適合中型或大型安裝的好選擇專用網路<br>可封裝少<br>數故障點相對<br>便宜<br>的擴展</br></td>
   <td>強制性網際網路資料計畫</td>
  </tr>
    <tr>

<td><strong>封閉的公司網路（有線／無線）</strong></td>
   <td>高靈活性和可擴<br>展性由於不同的防線封裝網路<br>而<br>且易於監控和維<br>護</td>
   <td>為網路專家或系<br>統整合商推薦的複雜而昂貴的產品</td>
  </tr>
  </tr>
 </tbody>
</table>



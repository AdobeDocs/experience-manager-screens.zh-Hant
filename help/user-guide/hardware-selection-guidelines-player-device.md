---
title: 播放器裝置的硬體選擇准則
description: 瞭解AEM Screens Player裝置的硬體選擇准則。
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 3%

---


# 播放器裝置的硬體選擇准則 {#hardware-selection}

下節提供AEM Screens Player的硬體選擇准則。

## 重要考量 {#important-considerations}

* 永遠來源 ***商業*** 或 ***工業*** PC播放器及顯示面板或投影機的等級元件。

* 永遠與數位看板市場的供應商互動。
* 請務必考量環境因素，例如環境溫度和相對濕度。
* 請務必檢閱電源需求與電源調節。
* 請仔細檢閱應用程式所需的效能需求和I/O連線埠。

## 硬體組態 {#hardware-configurations}

下表概述AEM Screens專案的硬體組態與典型使用案例：

<table>
 <tbody>
  <tr>
   <tr>
   <td><strong>播放器設定</strong></td>
   <td><strong>處理器</strong></td>
   <td><strong>記憶體</strong></td>
   <td><strong>儲存固態硬碟</strong></td>
   <td><strong>GPU</strong></td>
   <td><strong>顯示區</strong></td>
   <td><strong>I/O</strong></td>
   <td><strong>典型使用案例</strong></td>
  </tr>
  <tr>
   <td>基本</td>
   <td>雙核心、i3或入門級四核心Intel® Atom處理器</td>
   <td><p>4 GB記憶體</p> <p>2 MB快取</p> </td>
   <td><p>*ChromeOS 32 GB</p> <p>*Windows 128 GB</p> </td>
   <td>主機板</td>
   <td>1920 x 1080</td>
   <td>DVI<br /> 乙太網路/無線、<br /> 2個USB</td>
   <td>
    <ul>
     <li>標準全熒幕循環<br /> </li>
     <li>日時段分割</li>
    </ul> </td>
  </tr>
  <tr>
   <td>標準</td>
   <td>四核心、Intel® Core™ i5處理器</td>
   <td><p>8 GB記憶體</p> <p>4 MB快取</p> </td>
   <td>128 GB</td>
   <td>主機板</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI、HDMI<br /> 乙太網路/無線、<br /> 2個USB</td>
   <td>
    <ul>
     <li>單一來源動態內容</li>
     <li>簡單互動式</li>
     <li>1-3區域配置</li>
    </ul> </td>
  </tr>
  <tr>
   <td>進階</td>
   <td>四核心含超執行緒、Intel® Core™ i7處理器</td>
   <td><p>16 GB記憶體</p> <p>8 MB快取</p> </td>
   <td>256 GB</td>
   <td>專用圖形GPU</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI、HDMI<br /> 乙太網路/無線、<br /> 4個USB</td>
   <td>
    <ul>
     <li>4個或更多內容區域，同時播放視訊</li>
     <li>多頁互動式</li>
     <li>多來源資料觸發器</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

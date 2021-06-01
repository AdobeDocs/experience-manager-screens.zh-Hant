---
title: 使用AEM Screens Player
seo-title: 使用Screens Player
description: 請詳閱本頁以了解Screens Player。 也說明管理員UI和通道切換器。
seo-description: 請詳閱本頁以了解Screens Player。 也說明管理員UI和通道切換器。
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
feature: 管理畫面
role: Administrator
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 1%

---


# 使用AEM Screens Player {#working-with-aem-screens-player}

您可以在AEM Screens播放器上管理頻道內容和其他設定。

>[!NOTE]
>
>按&#x200B;***Ctrl+Cmd+F***&#x200B;退出OS X AEM Screens Player的全螢幕模式。

將頻道指派給顯示器後，AEM Screens播放器就會顯示內容。 您可以使用管理員UI的偏好設定（從控制面板）或從播放器本身來設定播放器的設定。

## 使用設備儀表板{#using-the-device-dashboard}

您可以從裝置控制面板設定裝置的偏好設定，可透過AEM製作例項存取。

1. 從您的專案導覽至裝置控制面板，例如&#x200B;***測試專案*** —> ***裝置***。

   從操作欄中選擇&#x200B;**設備**&#x200B;和&#x200B;**設備管理器**。

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. 按一下裝置以開啟裝置控制面板。

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. 檢查&#x200B;**PREFERENCES**&#x200B;面板。 您可以透過這兩個選項，啟用/停用您播放器的&#x200B;**管理UI**&#x200B;和&#x200B;**頻道切換器**。

   ![chlimage_1-68](assets/chlimage_1-68.png)

### 管理員UI {#the-admin-ui}

從偏好設定面板啟用&#x200B;**管理UI**&#x200B;可讓使用者從Screens Player開啟管理設定。 此外，如果您從裝置控制面板停用此選項，使用者將無法從播放器開啟管理員UI。

若要從Screens播放器檢視管理員UI，請在左上角長按以開啟「管理員」功能表、啟用觸控的AEM Screens播放器，或使用滑鼠。 它會在註冊完成後顯示資訊並載入通道。

>[!NOTE]
>
>此外，您也可以檢視AEM Screens Player應用程式的正常運作時間，以檢查應用程式健康狀態。

![chlimage_1-3](assets/chlimage_1-3.gif)

#### 訪問配置菜單選項{#configuration-options}

如果從側菜單中選擇&#x200B;**Configuration**&#x200B;選項，則可以更新配置，如下圖所示：

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

「配置」菜單允許您修改以下設定：

* 從此對話框重置&#x200B;**韌體**、**首選項**&#x200B;或&#x200B;**至工廠**。

* 指定在&#x200B;**最大編號中為AEM Screens播放器保留的最大日誌檔案數。 保留**&#x200B;的日誌檔案。

* 為Screens播放器啟用或停用&#x200B;**管理功能表**、**頻道切換器**&#x200B;和&#x200B;**活動UI**。

   如果從&#x200B;**Configuration**&#x200B;功能表啟用&#x200B;**Activity UI**,AEM Screens播放器會在播放器的右上角顯示&#x200B;*播放器活動通知*，如下圖所示。

   ![影像](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>**更新韌體**&#x200B;選項只能在cordova（如Android播放器）上運作。

>[!NOTE]
>
>建議在生產部署中停用&#x200B;**管理UI**。

#### 訪問「內容快取」菜單選項{#content-cache-options}

您可以從AEM Screens播放器的管理員UI中清除通道和應用程式的快取。

從側邊欄選取「**內容快取**」以更新快取。

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### 通道切換器{#the-channel-switcher}

從偏好設定面板啟用&#x200B;**頻道切換器**&#x200B;可讓使用者從Screens播放器開啟頻道選取/設定。

此外，如果您從裝置控制面板停用此選項，使用者將無法從Screens Player控制通道偏好設定。

您可以從Screens Player切換並控制頻道的設定。

若要從播放器檢視頻道切換器，請長按左下角以開啟允許切換頻道和其他功能的頻道切換器。

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>您也可以從Screens播放器啟用或停用播放器的管理功能表和頻道切換器。
>
>（請參閱下節中提及的&#x200B;*從Screens Player*&#x200B;變更偏好設定）。

### 從AEM Screens播放器{#managing-preferences-from-the-aem-screens-player}管理偏好設定

您也可以從播放器本身變更管理員UI和通道切換器的設定。

請依照下列步驟，變更播放器的偏好設定：

1. 長按閒置頻道左上角的以開啟「管理面板」。
1. 從左側動作功能表導覽至&#x200B;**Configuration**。
1. 啟用/停用&#x200B;**管理UI**&#x200B;或&#x200B;**通道切換器**&#x200B;的設定。

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## 疑難排解AEM Screens Player {#troubleshooting-aem-screens-player}

您可以疑難排解與AEM Screens Player（硬體和軟體）相關的各種問題：

| **問題** | **建議** |
|---|---|
| 播放器儲存已滿 | 消除不必要的檔案 |
| 播放器丟失網路 | 使用Cat-5/Cat-6電纜。 對於wifi，減少從路由器到播放器設備的距離 |
| AEM Screens播放器當機 | 建議您有一個監看程式，確保AEM Screens Player一律執行 |
| AEM Screens播放器遺失設定 | 檢查與AEM伺服器的連線 |
| AEM Screens Player重新啟動/重新啟動後不會自動啟動 | 檢查作業系統啟動資料夾或初始化過程 |
| AEM Screens Player顯示錯誤/舊內容 | 檢查網路連接 |

### AEM Screens Player {#updates-for-aem-screens-player}的更新

AEM Screens播放器有兩種更新類型：

| **方法** | **詳細資料** | **透過遠端** | **自動** | **0停機時間** |
|---|---|---|---|---|
| 韌體更新 | 透過遠端命令套用至現有已安裝的播放器。 更新後，播放器會使用現有內容自動重新載入。 | 是 | 自訂 | 近 — 1-3秒 |
| 播放器殼層更新 | 這是要部署在播放器上的新執行檔。 這需要在播放器上遠端複製新的二進位檔，並停止目前執行中，然後啟動新版本。 這可能需要重新下載預先載入的套件。 | 是（通過遠程外殼） | 自訂 | 否 |

## 播放器設備{#hardware-selection-guidelines-for-player-device}的硬體選擇指南

以下章節提供Screens專案的硬體選擇准則：

* 始終為PC播放器和顯示面板或投影儀源&#x200B;***商業***&#x200B;或&#x200B;***工業***&#x200B;等級元件。

* 請務必與提供數位看板市場的廠商互動。
* 始終考慮環境因素，如環境溫度和相對濕度。
* 始終檢查電源要求和電源調節。
* 仔細審查應用程式所需的效能需求和I/O埠。

下表概述硬體配置以及AEM Screens項目的典型使用案例：

<table>
 <tbody>
  <tr>
   <td>播放器設定</td>
   <td>處理器</td>
   <td>記憶體</td>
   <td>儲存固態硬碟</td>
   <td>GPU</td>
   <td>顯示</td>
   <td>I/O</td>
   <td>典型使用案例</td>
  </tr>
  <tr>
   <td>基本</td>
   <td>雙核、i3或入門級四核英特爾®凌動處理器</td>
   <td><p>4GB記憶體</p> <p>2MB快取</p> </td>
   <td><p>· ChromeOS 32 GB</p> <p>· Windows 128GB</p> </td>
   <td>板載</td>
   <td>1920x1080</td>
   <td>DVI,<br />乙太網/無線，<br /> 2xUSB</td>
   <td>
    <ul>
     <li>標準全螢幕循環<br /> </li>
     <li>日劃分</li>
    </ul> </td>
  </tr>
  <tr>
   <td>標準</td>
   <td>四核，英特爾®酷睿i5處理器</td>
   <td><p>8GB記憶體</p> <p>4MB快取</p> </td>
   <td>128 GBB</td>
   <td>板載</td>
   <td>3840x2160(4K)</td>
   <td>DVI、HDMI<br />乙太網/無線，<br /> 2xUSB</td>
   <td>
    <ul>
     <li>單一來源動態內容</li>
     <li>簡單互動式</li>
     <li>1-3個區域佈局</li>
    </ul> </td>
  </tr>
  <tr>
   <td>進階</td>
   <td>四核超線程，英特爾®酷睿i7處理器</td>
   <td><p>16GB記憶體</p> <p>8MB快取</p> </td>
   <td>256 GB</td>
   <td>專用圖形GPU</td>
   <td>3840x2160(4K)</td>
   <td>DVI、HDMI<br />乙太網/無線，<br /> 4xUSB</td>
   <td>
    <ul>
     <li>4個或更多內容區域，同時播放視訊</li>
     <li>多頁互動式</li>
     <li>多來源資料觸發器</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

---
title: 與AEM Screens玩家合作
seo-title: Working with Screens Player
description: 按此頁瞭解Screens Player。 它還說明了Admin UI和Channel Switcher。
seo-description: Follow this page to learn about Screens Player. It also explains the Admin UI and the Channel Switcher.
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4faac090-ad8a-4d7e-a502-6fb63f6b2761
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 1%

---

# 與AEM Screens玩家合作 {#working-with-aem-screens-player}

您可以管理AEM Screens播放器上的頻道內容和其他設定。

>[!NOTE]
>
>按 ***Ctrl+Cmd+F*** 退出OS XAEM Screens播放器的全屏模式。

一旦為顯示器分配了頻道，AEM Screens播放器就會顯示內容。 可以使用管理員UI的首選項（從儀表板）或播放器本身配置播放器的設定。

## 使用設備儀表板 {#using-the-device-dashboard}

可以從「設備儀表板」配置設備的首選項，可通過創作實例AEM訪問。

1. 從項目導航到設備儀表板，例如， ***Test項目*** —> ***設備***。

   選擇 **設備** 和 **設備管理器** 按鈕。

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. 按一下設備以開啟設備儀表板。

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. 檢查 **首選項** 的子菜單。 您可以啟用/禁用 **管理員UI** 和 **通道切換器** 你的玩家。

   ![chlimage_1-68](assets/chlimage_1-68.png)

### 管理員UI {#the-admin-ui}

啟用 **管理員UI** 從「首選項」面板中，用戶可以從「螢幕播放器」開啟管理設定。 此外，如果從設備儀表板禁用此選項，則用戶無法從播放器開啟管理員UI。

要從螢幕播放器查看管理員UI，請在左上角按長時間以開啟「管理員」菜單、啟用觸摸的AEM Screens播放器或使用滑鼠。 在註冊完成後顯示資訊，並載入通道。

>[!NOTE]
>
>此外，您還可以查看AEM ScreensPlayer應用程式的正常運行時間，以檢查應用程式運行狀況。

![chlimage_1-3](assets/chlimage_1-3.gif)

#### 訪問配置菜單選項 {#configuration-options}

如果選擇 **配置** 選項，如下圖所示：

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

「配置」菜單允許您修改以下設定：

* 重置 **韌體**。 **首選項**&#x200B;或 **到工廠** 的子菜單。

* 指定要保留的AEM Screens播放器的最大日誌檔案數 **Max No. 保留的日誌檔案**。

* 啟用或禁用 **管理菜單**。 **通道切換器**, **活動UI** 螢幕播放器。

   如果 **活動UI** 從 **配置** 菜單，AEM Screens播放器顯示 *玩家活動通知* 右上角，如下圖所示。

   ![影像](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>的 **更新韌體** 選項僅在cordova上有效，如Android播放器。

>[!NOTE]
>
>建議 **管理員UI** 在生產部署中禁用。

#### 訪問內容快取菜單選項 {#content-cache-options}

可以從AEM Screens播放器的管理UI中清除通道和應用程式的快取。

選擇 **內容快取** 以更新快取。

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### 頻道切換器 {#the-channel-switcher}

啟用 **通道切換器** 從「首選項」面板中，用戶可以從「螢幕播放器」開啟頻道選擇/設定。

此外，如果從設備儀表板禁用此選項，則用戶無法控制螢幕播放器中的頻道首選項。

可以從螢幕播放器切換和控制頻道設定。

要從播放器查看頻道切換器，請長按左下角以開啟允許切換頻道和其他功能的頻道切換器。

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>您也可以從螢幕播放器中啟用或禁用播放器的管理菜單和頻道切換器。
>
>(請參閱 *從螢幕播放器更改首選項* 如下節所述)。

### 管理AEM Screens播放器的首選項 {#managing-preferences-from-the-aem-screens-player}

您也可以從播放器本身更改管理UI和頻道切換器的設定。

按照以下步驟更改播放器的首選項：

1. 按空閒通道左上角的長鍵以開啟管理面板。
1. 導航到 **配置** 按鈕。
1. 啟用/禁用配置 **管理員UI** 或 **通道切換器**。

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## 診斷AEM Screens播放器 {#troubleshooting-aem-screens-player}

您可以解決與AEM Screens播放器（硬體和軟體）相關的各種問題：

| **問題** | **建議** |
|---|---|
| 播放器儲存已滿 | 消除不必要的檔案 |
| 播放器丟失網路 | 使用Cat-5/Cat-6電纜。 對於wifi，減少從路由器到播放器設備的距離 |
| AEM Screens球員 | 建議使用一個監視應用程式，確保AEM Screens播放器始終運行 |
| AEM Screens播放器丟失設定 | 檢查與伺服器的AEM連接 |
| AEM Screens播放器在播放器重新啟動/重新啟動後不自動啟動 | 檢查作業系統啟動資料夾或初始化過程 |
| AEM Screens播放器顯示錯誤/舊內容 | 檢查網路連接 |

### AEM Screens播放器更新 {#updates-for-aem-screens-player}

AEM Screens播放器有兩種更新類型：

| **方法** | **詳細資料** | **通過遠程** | **自動化** | **0停機時間** |
|---|---|---|---|---|
| 韌體更新 | 通過遠程命令應用於現有已安裝的播放器。 更新後，播放器將自動重新載入現有內容。 | 是 | 自訂 | 快 — 1-3秒 |
| 播放器Shell更新 | 這是要部署在播放器上的新執行檔。 這要求遠程複製播放器上的新二進位檔案，並停止當前正在運行並啟動新版本。 這可能需要重新下載包的預載入。 | 是（通過遠程外殼） | 自訂 | 否 |

## 播放器設備的硬體選擇指南 {#hardware-selection-guidelines-for-player-device}

以下部分提供了螢幕項目的硬體選擇指南：

* 始終源 ***商業*** 或 ***工業*** PC播放器和顯示面板或投影儀的等級元件。

* 始終與為數字標牌市場服務的供應商接洽。
* 始終考慮環境因素，如環境溫度和相對濕度。
* 始終查看電源要求和電源調節。
* 仔細審查應用程式所需的效能需求和I/O埠。

下表概述了AEM Screens項目的硬體配置和典型使用案例：

<table>
 <tbody>
  <tr>
   <td>播放器配置</td>
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
   <td><p>·ChromeOS 32 GB</p> <p>·Windows 128GB</p> </td>
   <td>板載</td>
   <td>1920x1080</td>
   <td>DVI、<br /> 乙太網/無線<br /> 2個USB</td>
   <td>
    <ul>
     <li>標準全屏循環<br /> </li>
     <li>日分</li>
    </ul> </td>
  </tr>
  <tr>
   <td>標準</td>
   <td>四核英特爾®酷睿i5處理器</td>
   <td><p>8 GB記憶體</p> <p>4 MB快取</p> </td>
   <td>小行星128</td>
   <td>板載</td>
   <td>3840x2160(4K)</td>
   <td>DVI、HDMI<br /> 乙太網/無線<br /> 2個USB</td>
   <td>
    <ul>
     <li>單源動態內容</li>
     <li>簡單交互</li>
     <li>1-3區域佈局</li>
    </ul> </td>
  </tr>
  <tr>
   <td>進階</td>
   <td>四核超線程，英特爾®酷睿i7處理器</td>
   <td><p>16GB記憶體</p> <p>8 MB快取</p> </td>
   <td>256 GB</td>
   <td>專用圖形GPU</td>
   <td>3840x2160(4K)</td>
   <td>DVI、HDMI<br /> 乙太網/無線<br /> 4個USB</td>
   <td>
    <ul>
     <li>4個或更多內容區域，並行視頻播放</li>
     <li>多頁互動式</li>
     <li>多源資料觸發器</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

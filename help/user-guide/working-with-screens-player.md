---
title: 使用AEM Screens Player
description: 瞭解如何使用AEM Screens Player、管理員UI和管道切換器。
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4faac090-ad8a-4d7e-a502-6fb63f6b2761
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 1%

---

# 使用AEM Screens Player

您可以在AEM Screens Player上管理頻道內容和其他設定。

>[!NOTE]
>
>按下 ***Ctrl+Cmd+F*** 因此您可以結束OS X AEM Screens Player的全熒幕模式。

將管道指派給顯示區後，AEM Screens Player就會顯示內容。 您可以使用管理員UI的偏好設定（從控制面板）或播放器本身來設定播放器的設定。

## 使用裝置控制面板 {#using-the-device-dashboard}

您可以從裝置控制面板設定裝置的偏好設定，您可以透過AEM編寫執行個體來存取。

1. 從您的專案導覽至裝置控制面板，例如 ***測試專案*** > ***裝置***.

   按一下 **裝置** 和 **裝置管理員** 從動作列移除。

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. 按一下裝置，即可開啟裝置控制面板。

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. 檢查 **偏好設定** 面板。 您可以啟用或停用 **管理員UI** 和 **頻道切換器** 這兩個選項可為您的播放器提供。

   ![chlimage_1-68](assets/chlimage_1-68.png)

### 管理員UI {#the-admin-ui}

啟用 **管理員UI** 從偏好設定面板中，允許使用者從Screens播放器開啟管理員設定。 此外，如果您從裝置控制面板停用此選項，使用者將無法從播放器開啟Admin UI 。

若要從Screens播放器檢視Admin UI，請在觸控式AEM Screens播放器上按一下左上角以開啟Admin功能表，或使用滑鼠來開啟。 完成註冊並載入通道後，資訊便會顯示。

>[!NOTE]
>
>您也可以檢視AEM Screens Player應用程式運作時間，以檢查應用程式運作狀態。

![chlimage_1-3](assets/chlimage_1-3.gif)

#### 存取組態功能表選項 {#configuration-options}

您可以更新您的設定，如果您按一下 **設定** 側選單中的選項，如下圖所示：

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

「組態」功能表可讓您修改下列設定：

* 重設 **韌體**， **偏好設定**，或 **到工廠** 在此對話方塊中。

* 指定您要為AEM Screens Player保留的記錄檔數目上限 **最大數量 要保留的記錄檔**.

* 啟用或停用 **管理功能表**， **頻道切換器**、和 **活動UI** 用於Screens播放器。

  如果 **活動UI** 啟用於 **設定** 功能表，AEM Screens Player會顯示 *播放器活動通知* 位於播放器右上角，如下圖所示。

  ![影像](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>此 **更新韌體** 選項僅適用於Cordova，例如Android™播放器。

>[!NOTE]
>
>建議 **管理員UI** 在生產部署中停用。

#### 存取內容快取功能表選項 {#content-cache-options}

您可以從AEM Screens Player的管理員UI中清除管道和應用程式的快取。

按一下 **內容快取** 以更新快取。

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### 頻道切換器 {#the-channel-switcher}

啟用 **頻道切換器** 從「偏好設定」面板中，使用者可從Screens播放器開啟頻道選取設定。

此外，如果您從裝置儀表板停用此選項，使用者將無法從Screens播放器控制頻道偏好設定。

您可以從Screens播放器切換並控制頻道的設定。

若要從播放器檢視頻道切換程式，請長按左下角，開啟可切換頻道和其他功能的頻道切換程式。

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>您也可以從Screens播放器啟用或停用播放器的管理功能表及頻道切換器。
>
>(請參閱 *從Screens播放器變更偏好設定* （如下節所述）。

### 從AEM Screens播放器管理偏好設定

您也可以從播放器本身變更管理員UI和頻道切換器的設定。

若要變更播放器的偏好設定：

1. 長按閒置頻道左上角以開啟「管理」面板。
1. 瀏覽至 **設定** 從左側動作功能表。
1. 啟用或停用設定 **管理員UI** 或 **頻道切換器**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## 疑難排解AEM Screens Player

您可以針對AEM Screens Player （硬體和軟體）相關的各種問題進行疑難排解：

| **問題** | **Recommendations** |
|---|---|
| 播放器儲存空間已滿 | 消除不必要的檔案 |
| 播放器網路中斷 | 使用Cat-5或Cat-6纜。 若使用Wifi，請縮短路由器與播放器裝置的距離 |
| AEM Screens Player當機 | 建議使用監視程式應用程式，以確保AEM Screens Player一律執行 |
| AEM Screens Player遺失設定 | 檢查與AEM伺服器的連線 |
| AEM Screens Player不會在播放器重新啟動或重新開機後自動啟動 | 檢查作業系統啟動資料夾或初始化程式 |
| AEM Screens Player顯示錯誤或舊內容 | 檢查網路連線 |

### AEM Screens Player更新

AEM Screens Player有兩種型別的更新：

| **方法** | **詳細資料** | **經由遠端** | **自動化** | **0停機時間** |
|---|---|---|---|---|
| 韌體更新 | 透過遠端指令套用至現有的已安裝播放器。 更新後，播放器會自動重新載入現有的內容。 | 是 | 自訂 | 幾乎 — 1-3秒 |
| 播放器殼層更新 | 部署在播放器上的新可執行檔。 此功能需要您在播放器上遠端複製新的二進位檔，並停止目前執行的專案，然後啟動新版本。 它可能需要再次下載套件的預先載入。 | 是（透過遠端shell） | 自訂 | 否 |

## 播放器裝置的硬體選擇准則 {#hardware-selection-guidelines-for-player-device}

下節提供Screens專案的硬體選擇准則：

* 永遠來源 ***商業*** 或 ***工業*** PC播放器及顯示面板或投影機的等級元件。

* 永遠與數位看板市場的供應商互動。
* 請務必考量環境因素，例如環境溫度和相對濕度。
* 請務必檢閱電源需求與電源調節。
* 請仔細檢閱應用程式所需的效能需求和I/O連線埠。

下表概述AEM Screens專案的硬體組態與典型使用案例：

<table>
 <tbody>
  <tr>
   <td>播放器設定</td>
   <td>處理器</td>
   <td>記憶體</td>
   <td>儲存固態硬碟</td>
   <td>GPU</td>
   <td>顯示區</td>
   <td>I/O</td>
   <td>典型使用案例</td>
  </tr>
  <tr>
   <td>基本</td>
   <td>雙核心、i3或入門級四核心Intel® Atom處理器</td>
   <td><p>4 GB記憶體</p> <p>2 MB快取</p> </td>
   <td><p>*ChromeOS 32 GB</p> <p>*Windows 128 GB</p> </td>
   <td>主機板</td>
   <td>1920 x 1080</td>
   <td>DVI<br /> 乙太網路/無線<br /> 2個USB</td>
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

---
title: 使用AEM Screens Player
seo-title: 使用Screens Player
description: 請依照本頁來瞭解Screens Player。 此外，還說明管理員UI和頻道切換器。
seo-description: 請依照本頁來瞭解Screens Player。 此外，還說明管理員UI和頻道切換器。
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
translation-type: tm+mt
source-git-commit: 5aea3e032cc5279de7f3abab679825aa2794a89e
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 1%

---


# 使用AEM Screens Player {#working-with-aem-screens-player}

您可以管理AEM Screens Player上的頻道內容和其他設定。

>[!NOTE]
>
>按 ***Ctrl+Cmd+F*** ，以退出OS X AEM Screens Player的全螢幕模式。

在您將頻道指派給顯示器後，AEM Screens Player會顯示內容。 您可以使用管理員UI的偏好設定（從控制面板）或從播放器本身設定您的播放器設定。

## 使用裝置儀表板 {#using-the-device-dashboard}

您可以從「裝置儀表板」（可透過AEM製作例項存取）設定裝置的偏好設定。

1. 從您的專案導覽至裝置控制面板，例如 ***Test Project*** —>裝 ***置***。

   從操 **作欄中** ，選 **擇「設備和設備管理器** 」。

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. 按一下裝置以開啟裝置控制面板。

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. 檢查「首 **選項** 」面板。 您可以從這兩個選項 **啟用／停用您播** 放器的管理UI **** 和頻道切換器。

   ![chlimage_1-68](assets/chlimage_1-68.png)

### 管理員UI {#the-admin-ui}

從偏好 **設定面板啟用** 「管理員UI」可讓使用者從「畫面播放器」開啟管理員設定。 此外，如果您在裝置儀表板中停用此選項，使用者便無法從播放器開啟管理員UI。

若要從「螢幕」播放器檢視管理員UI，請長按左上角的長按鍵以開啟「管理」功能表、啟用觸控功能的AEM Screens播放器，或使用滑鼠。 它會在註冊完成並載入頻道後顯示資訊。

>[!NOTE]
>
>此外，您還可以檢視AEM Screens Player應用程式的正常運作時間，以檢查應用程式的狀況。

![chlimage_1-3](assets/chlimage_1-3.gif)

#### 訪問配置菜單選項 {#configuration-options}

如果從側面菜單中選擇「配置」( **Configuration** )選項，則可以更新配置，如下圖所示：

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

「配置」菜單允許您修改以下設定：

* 從此 **對話框重置**「韌體」、「首選項 **」**&#x200B;或「至工廠 **** 」。

* 指定AEM Screens播放器在「最大編號」中保留的最大記錄 **檔數。 要保存的日誌檔案**。

* 啟用或停用 **Screens播放器的**「管理 **功能表」**、「頻道切換器」 **和「活動UI** 」。

   如果從「 **設定」選單啟用「活動UI** 」,AEM Screens播放器會在播放器的右上角顯示 ****** player活動通知，如下圖所示。

   ![影像](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>「更 **新韌體** 」選項僅適用於cordova，例如Android播放器。

>[!NOTE]
>
>建議在「生產部 **署」中停用** 「管理員UI」。

#### 存取內容快取功能表選項 {#content-cache-options}

您可從AEM Screens播放器的「管理員UI」中，清除頻道和應用程式的快取。

從側邊 **欄選取「內容快取** 」，以更新快取。

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### 頻道切換器 {#the-channel-switcher}

從偏好 **設定面板啟用頻道切換器** ，可讓使用者從「畫面播放器」開啟頻道選擇／設定。

此外，如果您從裝置儀表板停用此選項，使用者將無法從Screens Player控制頻道偏好設定。

您可以從Screens Player切換並控制頻道的設定。

若要從播放器檢視頻道切換器，請長按左下角的以開啟頻道切換器，讓您切換頻道和其他功能。

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>您也可以從「畫面播放器」啟用或停用播放器的管理功能表和頻道切換器。
>
>(請參 *閱以下章節中提及的* 「從畫面播放器變更偏好設定」)。

### 從AEM Screens Player管理偏好設定 {#managing-preferences-from-the-aem-screens-player}

您也可以從播放器本身變更管理UI和頻道切換器的設定。

請依照下列步驟，從您的播放器變更偏好設定：

1. 長按閒置頻道左上角的，以開啟管理面板。
1. 從左側 **操作菜單** ，導航至「配置」。
1. 啟用／停用管理UI或 **頻道切換器****的設定**。

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## 疑難排解AEM Screens Player {#troubleshooting-aem-screens-player}

您可以疑難排解與AEM Screens Player（硬體和軟體）相關的各種問題：

| **問題** | **建議** |
|---|---|
| 播放器儲存空間已滿 | 消除不必要的檔案 |
| 播放器失去網路 | 使用5類/6類電纜。 對於wifi，請減少路由器到播放器設備的距離 |
| AEM Screens Player當機 | 建議您使用監視程式應用程式，以確保AEM Screens Player一律執行 |
| AEM Screens Player遺失設定 | 檢查與AEM伺服器的連線 |
| AEM Screens Player在播放器重新啟動／重新啟動後不會自動啟動 | 檢查作業系統啟動資料夾或初始化過程 |
| AEM Screens Player顯示錯誤／舊內容 | 檢查網路連接 |

### AEM Screens Player的更新 {#updates-for-aem-screens-player}

AEM Screens Player有兩種更新類型：

| **方法** | **詳細資料** | **透過遠端** | **自動化** | **0停機時間** |
|---|---|---|---|---|
| 韌體更新 | 已透過遠端命令套用至現有已安裝的播放器。 更新後，播放器會自動重新載入現有內容。 | 是 | 自訂 | 近- 1-3秒 |
| 播放器殼層更新 | 這是要部署在播放器上的新可執行檔。 這需要遠端複製播放器上的新二進位檔，並停止目前執行中的程式碼，然後啟動新版本。 這可能需要重新下載預載的套件。 | 是（通過遠程外殼） | 自訂 | 否 |

## 播放器裝置的硬體選擇指南 {#hardware-selection-guidelines-for-player-device}

下節提供畫面專案的硬體選擇指南：

* 請務必 ***為PC播放********* 器和顯示面板或投影儀提供商業級或工業級元件。

* 與為數位標牌市場服務的廠商永遠互動。
* 始終考慮環境因素，如環境溫度和相對濕度。
* 請隨時查看電源要求和電源調節。
* 仔細審查應用程式所需的效能需求和I/O埠。

下表摘要了AEM Screens專案的硬體組態及一般使用案例：

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
   <td><p>·ChromeOS 32 GB</p> <p>·Windows 128GB</p> </td>
   <td>OnBoard</td>
   <td>1920x1080</td>
   <td>DVI，乙太網<br /> /無線，<br /> 2個USB</td>
   <td>
    <ul>
     <li>標準全螢幕循環<br /> </li>
     <li>日分割</li>
    </ul> </td>
  </tr>
  <tr>
   <td>標準</td>
   <td>四核、英特爾®酷睿i5處理器</td>
   <td><p>8GB記憶體</p> <p>4MB快取</p> </td>
   <td>128 GBB</td>
   <td>OnBoard</td>
   <td>3840x2160(4K)</td>
   <td>DVI、HDMI<br /> 乙太網／無線<br /> 、2個USB</td>
   <td>
    <ul>
     <li>單一來源動態內容</li>
     <li>簡單的互動功能</li>
     <li>1-3個區域佈局</li>
    </ul> </td>
  </tr>
  <tr>
   <td>進階</td>
   <td>四核超線程，英特爾®酷睿i7處理器</td>
   <td><p>16GB的記憶體</p> <p>8MB快取</p> </td>
   <td>256 GB</td>
   <td>專用圖形GPU</td>
   <td>3840x2160(4K)</td>
   <td>DVI、HDMI<br /> 乙太網／無線<br /> 4個USB</td>
   <td>
    <ul>
     <li>4個或多個內容區域，並行視訊播放</li>
     <li>多頁互動</li>
     <li>多來源資料觸發器</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

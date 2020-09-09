---
title: 設備控制中心故障排除
seo-title: 監控畫面
description: 請依照本頁，使用「裝置」控制面板來監視和疑難排解Screens播放器活動和裝置的效能。
seo-description: 請依照本頁，使用「裝置」控制面板來監視和疑難排解Screens播放器活動和裝置的效能。
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 2%

---


# 設備控制中心故障排除 {#troubleshooting-device-control-center}

您可以使用「裝置」控制面板來監視和疑難排解螢幕播放器活動與裝置的效能。 本頁提供如何監視和疑難排解Screens播放器和已指派裝置的效能問題的資訊。

## 從設備控制中心監視和故障排除 {#monitor-and-troubleshoot-from-device-control-center}

您可以使用「裝置儀表板」來監視活動，並因此疑難排解您的Screens播放器。

### 裝置儀表板 {#device-dashboard}

請依照下列步驟導覽至裝置控制面板：

1. 從您的專案導覽至裝置控制面板，例如 ***Test Project*** —>裝 ***置***。

   從操 **作欄中** ，選 **擇「設備和設備管理器** 」。

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 清單顯示已分配和未分配的設備，如下圖所示。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. 選取裝置(**NewTestDevice**)，然後從動作列按 **一下「儀表板** 」。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. 該頁顯示設備資訊、活動和設備詳細資訊，允許您監視設備活動和功能。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### 監視設備活動 {#monitor-device-activity}

「活 **動** 」面板會顯示畫面播放器的上次ping及時間戳記。 最後一個ping命令與設備上次聯繫伺服器的時間相對應。

![chlimage_1](assets/chlimage_1.png)

此外，按一 **下「活動****** 」面板右上角的「收集記錄檔」，以檢視您播放器的記錄檔。

### 更新裝置詳細資訊 {#update-device-details}

檢查「 **Device Details** （裝置詳細資訊）」面板，以檢視裝置的IP、儲存空間使用情況、韌體版本，以及播放器的正常運作時間。

![chlimage_1-1](assets/chlimage_1-1.png)

此外，按一下 **清除快取** 和 **更新** ，分別清除設備的快取和更新 [](screens-glossary.md) 韌體版本。

此外，按一下 **...** 從「裝置詳細資訊」面板的右上角 **重新啟動** ，或重新整理您播放器的狀態。

![chlimage_1-2](assets/chlimage_1-2.png)

### 更新裝置資訊 {#update-device-information}

檢查 **DEVICE INFORMATION** （裝置資訊）面板，以檢視組態更新、裝置型號、裝置作業系統和殼層資訊。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

此外，按一&#x200B;**下「裝置資訊」面板右上角的**(...)以檢視屬性或更新裝置。

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

按一下 **屬性** ，查看設 **** 備屬性對話框。 您可以編輯裝置標題，或選擇「手動」或「自動」的 **配置更** 新 **選項**。

>[!NOTE]
>
>若要進一步瞭解與裝置自動或手動更新相關的事件，請參閱「管理頻道」中「裝置儀表板」的「自動與手動更新 ***」*** 一節 [](managing-channels.md)。

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### 檢視播放器螢幕擷取 {#view-player-screenshot}

您可從「播放器螢幕擷取」面板中，從裝置檢 **視播放器螢幕擷取** 。

按一下「播&#x200B;**放器螢幕擷取」面板右上角的(...**)，並選取「重新整理螢幕擷取 **** 」以檢視執行中播放器的快照。

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 管理偏好設定 {#manage-preferences}

PREFERENCES **** (偏好設定 **)面板可讓使用者變更** Admin UI **、** Channel Switcher **，以及裝置的** 遠端除錯偏好設定。

>[!NOTE]
>若要進一步瞭解這些選項，請參閱「 [AEM Screens Player](working-with-screens-player.md)」。

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

此外，按一 **下右上角的** 「設定」，以更新裝置偏好設定。 您可以更新下列偏好設定：

* **伺服器 URL**
* **解析度**
* **重新開機排程**
* **Max No. 要保存的日誌檔案**
* **記錄層級**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>您可以選取下列任一「記錄檔」層級：
>* **停用**
>* **偵錯**
>* **資訊**
>* **警告**
>* **錯誤**


![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## 疑難排解OSGi設定 {#troubleshoot-osgi-settings}

您必須啟用空的反向連結，以允許裝置將資料張貼至伺服器。 例如，如果停用空的反向連結屬性，裝置就無法將螢幕擷取張貼回去。

目前，部分功能僅在OSGi組態中啟用 *Apache Sling Referrer Filter Allow Empty* 時才可用。 控制面板可能會顯示警告，指出安全性設定可能會使部分功能無法運作。

請依照下列步驟來啟用Apache Sling Referrer Filter Allow Empty

1. 導覽至 **Adobe Experience Manager Web Console設定**，即 `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`。
1. 選中 **allow.empty選項** 。
1. 按一下&#x200B;**「儲存」**。

![chlimage_1-3](assets/chlimage_1-3.png)

### 建議 {#recommendations}

下節建議監控網路連結、伺服器和播放器，以瞭解運作狀況並回應問題。

AEM提供內建的監控功能：

* *心率* （每5秒），以指出AEM Screens Player已運作。
* *來自* Player的螢幕擷取，顯示Player中目前顯示的內容。
* Player上 *安裝的AEM Screens Player Firmware* version。
* *Player上的可用儲存空間* 。

使用第三方軟體進行遠程監控的建議：

* 播放器上的CPU使用量。
* 檢查AEM Screens Player程式是否正在執行。
* Player的遠程重啟／重新啟動。
* 即時通知。

建議您部署Player硬體和作業系統，讓遠端登入可診斷問題並重新啟動Player。

#### 其他資源 {#additional-resources}

請參 [閱視訊播放設定和疑難排解](troubleshoot-videos.md) ，以除錯和疑難排解頻道中播放的視訊。

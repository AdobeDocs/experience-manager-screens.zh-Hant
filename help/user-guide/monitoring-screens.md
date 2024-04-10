---
title: 裝置控制中心的故障排除
description: 了解如何使用设备儀表板監視AEM Screens播放器活動和裝置的性能並對其進行故障排除。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 1%

---

# 疑難排解裝置控制中心 {#troubleshooting-device-control-center}

您可以使用裝置控制面板，監控及疑難排解AEM Screens播放器活動和裝置的效能。 此頁面提供如何監視和疑難排解Screens播放器和指派之裝置的感知效能問題的相關資訊。

## 從設備控制中心進行監控和故障排除 {#monitor-and-troubleshoot-from-device-control-center}

您可以使用设备儀表板監視活動，從而對AEM Screens播放器進行故障排除。

### 裝置控制面板 {#device-dashboard}

請按照以下步驟導航到 裝置 控制面板：

1. 從項目導航到裝置儀錶板，例如「 ***測試專案*** > ***設備***」。。

   從操作列中選擇&#x200B;**設備和****設備管理員**。

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 清單會顯示已指派和未指派的裝置，如下圖所示。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. 選取裝置(**NewTestDevice**)並按一下 **儀表板** 從動作列移除。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. 此頁面會顯示裝置資訊、活動，以及可讓您監視裝置活動和功能的裝置詳細資訊。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### 監視裝置活動 {#monitor-device-activity}

此 **活動** 面板會顯示您的AEM Screens播放器最後一次ping的時間戳記。 最後一個ping對應到裝置上次連線伺服器的時間。

![chlimage_1](assets/chlimage_1.png)

此外，從“**活動**”面板的右上角選擇&#x200B;**“收集日誌**”以視圖播放機的日誌。

### 更新裝置詳細數據 {#update-device-details}

檢查设备 **詳細信息** 面板，以便您可以視圖裝置 IP、存儲使用方式、固件版本和裝置播放機正常運行時間。

![chlimage_1-1](assets/chlimage_1-1.png)

另外，選取 **清除快取** 和 **更新** 以清除裝置的快取並更新 [韌體](screens-glossary.md) 版本。

另外，選取 **...** 從右上角 **裝置詳細資料** 面板以重新啟動或重新整理播放器的狀態。

![chlimage_1-2](assets/chlimage_1-2.png)

### 更新裝置資訊 {#update-device-information}

檢查設備 **資訊** 面板。 您可以在此處視圖配置更新、裝置型号、裝置 OS 和 shell 信息。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

此外，從“设备信息”面板的右上角選擇 （**...**） 以視圖屬性或更新裝置。

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

選取 **屬性** 以便您檢視 **裝置屬性** 對話方塊。 您可以編輯裝置標題或選擇設定更新的選項，如下所示 **手動** 或 **自動**.

>[!NOTE]
>
>若要進一步瞭解與裝置的自動或手動更新相關聯的事件，請參閱區段 ***從裝置控制面板自動與手動更新*** 在 [管理管道](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### 檢視播放器熒幕擷圖 {#view-player-screenshot}

您可以從裝置檢視播放器熒幕擷圖 **播放器熒幕擷圖** 面板。

按一下(**...**)，並選取「 」 **重新整理熒幕擷圖** 以檢視執行中播放器的快照。

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 管理偏好設定 {#manage-preferences}

此 **偏好設定** 面板可讓使用者變更的偏好設定 **管理員UI**， **頻道切換器**、和 **遠端偵錯** 適用於裝置。

>[!NOTE]
>要瞭解有關這些選項的詳細資訊，請參閱 [AEM Screens播放機](working-with-screens-player.md)。

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

另外，選取 **設定** 從右上角更新裝置偏好設定。 您可以更新下列偏好設定：

* **伺服器URL**
* **解析度**
* **重新啟動排程**
* **最大數量 要保留的記錄檔**
* **記錄層級**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>您可以選取下列任一「記錄」層次：
>* **停用**
>* **偵錯**
>* **資訊**
>* **警告**
>* **錯誤**

![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## 疑難解答 OSGi 設定 {#troubleshoot-osgi-settings}

啟用空推薦者以允許裝置將数据貼文到伺服器。 例如，如果停用空白反向連結屬性，裝置就無法張貼熒幕擷圖。

目前，其中部分功能僅適用於 *Apache Sling查閱者篩選器允許空白* 會在OSGi設定中啟用。 儀表板可能會顯示警告，指出安全性設定可能會使這些功能的部分功能無法運作。

請依照下列步驟，啟用Apache Sling查閱者篩選器允許空白

1. 導航到 **Adobe Experience Manager Web 控制台配置**，即 `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`。
1. **勾選allow.empty** 選項。
1. 按一下「**儲存**」。

![chlimage_1-3](assets/chlimage_1-3.png)

### 建議 {#recommendations}

以下部分建議監視網路連結、伺服器和播放機，以瞭解運行狀況並對問題做出反應。

AEM提供下列專案的內建監控：

* *心率* 每5秒顯示一次，表示AEM Screens Player運作中。
* *熒幕擷圖* 從「播放器」，顯示在播放器上顯示的內容。
* 此 *AEM Screens播放器韌體* 版本已安裝在播放器上。
* *可用儲存空間* 在播放器上。

使用協力廠商軟體進行遠端監控的Recommendations：

* 播放器上的CPU使用量。
* 檢查AEM Screens Player程式是否正在執行。
* 遠端重新啟動/重新啟動播放器。
* 即時通知。

建議以可讓遠端登入診斷問題並重新啟動播放器的方式，部署播放器硬體及作業系統。

#### 其他資源 {#additional-resources}

如果您想偵錯和疑難解答在通道播放的視頻，請參閱 [影片播放配置和疑難解答](troubleshoot-videos.md) 。

---
title: 設備控制中心故障排除
seo-title: Monitoring Screens
description: 按照本頁，使用「設備」儀表板監視螢幕播放器活動和設備的效能並排除故障。
seo-description: Follow this page to monitor and troubleshoot performance for your Screens player activity and device usingtheDevice dashboard.
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 2%

---

# 設備控制中心故障排除 {#troubleshooting-device-control-center}

您可以使用「設備」儀表板監視螢幕播放器活動和設備的效能並排除故障。 此頁提供有關如何監視和解決螢幕播放器和已分配設備的效能問題的資訊。

## 從設備控制中心進行監視和故障診斷 {#monitor-and-troubleshoot-from-device-control-center}

您可以監視活動，並因此使用設備儀表板對螢幕播放器進行故障排除。

### 設備儀表板 {#device-dashboard}

按照以下步驟導航到設備儀表板：

1. 從項目導航到設備儀表板，例如， ***Test項目*** —> ***設備***。

   選擇 **設備** 和 **設備管理器** 按鈕。

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 該清單顯示已分配和未分配的設備，如下圖所示。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. 選擇設備(**新測試設備**) **儀表板** 按鈕。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. 該頁顯示設備資訊、活動和設備詳細資訊，這些資訊允許您監視設備活動和功能。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### 監視設備活動 {#monitor-device-activity}

的 **活動** 面板顯示螢幕播放器的最後一個ping命令，並帶有時間戳。 上次ping對應於設備上次聯繫伺服器的時間。

![chlimage_1](assets/chlimage_1.png)

此外，按一下 **收集日誌** 從右上角 **活動** 的子菜單。

### 更新設備詳細資訊 {#update-device-details}

檢查 **設備詳細資訊** 查看設備IP、儲存使用情況、韌體版本和播放器正常運行時間的面板。

![chlimage_1-1](assets/chlimage_1-1.png)

此外，按一下 **清除快取** 和 **更新** 清除設備的快取並更新 [韌體](screens-glossary.md) 版本。

另外，按一下 **...** 從右上角 **設備詳細資訊** 面板，以重新啟動或刷新播放器的狀態。

![chlimage_1-2](assets/chlimage_1-2.png)

### 更新設備資訊 {#update-device-information}

檢查 **設備資訊** 查看配置更新、設備型號、設備OS和shell資訊的面板。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

另外，按一下&#x200B;**...**)，查看屬性或更新設備。

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

按一下 **屬性** 的 **設備屬性** 對話框。 您可以編輯設備標題或選擇配置更新選項作為 **手動** 或 **自動**。

>[!NOTE]
>
>要瞭解有關與設備自動或手動更新相關的事件的詳細資訊，請參閱一節 ***從設備儀表板自動更新與手動更新*** 在 [管理渠道](managing-channels.md)。

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### 查看播放器螢幕快照 {#view-player-screenshot}

您可以從以下位置查看設備的播放器螢幕快照： **播放器螢幕截圖** 的子菜單。

按一下(**...**)，然後選擇 **刷新螢幕截圖** 查看正在運行的播放器的快照。

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 管理首選項 {#manage-preferences}

的 **首選項** 面板允許用戶更改首選項 **管理員UI**。 **通道切換器**, **遠程調試** 設備。

>[!NOTE]
>要瞭解有關這些選項的詳細資訊，請參閱 [AEM Screens選手](working-with-screens-player.md)。

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

此外，按一下 **設定** 從右上角更新設備首選項。 您可以更新以下首選項：

* **伺服器 URL**
* **解析度**
* **重新開機排程**
* **Max No. 保留的日誌檔案**
* **記錄層級**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>您可以選擇以下任一日誌級別：
>* **停用**
>* **偵錯**
>* **資訊**
>* **警告**
>* **錯誤**


![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## 排除OSGi設定故障 {#troubleshoot-osgi-settings}

您需要啟用空引用程式以允許設備將資料發佈到伺服器。 例如，如果禁用了空引用器屬性，則設備無法將螢幕截圖發回。

目前，這些功能中的某些功能僅在 *Apache Sling引用篩選器允許空* 在OSGi配置中啟用。 儀表板可能顯示警告，安全設定可能會阻止某些功能正常工作。

按照以下步驟啟用Apache Sling引用過濾器允許空

1. 導航到 **Adobe Experience ManagerWeb控制台配置**&#x200B;就是， `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`。
1. 檢查 **allow.empty** 的雙曲餘切值。
1. 按一下「**儲存**」。

![chlimage_1-3](assets/chlimage_1-3.png)

### 建議 {#recommendations}

以下部分建議監視網路鏈路、伺服器和玩家，以瞭解運行狀況並對問題做出反應。

提AEM供內置監視：

* *心跳* 每5秒顯示AEM Screens播放器正在運行。
* *螢幕截圖* 顯示播放器上當前顯示的內容。
* 的 *AEM Screens播放器韌體* 版本。
* *可用儲存空間* 在播放器上。

Recommendations用於使用第三方軟體進行遠程監控：

* 播放器上的CPU使用率。
* 檢查AEM Screens播放器進程是否正在運行。
* 遠程重新啟動/重新啟動播放器。
* 即時通知。

建議以允許遠程登錄來診斷問題並重新啟動Player的方式部署Player硬體和作業系統。

#### 其他資源 {#additional-resources}

請參閱 [視頻播放配置和故障排除](troubleshoot-videos.md) 調試和排除在頻道播放的視頻。

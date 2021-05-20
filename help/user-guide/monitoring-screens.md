---
title: 疑難排解設備控制中心
seo-title: 監視畫面
description: 請依照本頁所述，使用「裝置」控制面板監視及疑難排解Screens播放器活動和裝置的效能。
seo-description: 請依照本頁所述，使用「裝置」控制面板監視及疑難排解Screens播放器活動和裝置的效能。
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
feature: 數位招牌、內容、播放器
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 2%

---

# 設備控制中心{#troubleshooting-device-control-center}故障排除

您可以使用「裝置」控制面板，監控及疑難排解Screens播放器活動和裝置的效能。 本頁提供如何監視和疑難排解Screens播放器和已指派裝置之效能問題的相關資訊。

## 從設備控制中心{#monitor-and-troubleshoot-from-device-control-center}進行監視和故障排除

您可以監控活動，因此請使用「裝置控制面板」疑難排解Screens播放器。

### 設備儀表板{#device-dashboard}

請依照下列步驟導覽至裝置控制面板：

1. 從您的專案導覽至裝置控制面板，例如&#x200B;***測試專案*** —> ***裝置***。

   從操作欄中選擇&#x200B;**設備**&#x200B;和&#x200B;**設備管理器**。

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 清單顯示已分配和未分配的設備，如下圖所示。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. 選擇設備(**NewTestDevice**)，然後從操作欄中按一下&#x200B;**儀表板**。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. 頁面會顯示裝置資訊、活動和裝置詳細資訊，讓您監控裝置活動和功能。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### 監視設備活動{#monitor-device-activity}

**Activity**&#x200B;面板會顯示螢幕播放器上次偵測時間戳記的情形。 上次Ping對應於設備上次與伺服器聯繫的時間。

![chlimage_1](assets/chlimage_1.png)

此外，按一下&#x200B;**Activity**&#x200B;面板右上角的&#x200B;**收集記錄檔**&#x200B;以檢視您播放器的記錄檔。

### 更新設備詳細資訊{#update-device-details}

檢查&#x200B;**設備詳細資訊**&#x200B;面板，查看設備的設備IP、儲存使用情況、韌體版本和播放器正常運行時間。

![chlimage_1-1](assets/chlimage_1-1.png)

此外，按一下「**清除快取**」和「**更新**」以清除設備的快取，並從此面板分別更新[韌體](screens-glossary.md)版本。

此外，按一下&#x200B;**...**&#x200B;裝置詳細資料&#x200B;**面板右上角的**，重新開始或重新整理播放器狀態。

![chlimage_1-2](assets/chlimage_1-2.png)

### 更新設備資訊{#update-device-information}

檢查&#x200B;**DEVICE INFORMATION**&#x200B;面板，查看配置更新、設備型號、設備作業系統和外殼資訊。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

此外，按一下(**...**)，以檢視屬性或更新裝置。

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

按一下「**屬性**」以查看「設備屬性&#x200B;**」對話框。**&#x200B;您可以編輯設備標題或選擇配置更新選項，作為&#x200B;**Manual**&#x200B;或&#x200B;**Automatic**。

>[!NOTE]
>
>若要進一步了解與裝置自動或手動更新相關聯的事件，請參閱[管理管道](managing-channels.md)中「裝置控制面板」的&#x200B;***「自動與手動更新」一節。***

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### 檢視播放器螢幕截圖{#view-player-screenshot}

您可以從&#x200B;**播放器螢幕擷取**&#x200B;面板檢視裝置的播放器螢幕擷取。

按一下(**...**)，並選取&#x200B;**重新整理螢幕擷取**&#x200B;以檢視執行中播放器的快照。

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 管理首選項{#manage-preferences}

**PREFERENCES**&#x200B;面板可讓使用者變更裝置的&#x200B;**管理UI**、**通道切換器**&#x200B;和&#x200B;**遠端除錯**&#x200B;的偏好設定。

>[!NOTE]
>若要進一步了解這些選項，請參閱[AEM Screens Player](working-with-screens-player.md)。

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

此外，按一下右上角的&#x200B;**設定**&#x200B;以更新設備首選項。 您可以更新下列偏好設定：

* **伺服器 URL**
* **解析度**
* **重新開機排程**
* **Max否。保留的日誌檔案**
* **記錄層級**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>您可以選取下列任一「記錄」層級：
>* **停用**
>* **偵錯**
>* **資訊**
>* **警告**
>* **錯誤**


![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## 疑難排解OSGi設定{#troubleshoot-osgi-settings}

您必須啟用空的反向連結，才能讓裝置將資料發佈至伺服器。 例如，如果停用空的反向連結屬性，裝置就無法將螢幕擷圖張貼回。

目前，只有在OSGi設定中啟用&#x200B;*Apache Sling Referrer Filter Allow Empty*&#x200B;時，才能使用其中部分功能。 控制面板可能會顯示警告，指出安全設定可能會使部分功能無法運作。

請依照下列步驟，啟用Apache Sling Referrer Filter Allow Empty

1. 導覽至&#x200B;**Adobe Experience Manager Web主控台設定**，即`https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`。
1. 檢查&#x200B;**allow.empty**&#x200B;選項。
1. 按一下「**儲存**」。

![chlimage_1-3](assets/chlimage_1-3.png)

### 建議 {#recommendations}

下節建議監控網路連結、伺服器和播放器，以了解運作狀況並回應問題。

AEM提供下列項目的內建監控：

* ** 心率為5秒，表示AEM Screens播放器正在運作。
* ** 來自播放器的螢幕截圖，顯示播放器上目前顯示的內容。
* 播放器上安裝的&#x200B;*AEM Screens播放器韌體*&#x200B;版本。
* *播放器* 上的可用儲存空間。

Recommendations，使用第三方軟體進行遠程監控：

* 播放器上的CPU使用量。
* 檢查AEM Screens播放器程式是否執行中。
* 遠程重新啟動/重新啟動播放器。
* 即時通知。

建議您部署播放器硬體和作業系統，以便遠程登錄診斷問題並重新啟動播放器。

#### 其他資源 {#additional-resources}

請參閱[視訊播放設定和疑難排解](troubleshoot-videos.md)以偵錯和疑難排解頻道中播放的視訊。

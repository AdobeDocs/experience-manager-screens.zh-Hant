---
title: 疑難排解裝置控制中心
description: 瞭解如何使用裝置儀表板來監控和疑難排解AEM Screens Player活動和裝置的效能。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 1%

---

# 疑難排解裝置控制中心 {#troubleshooting-device-control-center}

您可以使用裝置控制面板，監控及疑難排解AEM Screens Player活動和裝置的效能。 此頁面提供如何監督及疑難排解Screens播放器和指派裝置感知效能問題的相關資訊。

## 從裝置控制中心進行監控和疑難排解 {#monitor-and-troubleshoot-from-device-control-center}

您可以使用Device Dashboard監控活動，進而疑難排解AEM Screens Player。

### 裝置控制面板 {#device-dashboard}

請依照下列步驟，導覽至裝置控制面板：

1. 從您的專案導覽至裝置儀表板，例如，***測試專案*** > ***裝置***。

   從動作列按一下&#x200B;**裝置**&#x200B;和&#x200B;**裝置管理員**。

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 清單會顯示已指派和未指派的裝置，如下圖所示。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. 按一下裝置(**NewTestDevice**)，然後從動作列按一下&#x200B;**儀表板**。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. 此頁面會顯示裝置資訊、活動，以及可讓您監視裝置活動和功能的裝置詳細資訊。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### 監視裝置活動 {#monitor-device-activity}

**活動**&#x200B;面板會以時間戳記顯示AEM Screens Player的最後一次Ping。 最後一個ping對應到裝置上次連線伺服器的時間。

![chlimage_1](assets/chlimage_1.png)

此外，按一下&#x200B;**活動**&#x200B;面板右上角的&#x200B;**收集記錄**&#x200B;以檢視播放器的記錄。

### 更新裝置詳細資料 {#update-device-details}

檢查&#x200B;**裝置詳細資料**&#x200B;面板，以便檢視裝置的裝置IP、儲存空間使用量、韌體版本和播放器運作時間。

![chlimage_1-1](assets/chlimage_1-1.png)

此外，按一下&#x200B;**清除快取**&#x200B;和&#x200B;**更新**&#x200B;以清除裝置的快取，並從此面板分別更新[韌體](screens-glossary.md)版本。

此外，從&#x200B;**裝置詳細資料**&#x200B;面板的右上角，按一下&#x200B;**...**&#x200B;以重新啟動或重新整理您的播放器狀態。

![chlimage_1-2](assets/chlimage_1-2.png)

### 更新裝置資訊 {#update-device-information}

檢查&#x200B;**裝置資訊**&#x200B;面板。 您可以在此處檢視設定更新、裝置型號、裝置作業系統和殼層資訊。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

另外，按一下[裝置資訊]面板右上角的(**...**)以檢視內容或更新裝置。

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

按一下「**內容**」，檢視「**裝置內容**」對話方塊。 您可以編輯裝置標題，或選擇以&#x200B;**手動**&#x200B;或&#x200B;**自動**&#x200B;更新組態的選項。

>[!NOTE]
>
>若要深入瞭解與裝置的自動或手動更新相關的事件，請參閱[管理管道](managing-channels.md)中裝置控制面板&#x200B;***的***&#x200B;自動與手動更新一節。

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### 檢視播放器熒幕擷圖 {#view-player-screenshot}

您可以從&#x200B;**播放器熒幕擷圖**&#x200B;面板檢視裝置上的播放器熒幕擷圖。

按一下「播放器熒幕擷取畫面」面板右上角的(**...**)，然後按一下「重新整理熒幕擷取畫面」**，以檢視執行中播放器的快照。**

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 管理偏好設定 {#manage-preferences}

**偏好設定**&#x200B;面板可讓使用者變更裝置的&#x200B;**管理員UI**、**頻道切換器**&#x200B;和&#x200B;**遠端偵錯**&#x200B;的偏好設定。

>[!NOTE]
>若要深入瞭解這些選項，請參閱[AEM Screens Player](working-with-screens-player.md)。

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

此外，按一下右上角的&#x200B;**設定**&#x200B;以更新裝置偏好設定。 您可以更新下列偏好設定：

* **伺服器URL**
* **解析度**
* **重新開機排程**
* **最大數量 要保留的記錄檔**
* **記錄層級**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>您可以按一下下列任一記錄層級：
>* **停用**
>* **偵錯**
>* **資訊**
>* **警告**
>* **錯誤**

![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## 疑難排解OSGi設定 {#troubleshoot-osgi-settings}

啟用空白反向連結以允許裝置將資料發佈至伺服器。 例如，如果停用空白反向連結屬性，裝置就無法張貼熒幕擷圖。

目前只有在OSGi設定中啟用&#x200B;*Apache Sling反向連結篩選允許空白*&#x200B;時，才能使用其中的部分功能。 儀表板可能會顯示警告，指出安全性設定可能會使這些功能的部分功能無法運作。

請依照下列步驟，啟用Apache Sling查閱者篩選器允許空白

1. 導覽至&#x200B;**Adobe Experience Manager Web主控台組態**，也就是`https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`。
1. 核取&#x200B;**allow.empty**&#x200B;選項。
1. 按一下「**儲存**」。

![chlimage_1-3](assets/chlimage_1-3.png)

### 建議 {#recommendations}

下節建議監控網路連結、伺服器和播放器，以瞭解運作狀況並對問題做出反應。

AEM提供下列專案的內建監控：

* 每5秒&#x200B;*心率*&#x200B;一次，指出AEM Screens Player運作中。
* 播放器中的&#x200B;*熒幕擷圖*，顯示播放器上顯示的內容。
* 播放器上已安裝&#x200B;*AEM Screens播放器韌體*&#x200B;版本。
* 播放器上的&#x200B;*可用儲存空間*。

使用協力廠商軟體進行遠端監控的Recommendations：

* 播放器中的CPU使用量。
* 檢查AEM Screens Player程式是否正在執行。
* 遠端重新啟動/重新啟動播放器。
* 即時通知。

建議以可讓遠端登入診斷問題並重新啟動播放器的方式，部署播放器硬體及作業系統。

#### 其他資源 {#additional-resources}

如果您想要在您的頻道中偵錯和疑難排解播放的視訊，請參閱[視訊播放設定和疑難排解](troubleshoot-videos.md)。

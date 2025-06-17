---
title: Feature Pack 202109發行說明
description: 瞭解關於2021年9月23日發行的AEM Screens Feature Pack 202109。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 1%

---

# Feature Pack 202109發行說明 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe建議您升級至Adobe Experience Manager (AEM)的最新版本。 AEM Screens提供AEM 6.3 Screens平台的維護支援。

## 可用性 {#availability}

AEM Screens已發行AEM 6.5 Feature Pack 9。

您可以使用您的Adobe ID，從[軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載AEM Screens 6.5.9版的最新Feature Pack。 瀏覽至&#x200B;**Adobe Experience Manager**&#x200B;索引標籤並搜尋&#x200B;**Screens**，以取得標題為&#x200B;**AEM 6.5 Screens FP9**&#x200B;的最新功能套件。

## 發行日期 {#release-date}

AEM Screens Feature Pack 202109的發行日期為2021年9月23日。

### 新增功能 {#what-is-new}

* 影片的縮圖支援&#x200B;**&#x200B;**

  AEM Screens現在支援影片的縮圖支援。 內容作者會定義影片的縮圖，好讓影像可當做預留位置使用。 他們也會適當測試內容播放和目標定位，而由適當的團隊最終確定實際影片。 如果影片播放失敗，也可以使用該影像。
如需詳細資訊，請參閱[影片的縮圖支援](/help/user-guide/thumbnail-support.md)。

* **基本播放監視**

  AEM Screens現在可支援基本播放監控。 播放器現在會報告每次ping （預設為30秒鐘）的各種播放量度。 它會根據量度偵測各種邊緣情況（停滯體驗、空白熒幕、排程問題等）。 此功能可讓團隊在遠端監視播放器是否正確播放內容，並改善對空白熒幕或現場中斷體驗的反應能力。 這也會降低向一般使用者顯示中斷體驗的風險。
如需詳細資訊，請參閱[基本播放監視](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/administering/installing-screens-player#playback-monitoring)。

* **內容指派報告的更新**

  內容指派報告現已最佳化並改善，並擁有增強的使用者體驗。 可下載的報表會顯示改良的播放器相關實體。 這類實體包括位置、顯示器和一個試算表標籤中的裝置。 它也包括內容提供者資訊，例如其他索引標籤中的管道和資產。
如需詳細資訊，請參閱[內容指派報告](/help/user-guide/content-assignment-report.md)。

* **最適化轉譯**

  最適化轉譯可讓裝置根據客戶定義的規則，自動針對裝置按一下最佳轉譯。

  身為AEM Screens開發人員，您現在可以設定自動下載和播放裝置專屬的資產轉譯，而不需要手動建立所有內容變數。 如需詳細資訊，請參閱[最適化轉譯：架構概觀與設定](/help/user-guide/adaptive-renditions.md)。

  此外，身為AEM Screens內容作者，您可以設定資產以使用最適化轉譯。 您也可以移轉大型網路的裝置，以便在AEM Screens管道中使用此功能。 如需詳細資訊，請參閱[在AEM Screens中使用最適化轉譯](/help/user-guide/using-adaptive-renditions.md)。

* **支援V3資訊清單**

  您現在可以為資訊清單版本v3設定Dispatcher 。 若要啟用v3資訊清單，請執行下列動作：

   * 清除作者和已發佈中的任何擱置離線內容工作。

      * 在「作者」和「發佈」中導覽至CRXDE Lite。

      * 按一下「工具」>「查詢」。

      * 在查詢中使用`/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`。

      * 這會列出佇列中目前正在執行或擱置的所有離線內容工作。

      * 等到查詢傳回的離線內容工作已不存在。

   * 在`/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`中停用ContentSync。

   * 在`/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`中啟用SmartSync。

   * 更新Dispatcher。

   * 更新自訂元件。


   * 如需詳細資訊，請參閱[為資訊清單版本v3](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3)設定Dispatcher。
   * 如果您使用自訂元件做為v3資訊清單的一部分，請參閱[自訂處理常式的範本](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers)。


### 錯誤修正 {#bug-fixes}

**播放器端**

* 以轉譯取代資產，解決檔案快取錯誤。

* 如果存在轉譯對應，播放器現在只會公開資產轉譯。

* 增強Ping功能，可在回應無效JSON時重新驗證。

* 數值管道名稱/角色導致空白熒幕。

* 透過SmartSync下載最佳化的轉譯。

* 已將對應轉換為轉譯金鑰清單。

* 已移除Windows Player中`cmd.exe`和`reg.exe`的存取權。

* 播放器必須報告其最後成功的播放事件。

* 播放器必須回報其播放狀態。

* 清除`ALL`快取時，播放器不會重新下載Assets。

* 身為播放器管理員，您現在可以選擇播放器名稱。

* 從顯示區移除頻道指定任務並不會反映在播放器中。

* 如果在下載頻道更新時重新載入播放器，則播放器會忽略更新。

* 內嵌頁面元件現在會遵循觸控事件。

* 現在支援遠端布建Tizen播放器。

**伺服器端**

* 目標影片未顯示
* 將顯示資料廣播到子序列的競爭條件。

* 管道預覽無法用於包含視訊的管道。

* 分割畫面頻道的預覽模式顯示空白。

* 啟用最適化轉譯後，視訊縮圖會呈現為空白。

* 如果已發佈參考的頁面，則自動更新管道資訊清單。

* 刪除的裝置現在不會封鎖Screens復寫佇列。

* 資訊清單未包含目標內容或網站內嵌頁面。 此錯誤現已修正。

* 新的核心影像元件現已新增至頻道資訊清單。

* 現在支援透過SmartSync下載最佳化的轉譯。

* 播放所有資產的最佳化轉譯。

* 新增對多個內容提供者型別的支援

* 內嵌序列播放策略已失效，此錯誤現已修正。

* 使用html專案的要求引數`wcmmode`的離線資訊清單，使其無法快取。

* 空白的動態內嵌序列有時會導致空白熒幕。

* 播放器現在會報告其播放狀態。

* 視訊已在`Tiny mode`中播放，並未在裝置上以全熒幕視訊播放，此問題現已修正。

### 已發行的AEM Screens Players

下列AEM Screens Player已針對AEM 6.5 Feature Pack 9發行：

* Chrome OS
* Windows
* Tizen
* Android™
* Linux®

#### AEM Screens播放器下載

若要下載最新的AEM Screens播放器並深入瞭解錯誤修正，請參閱&#x200B;**[AEM Screens播放器下載](https://download.macromedia.com/screens/index.html)**。

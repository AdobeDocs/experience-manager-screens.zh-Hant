---
title: Feature Pack 202109發行說明
description: 請詳閱本頁，了解2021年9月23日發行的AEM Screens Feature Pack 202105的相關資訊。
feature: Feature Pack
role: Developer
level: Intermediate
source-git-commit: ec58cd9171e359b451eaad7015d42b41ef1bff3f
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 2%

---

# Feature Pack 202109發行說明 {#release-notes-for-feature-pack}

>[!CAUTION]
>建議您升級至最新版Adobe Experience Manager(AEM)。 Screens對AEM 6.3 Screens平台提供維護支援。

## 可用性 {#availability}

AEM Screens發行AEM 6.5 Feature Pack 9。

您可以使用Adobe ID，從[軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載AEM Screens 6.5.9版的最新Feature Pack。 導覽至「**Adobe Experience Manager**」標籤並搜尋「**Screens**」，以取得最新的Feature Pack，標題為「**AEM 6.5 Screens FP9**」。

## 發行日期 {#release-date}

AEM Screens Feature Pack 202109的發行日期為2021年9月23日。

### 新增功能 {#what-is-new}

* **影片的縮圖支援**

   AEM Screens現在支援中影片的縮圖支援。 內容作者可以定義視訊的縮圖，以便影像可作為預留位置，並在適當團隊完成實際視訊時，正確測試內容播放和鎖定目標。 當視訊播放失敗時，也可以使用影像。
如需詳細資訊，請參閱[視訊的縮圖支援](/help/user-guide/thumbnail-support.md) 。

* **基本播放監控**

   AEM Screens現在支援基本播放監控。 播放器現在會報告各種播放量度，每次偵測（預設為30秒）。 它可根據量度偵測各種邊緣案例（停滯體驗、空白畫面、排程問題等）。 此功能可讓團隊遠端監視播放器是否正確播放內容、改善對空白畫面或欄位中中斷體驗的再活動，並降低向使用者顯示中斷體驗的風險。
如需詳細資訊，請參閱[基本播放監控](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/installing-screens-player.html?lang=en#playback-monitoring) 。

* **內容指派報表的更新**

   內容指派報表現在已最佳化，並透過增強的使用者體驗加以改善。 可下載的報表在一個試算表標籤中顯示改善的播放器相關實體，例如位置、顯示器和裝置，以及內容提供者資訊，例如頻道和資產，在其他標籤中。
如需詳細資訊，請參閱[內容指派報表](/help/user-guide/content-assignment-report.md) 。

* **適用性轉譯**

   適用性轉譯可讓裝置根據客戶定義的規則，自動為裝置選取最佳轉譯。

   身為AEM Screens開發人員，您現在可以設定要下載和自動播放的裝置專屬資產轉譯，而不需要手動建立所有內容變異。 請參閱[適用性轉譯：架構概述和設定](/help/user-guide/adaptive-renditions.md)以取得詳細資訊

   此外，身為AEM Screens內容作者，您現在可以在AEM Screens專案中使用最適化轉譯，也可針對大型網路套用移轉策略。

* **支援V3艙單**

   您現在可以為資訊清單版本v3設定Dispatcher。 如需詳細資訊，請參閱[為資訊清單版本v3](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3)設定Dispatcher 。
此外，如果您將自定義元件用作v3清單的一部分，請參閱[自定義處理程式的模板](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers)。


### 錯誤修正 {#bug-fixes}

**播放器端**

* 以轉譯取代資產，解決檔案快取錯誤。

* 現在，如果轉譯對應存在，播放器只會顯示資產轉譯。

* 增強Ping功能，可在回應無效時重新驗證。

* 數值通道名稱/角色造成空白畫面。

* 透過SmartSync下載最佳化轉譯。

* 將對應轉換為轉譯金鑰清單。

* 移除Windows播放器中對`cmd.exe`和`reg.exe`的存取。

* 播放器需要回報其最後一次成功的播放事件。

* 播放器需要回報其播放狀態。

* 清除`ALL`快取時，播放器不會重新下載資產。

* 身為播放器管理員，您現在可以選擇播放器名稱。

* 從顯示中移除頻道指派不會反映在播放器上。

* 如果播放器在下載頻道更新時重新載入，播放器會忽略更新。

* 內嵌頁面元件現在會遵守觸控事件。

* 現在支援Tizen播放器的遠端布建。

**伺服器端**

* Target視訊未顯示
* 向子序列廣播顯示資料時的競爭條件。

* 包含視訊的管道無法使用管道預覽。

* 分割螢幕頻道的預覽模式顯示為空白。

* 視訊縮圖會以啟用的最適化轉譯呈現空白。

* 如果參考頁面已發佈，會自動更新管道資訊清單。

* 已刪除的裝置現在不會封鎖Screens復寫佇列。

* 資訊清單不包含目標內容或Sites內嵌頁面。 此問題現已修正。

* 新的核心影像元件現已新增至管道資訊清單。

* 現在支援透過SmartSync下載最佳化轉譯。

* 為所有資產播放最佳化的轉譯。

* 新增對多種內容提供者類型的支援

* 內嵌序列播放策略已中斷，此問題現已修正。

* 對html項目使用要求參數`wcmmode`的離線資訊清單，使其無法執行。

* 空白的動態內嵌序列有時會造成空白畫面。

* 播放器現在會回報其播放狀態。

* 視訊在`Tiny mode`中播放，但未在裝置上以全螢幕視訊的形式播放，問題現已修正。

### 發行的AEM Screens播放器 {#released-aem-screens-players}

已針對AEM 6.5 Feature Pack 9發行下列AEM Screens播放器：

* ChromeOS
* Windows
* 蒂森
* Android
* Linux

#### AEM Screens播放器下載  {#aem-screens-player-downloads}

若要下載最新的AEM Screens播放器並進一步了解錯誤修正，請參閱&#x200B;**[AEM Screens播放器下載](https://download.macromedia.com/screens/index.html)**。

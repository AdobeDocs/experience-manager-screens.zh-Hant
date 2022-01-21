---
title: 功能包202109發行說明
description: 按照本頁獲取2021年9月23日發佈的AEM Screens功能包202109的資訊。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: b56844c66bfa980013b610523842c7ac0c30f44d
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 1%

---

# 功能包202109發行說明 {#release-notes-for-feature-pack}

>[!CAUTION]
>建議您升級到最新版本的Adobe Experience Manager(AEM)。 螢幕為6.3螢幕AEM平台提供維護支援。

## 可用性 {#availability}

AEM Screens發AEM布了6.5功能包9。

您可以從以下網站下載AEM Screens6.5.9版的最新功能包： [軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 用你的Adobe ID。 導航到 **Adobe Experience Manager** 頁籤和搜索 **螢幕** 獲取最新功能包的標題為 **AEMFP9 6.5螢幕**。

## 發行日期 {#release-date}

AEM Screens功能包202109的發佈日期為2021年9月23日。

### 新增功能 {#what-is-new}

* **視頻縮略圖支援**

   現在在AEM Screens支援的視頻縮略圖支援。 內容作者可以定義視頻的縮略圖，以便影像可以用作佔位符並正確地test內容回放和目標，同時由適當的團隊最終確定實際視頻。 在視頻回放失敗時，也可以使用影像。
請參閱 [視頻縮略圖支援](/help/user-guide/thumbnail-support.md) 的子菜單。

* **基本播放監視**

   AEM Screens現在支援基本回放監視。 播放器現在將報告各種播放度量（預設為30秒）。 基於這些指標，它提供了檢測各種邊緣情況（停滯體驗、空白螢幕、調度問題等）的能力。 此功能允許團隊遠程監視玩家是否正確播放內容，提高對空白螢幕或現場中的中斷體驗的反應性，並降低向最終用戶顯示中斷體驗的風險。
請參閱 [基本播放監視](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/installing-screens-player.html?lang=en#playback-monitoring) 的子菜單。

* **內容分配報告的更新**

   內容分配報告現在通過增強的用戶體驗進行了優化和改進。 該可下載報告在一個電子錶格標籤中顯示改進的播放器相關實體，如位置、顯示器和設備，以及諸如頻道和其它標籤中的資產等內容提供者資訊。
請參閱 [內容分配報告](/help/user-guide/content-assignment-report.md) 的子菜單。

* **自適應格式副本**

   自適應格式副本允許設備根據客戶定義的規則自動為設備選擇最佳格式副本。

   作為AEM Screens開發人員，您現在可以配置特定於設備的資產格式副本，以便自動下載和播放，而無需手動建立所有內容變體。 請參閱 [自適應格式副本：體系結構概述和配置](/help/user-guide/adaptive-renditions.md) 的子菜單。

   此外，作為AEM Screens內容作者，您可以配置資產以使用自適應格式副本，還可以在AEM Screens渠道中為大型網路遷移設備以利用此功能。 請參閱 [在AEM Screens使用自適應格式副本](/help/user-guide/using-adaptive-renditions.md) 的子菜單。

* **支援V3艙單**

   現在，您可以為清單版本v3配置Dispatcher。 要啟用v3清單，您需要：

   * 清除作者和已發佈的任何掛起的離線內容作業

      * 導航到作者中的crx/de並發佈

      * 按一下「工具」 — >「查詢」

      * 在查詢使用中 `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`

      * 這將列出隊列中當前正在運行或掛起的任何離線內容作業

      * 等待，直到從查詢返回的離線內容作業不再
   * 在中禁用ContentSync `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`

   * 在中啟用SmartSync `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`

   * 更新調度程式

   * 更新自定義元件


   * 請參閱 [為清單版本v3配置Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) 的子菜單。
   * 如果將自定義元件用作v3清單的一部分，請參見 [自定義處理程式模板](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers)。



### 錯誤修正 {#bug-fixes}

**玩家側**

* 通過用格式副本替換資產來解決檔案快取錯誤。

* 如果存在格式副本映射，玩家現在僅公開資產格式副本。

* 如果響應無效，則增強ping以重新驗證。

* 數字通道名稱/角色導致空白螢幕。

* 通過SmartSync下載優化的格式副本。

* 已將映射轉換為格式副本鍵清單。

* 已刪除對 `cmd.exe` 和 `reg.exe` 的下界。

* 玩家需要報告其上次成功的回放事件。

* 播放器需要報告其播放狀態。

* Player在 `ALL` 快取已清除。

* 作為播放器管理員，您現在可以選擇播放器名稱。

* 從顯示中刪除頻道分配不會反映在播放器上。

* 如果播放器在下載頻道更新時被重新載入，則播放器將忽略更新。

* 嵌入式頁面元件現在尊重觸摸事件。

* 現在支援Tizen播放器的遠程設定。

**伺服器端**

* 目標視頻未顯示
* 將顯示資料廣播到子序列上的競爭條件。

* 「頻道預覽」不適用於包含視頻的頻道。

* 「拆分」螢幕通道的預覽模式顯示為空。

* 視頻縮略圖呈現為空，並啟用自適應格式副本。

* 如果已發佈引用頁，則自動更新通道清單。

* 刪除的設備現在不會阻止螢幕複製隊列。

* 清單不包含目標內容或站點嵌入頁面。 這個現在已經修復了。

* 新的核心影像元件現在添加到通道清單中。

* 現在支援通過SmartSync下載優化的格式副本。

* 為所有資產播放優化的格式副本。

* 增加了對多個內容提供程式類型的支援

* 嵌入式序列回放策略已中斷，現已修復。

* 使用請求參數的離線清單 `wcmmode` 為html條目，使其不可執行。

* 空動態嵌入序列有時會導致空白螢幕。

* 播放器現在報告其播放狀態。

* 視頻正在播放 `Tiny mode` 未在設備上作為全屏視頻播放，問題現已解決。

### 已釋放AEM Screens球員 {#released-aem-screens-players}

以下AEM Screens玩家AEM將發佈6.5功能包9:

* ChromeOS
* Windows
* 蒂森
* Android
* Linux

#### AEM Screens播放器下載  {#aem-screens-player-downloads}

要下載最新的AEM Screens播放器並瞭解有關錯誤修復的詳細資訊，請參閱 **[AEM Screens播放器下載](https://download.macromedia.com/screens/index.html)**。

---
title: 測試與品質保證
seo-title: AEM螢幕的測試與品質保證
description: 此頁面說明「AEM畫面的測試與品質保證最佳實務指南」
seo-description: 此頁面說明「AEM畫面的測試與品質保證最佳實務指南」
translation-type: tm+mt
source-git-commit: d5eb9fadffcc41ede9b1f9399c5edbeac3363954

---


# 測試與品質保證 {#testing-quality}

>[!NOTE]
>
>此活動的一般利益相關者是A/V整合商。

隨著我們越來越接近數位標牌網路的實際部署，我們應制定測試和QA計畫，以處理網路的每個元素，包括所有硬體元件、所有軟體元件和所有網路元件。
在此階段，應建立完整的測試系統，並加以充分測試。

應建立一個核對表，該核對表標識所有先前定義的KPI，並根據這些KPI測量交付項。

>[!NOTE]
> 此階段也應當做建立安裝與使用指南的工具，稍後可隨附設備，並留在現場供日後參考。

應考慮以下因素：

## 1.機械注意事項 {#mechanical-considerations}

建議使用下列機械注意事項：

* 顯示器安裝
* 播放器安裝
* 通風
* 外圍設備附件
* 電纜管理
* 設備聯網

## 2.軟體考量事項 {#software-considerations}

建議使用下列軟體考量事項：

* 設備註冊
* 媒體發佈
* 播放
* 資料庫依賴性（先前定義）


## 3.設備管理注意事項 {#device-management-considerations}


AEM Screens包含Device Control Center模組，可讓您管理Screens播放器應用程式端點。

這是指任何已 ** 安裝Screens player應用程式且已註冊至AEM例項的播放器硬體裝置。
此模組允許您：

1. 監視播放器應用程式錯誤日誌
1. 管理遠端螢幕擷取
1. 管理內容下載
1. 管理應用程式重新啟動問題

若要詳細瞭解裝置控 ***制中心***，請參閱 [AEM Screens使用指南中的疑難排解裝置控制中心](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html)****。

>[!CAUTION]
> 您不應使用Device Control Center來：
>
> 1. 安裝新版播放器應用程式
> 1. 監控系統級資源
> 1. 疑難排解系統級錯誤
> 1. 允許遠程案頭干預



>[!NOTE]
> Adobe建議所有部署應使用專用的第三方裝置管理平台。

選擇的特定平台取決於多個因素，包括目 ***標作業系統******、項目需*** 求 ******&#x200B;和端點數。

例如：

* Google Chrome裝置管理
* TeamViewer
* AirWatch
* 42Gears
* 專屬AV整合器中介軟體

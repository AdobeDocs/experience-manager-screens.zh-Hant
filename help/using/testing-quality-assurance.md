---
title: 測試與品質保證
seo-title: AEM Screens的測試與品質保證
description: 本頁面說明AEM Screens最佳實務指南的測試和品質保證
seo-description: 本頁面說明AEM Screens最佳實務指南的測試和品質保證
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 2%

---

# 測試與品質保證 {#testing-quality}

>[!NOTE]
>此活動的一般利害關係人是A/V整合商。

隨著我們更接近數字告示牌網路的實際部署，我們應建立測試和QA計畫，該計畫可解決網路的每個元素，包括所有硬體元件、所有軟體元件和所有網路元件。
在這一階段，應構建並完全測試整個測試系統。

應建立一個檢查清單，確定所有先前定義的KPI，並根據這些KPI測量交付項。

>[!NOTE]
>
>此階段還應用作建立安裝和使用手冊的工具，以後可隨設備一起運送，並留在現場供將來參考。

應考量下列元素：

## 1.機械注意事項{#mechanical-considerations}

建議使用下列機械注意事項：

* 顯示安裝
* 播放器安裝
* 通風
* 外圍設備附件
* 電纜管理
* 裝置聯網

## 2.軟體注意事項{#software-considerations}

建議使用下列軟體考量事項：

* 設備註冊
* 媒體發佈
* 播放
* 資料庫依賴項（以前定義）


## 3.設備管理注意事項{#device-management-considerations}

AEM Screens包含Device Control Center模組，可管理Screens播放器應用程式端點。

這是指任何已安裝Screens播放器應用程式且已註冊至AEM例項的&#x200B;*player*硬體裝置。
此模組可讓您：

1. 監視播放器應用程式錯誤日誌
1. 管理遠程螢幕快照
1. 管理內容下載
1. 管理應用程式重新啟動問題

要詳細了解&#x200B;***Device Control Center***，請參閱&#x200B;**AEM Screens使用手冊**&#x200B;中的[Troubleshooting Device Control Center](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html)。

>[!CAUTION]
>
> 您不應使用Device Control Center來：
> 1. 安裝新版本的播放器應用程式
> 1. 監視系統級別資源
> 1. 排解系統層級錯誤
> 1. 允許遠程案頭干預



>[!NOTE]
>
> Adobe建議所有部署都應使用專用的第三方裝置管理平台。

選擇的特定平台取決於多種因素，包括&#x200B;***目標作業系統***、***項目要求***&#x200B;和&#x200B;***端點數***。

以下是幾個範例：

* Google Chrome裝置管理
* TeamViewer
* AirWatch
* 42檔
* 專有AV整合商中間件

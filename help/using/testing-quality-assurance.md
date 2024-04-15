---
title: 測試與品質保證
description: 在最佳實務指南中瞭解AEM Screens的測試和品質保證。
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 3c4b37b3b9f268b500562fa4ce3782b7be1e7d74
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# 測試與品質保證 {#testing-quality}

>[!NOTE]
>此活動的一般利害關係人是音訊/視訊整合商。

當您接近部署數位看板網路時，請建立測試與QA計畫，解決網路的每個元素，包括所有硬體元件、所有軟體元件和所有網路元件。
在這個階段中，應該建置整個測試系統並進行完整測試。

應建立檢查清單，以識別所有先前定義的KPI並測量其交付成果。

>[!NOTE]
>
>此階段也應作為建立安裝和使用者指南的工具，之後可隨裝置一併寄出，並保留在現場以供日後參考。

應考慮以下元素：

## 1.機械考量 {#mechanical-considerations}

建議採取下列機械考量：

* 顯示器掛載
* 播放器掛載
* 通風
* 周邊裝置附件
* 纜線管理
* 裝置網路

## 2.軟體考量事項 {#software-considerations}

建議採取下列軟體考量事項：

* 裝置註冊
* 媒體發佈
* 播放
* 資料庫相依性（先前定義）


## 3.裝置管理考量事項 {#device-management-considerations}

AEM Screens包含Device Control Center模組，可管理Screens播放器應用程式端點。

這指任何 *播放器* 已安裝Screens播放器應用程式並註冊至AEM執行個體的硬體裝置。
此模組可讓您：

1. 監視播放器應用程式錯誤記錄
1. 管理遠端熒幕擷取畫面
1. 管理內容下載
1. 管理應用程式重新啟動問題

若要深入瞭解 ***裝置控制中心***，請參閱 [疑難排解裝置控制中心](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens) 在 **AEM Screens使用手冊**.

>[!CAUTION]
>
>請勿使用Device Control Center：
>
>* 安裝新版本的播放器應用程式
>* 監視系統層級資源
>* 疑難排解系統層級錯誤
>* 允許遠端案頭介入


>[!NOTE]
>
> Adobe建議使用專屬的協力廠商裝置管理平台進行所有部署。

選擇的特定平台取決於多種因素，包括 ***目標作業系統***， ***專案需求***、和 ***端點數目***.

以下是幾個範例：

* Google Chrome裝置管理
* 團隊檢視器
* AirWatch
* `42Gears`
* 專屬音訊/視訊整合器中介軟體

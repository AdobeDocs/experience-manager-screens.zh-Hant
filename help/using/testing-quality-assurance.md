---
title: 測試與品質保證
description: 在最佳實務指南中瞭解AEM Screens的測試和品質保證。
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# 測試與品質保證 {#testing-quality}

>[!NOTE]
>此活動的典型利害關係人為音訊 — 視訊整合商。

當您接近部署數位看板網路時，請建立測試與QA計畫，解決網路的每個元素，包括所有硬體元件、所有軟體元件和所有網路元件。
在這個階段中，應該建置整個測試系統並進行完整測試。

應建立檢查清單，以識別所有先前定義的KPI並測量其交付成果。

>[!NOTE]
>
>此階段也應作為建立安裝和使用者指南的工具。 兩者稍後都可以隨裝置出貨，並保留在現場以供日後參考。

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

AEM Screens包含裝置控制中心模組，可管理Screens播放器應用程式端點。

它是指任何已安裝Screens播放器應用程式並註冊到AEM執行個體的&#x200B;*播放器*硬體裝置。
此模組可讓您：

1. 監視播放器應用程式錯誤記錄
1. 管理遠端熒幕擷取畫面
1. 管理內容下載
1. 管理應用程式重新啟動問題

若要深入瞭解&#x200B;***裝置控制中心***，請參閱&#x200B;**AEM Screens使用手冊**&#x200B;中的[裝置控制中心疑難排解](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens)。

>[!CAUTION]
>
>請勿使用「裝置控制中心」來：
>
>* 安裝新版本的播放器應用程式
>* 監視系統層級資源
>* 疑難排解系統層級錯誤
>* 允許遠端案頭介入


>[!NOTE]
>
> Adobe建議使用專屬的協力廠商裝置管理平台進行所有部署。

所選的特定平台取決於數個因素，包括&#x200B;***目標作業系統***、***專案需求***&#x200B;以及&#x200B;***端點數目***。

以下是幾個範例：

* Google Chrome裝置管理
* 團隊檢視器
* AirWatch
* `42Gears`
* 專屬音訊整合器中介軟體

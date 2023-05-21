---
title: 測試與品質保證
seo-title: Testing and Quality Assurance for AEM Screens
description: 本頁介紹《AEM Screens最佳實踐指南》的測試和質量保證
seo-description: The page describes Testing and Quality Assurance for AEM Screens Best Practices Guide
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 2%

---

# 測試與品質保證 {#testing-quality}

>[!NOTE]
>此活動的典型利益相關方是A/V整合商。

隨著數字標牌網路的實際部署越來越接近，我們應該制定一個Test和QA計畫，解決網路的每個元素，包括所有硬體元件、所有軟體元件和所有網路元件。
在這一階段，整個test系統應該建立並進行充分測試。

應建立一個核對表，它標識所有先前定義的KPI並根據這些KPI衡量可交付項。

>[!NOTE]
>
>此階段還應用作建立安裝和使用手冊的工具，該指南稍後可隨設備一起提供，並在現場保存，以供將來參考。

應考慮以下因素：

## 1。機械考慮 {#mechanical-considerations}

建議考慮以下機械因素：

* 顯示器安裝
* 播放器安裝
* 通風
* 外圍設備附件
* 電纜管理
* 設備聯網

## 2.軟體注意事項 {#software-considerations}

建議使用以下軟體注意事項：

* 設備註冊
* 媒體發佈
* 播放
* 資料庫依賴項（以前定義）


## 3.設備管理注意事項 {#device-management-considerations}

AEM Screens包括設備控制中心模組，其允許管理螢幕播放器應用端點。

這是指 *玩家* 已安裝螢幕播放器應用程式並已註冊到實例的硬體設AEM備。
此模組允許您：

1. 監視播放器應用程式錯誤日誌
1. 管理遠程螢幕抓圖
1. 管理內容下載
1. 管理應用程式重啟問題

詳細瞭解 ***設備控制中心***，請參閱 [設備控制中心故障排除](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html) 在 **AEM Screens使用手冊**。

>[!CAUTION]
>
> 您不應使用設備控制中心：
> 1. 安裝播放器應用程式的新版本
> 1. 監視系統級資源
> 1. 排除系統級錯誤
> 1. 允許遠程案頭干預



>[!NOTE]
>
> Adobe建議將專用的第三方設備管理平台用於所有部署。

選擇的特定平台取決於許多因素，包括 ***目標作業系統***。 ***項目要求*** 和 ***端點數***。

很少有這樣的例子：

* GoogleChrome設備管理
* 團隊查看器
* AirWatch
* 42Gears
* 專有AV整合商中間件

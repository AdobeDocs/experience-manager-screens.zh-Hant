---
title: 支援監控
seo-title: 支援監控AEM Screens
description: 本頁面說明AEM Screens最佳實務支援監控指南
seo-description: 本頁面說明AEM Screens最佳實務支援監控指南
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# 支援監視{#support-monitoring}

本節提供與管理數位看板專案中的裝置和內容異常相關的最佳實務。

支援監控包括：

* **裝置監視**
* **內容監控**

## 內容監視{#content-monitoring}

內容監控可讓您疑難排解與未正確顯示在畫面上的內容相關的問題：

1. 如果遇到空白螢幕問題：

   * 檢查&#x200B;*preview*&#x200B;以查看通道是否顯示黑屏
   * 在筆記型電腦上註冊&#x200B;*本機Chrome播放器*（作為擴充功能）至該顯示器，並查看其是否顯示黑屏。
   * 按一下右鍵並檢查&#x200B;*適用日誌*。

   此外，如果此情況不會在本機播放器上發生，但只會在裝置上發生：

   * 檢查該裝置上可能有問題的&#x200B;*媒體類型*（正在使用），並確認內容是否已成功在本機下載（管理員UI清除頻道快取）。
   * 在票證中加入任何&#x200B;*裝置記錄*，以快速進行疑難排解。
   * *從* 裝置收集記錄。


## 設備監視{#device-monitoring}

如果遇到空白螢幕問題，則與監視物理設備相關的設備監視：

1. 如果遇到空白螢幕問題：

   * 檢查&#x200B;*display*&#x200B;是否已開啟。
   * 檢查&#x200B;*computer*&#x200B;是否已開啟並正在發送信號。
   * 按一下右鍵，檢查並檢查&#x200B;*適用日誌*。

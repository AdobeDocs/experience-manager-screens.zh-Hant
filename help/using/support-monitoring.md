---
title: 支援監控
seo-title: Support Monitoring for AEM Screens
description: 本頁介紹《AEM Screens最佳做法支援監控指南》
seo-description: The page describes Support Monitoring for AEM Screens Best Practices Guide
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 支援監控 {#support-monitoring}

本節提供與管理數字標牌項目中的設備和內容異常相關的最佳做法。

支援監控包括：

* **設備監視**
* **內容監視**

## 內容監視 {#content-monitoring}

內容監視允許您排除與螢幕上未正確顯示的內容相關的問題：

1. 如果遇到空白螢幕問題：

   * 檢查 *預覽* 看頻道是否顯示黑屏
   * 註冊 *局部鉻粉* （作為擴展）顯示到該顯示器，並查看是否顯示黑屏。
   * 按一下右鍵並檢查和檢查 *適用日誌*。

   此外，如果本地播放器上沒有出現這種情況，但僅在設備上出現：

   * 檢查 *媒體類型* （正在使用），該設備可能有問題，並且還確認內容是否已成功本地下載（管理UI清除通道快取）。
   * 包括任何 *設備日誌* 的子菜單。
   * *收集日誌* 從設備中AEM。


## 設備監視 {#device-monitoring}

與監視物理設備相關的設備監視（如果遇到空白螢幕問題）:

1. 如果遇到空白螢幕問題：

   * 檢查 *顯示* 已通電。
   * 檢查 *電腦* 已通電並正在發送信號。
   * 按一下右鍵、檢查和檢查 *適用日誌*。

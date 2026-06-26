---
title: 支援監控
description: 瞭解AEM Screens最佳實務指南的支援監視。
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
TQID: https://experienceleague.adobe.com/uqtkwa1zcJ58tJOxWT0gWkOhAM-C-5zEdcFLjrHa1-Q
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 266
ht-degree: 0%

---

# 支援監控 {#support-monitoring}

>[!IMPORTANT]
>此內容對AEM內部部署/AMS （AEM 6.5LTS和AEM 6.5）有效。 如需AEM as a Cloud Service Screens內容，請參閱[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

本節提供與管理數位看板專案中裝置和內容異常相關的最佳實務。

支援監控包括：

* **裝置監視**
* **內容監視**

## 內容監視 {#content-monitoring}

內容監視可讓您疑難排解與熒幕未正確顯示內容相關的問題：

1. 如果發生空白熒幕問題：

   * 檢查&#x200B;*預覽*，以便檢視頻道是否顯示黑色熒幕。
   * 在筆記型電腦上註冊&#x200B;*本機Chrome播放器* （作為擴充功能）至該顯示器，並檢視是否顯示黑熒幕。
   * 按一下滑鼠右鍵並檢查並檢查&#x200B;*適用的記錄*。

   此外，如果問題不是發生在本機播放器上，而是隻發生在裝置上：

   * 檢查該裝置上可能有問題的&#x200B;*媒體型別* （正在使用），並確認內容是否已成功在本機下載（管理UI清除頻道快取）。
   * 在票證中包含任何&#x200B;*裝置記錄*&#x200B;以進行快速疑難排解。
   * 從AEM收集裝置&#x200B;*的記錄*。

## 裝置監視 {#device-monitoring}

與監視實體裝置相關的裝置監視（如果您遇到空白熒幕問題）：

1. 如果發生空白熒幕問題：

   * 檢查&#x200B;*顯示器*&#x200B;是否已開機。
   * 檢查&#x200B;*電腦*&#x200B;是否已開機且正在傳送訊號。
   * 按一下滑鼠右鍵，檢查並檢查&#x200B;*適用的記錄*。


---
title: Feature Pack 202103發行說明
description: 進一步瞭解2021年3月5日發行的AEM Screens Feature Pack 202103。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
TQID: https://experienceleague.adobe.com/x7dgY8u-SdWo2JRK1W2uqRWtHy2wtXdAnIcS0gRoxiY
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 407
ht-degree: 4%

---

# Feature Pack 202103發行說明 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe建議您升級至Adobe Experience Manager (AEM)的最新版本。 AEM Screens提供AEM 6.3 Screens平台的維護支援。

## 可用性 {#availability}

AEM Screens已發行AEM 6.5 Feature Pack 7。

您可以使用您的Adobe ID，從[軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載AEM Screens 6.5.7版的最新Feature Pack。 瀏覽至&#x200B;**Adobe Experience Manager**&#x200B;索引標籤並搜尋&#x200B;**Screens**，以取得標題為&#x200B;**AEM 6.5 Screens FP7**&#x200B;的最新功能套件。

## 發行日期 {#release-date}

AEM Screens Feature Pack 202103的發行日期為2021年3月5日。

### 新增功能 {#what-is-new}

* **AEM Screens自動註冊播放器**

  手動大量註冊數千個播放器不僅費時費力，而且增加了時間和成本。 為簡化此程式，播放器自動註冊功能可讓您在AEM中指定預先共用金鑰。 此金鑰可透過設定檔案或行動裝置管理(MDM)解決方案布建至播放器。

  如需詳細資訊，請參閱[自動註冊播放器](/help/user-guide/auto-registration-players.md)。


* **使用Enterprise Mobility Management大量布建™播放器**

  大量部署™播放器時，手動向AEM註冊每個播放器會變得繁瑣起來。 強烈建議使用EMM （企業行動管理）解決方案，例如`VMWare Airwatch`、`MobileIron`或`Samsung Knox`，從遠端布建和管理您的部署。 AEM Screens Android™播放器支援業界標準的EMM AppConfig，以允許遠端布建。

  如需詳細資訊，請參閱[使用Enterprise Mobility Management大量布建™ Player](/help/user-guide/implementing-android-player.md#implementation)。


### 錯誤修正 {#bug-fixes}

* 改善計算`clientlib`和`asset hashes`的效能。

* 如果快取未失效，SmartSync移轉將會中斷播放器。

* 如果工作分派有&#x200B;*OfflineConfig*，則未建立離線快取。

* 因為不支援反向連結原則strict-origin-when-cross-origin，所以中斷的`Tizen`播放器更新。

* 變更指派頻道的排程&#x200B;*重複*&#x200B;欄位已中斷UI。

* 更新離線內容失敗，發生查詢例外。

* 互動式體驗互動期間，轉換之間的時間延遲現在已修正。

* 失敗的設定更新要求造成空白熒幕。

### 已發行的AEM Screens Players

下列AEM Screens Player已針對AEM 6.5 Feature Pack 7發行：

* Chrome作業系統
* Windows
* Linux®

#### AEM Screens播放器下載

若要下載最新的AEM Screens播放器並深入瞭解錯誤修正，請參閱&#x200B;**[AEM Screens播放器下載](https://download.macromedia.com/screens/index.html)**。

---
title: 安全性檢查清單
seo-title: 安全性檢查清單
description: 本頁說明安全檢查清單
seo-description: 本頁說明安全檢查清單
translation-type: tm+mt
source-git-commit: ccc1baa0b57cb1311855065433aabf627814d16a
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---


# AEM Screens安全性檢查清單  {#security-checklist}

「AEM畫面安全性檢查清單」頁面會說明主要安全性區域，以及問題和考量事項的檢查清單。

## 檢查清單表格 {#checklist-table}

| **安全區** | **檢查清單** | **是／否/不適用** |
|---|---|---|
| **AEM和畫面軟體更新** | ***a.*** *是否已套用最新的Adobe Experience Manager(AEM)Service Pack?* <br>***b.****是否已套用最新的AEM Screens Feature Pack?*<br>***c.*** *您是否在使用[AEM Screens Player下載中最新推出的AEM Screens Player軟體](https://download.macromedia.com/screens/)?* |
| **物理安全** | ***a.*** *是否禁用了所有不必要的埠？* <br>***b.****您是否已確保電纜和硬體的安全？*<br>***c.*** *您是否使用任何容器（如果適用）?* |
| **網路安全** | ***a.*** *您是否在您的標牌設備上使用隔離子網？* <br>***b.****隔離的子網是否允許存取必要的端點，包括AEM、Adobe Analytics或其他必要服務？*<br>***c.*** *您是否使用企業最佳實踐保護了Wi-Fi?* <br>***d.****如果使用同步播放，您是否僅允許在主設備上使用TCP 24503 for WebSocket?*<br>***e.*** *您是否已解除封鎖播放器裝置的IP位址範圍，讓只有授權的裝置才能存取作者的註冊服務？* |
| **作業系統安全性** | ***a.*** *您是否已升級到作業系統的最新版本並應用了所有必要的安全修補程式？* <br>***b.****您是否已禁用了所有不必要的服務並刪除了不必要的應用程式？*<br>***c.*** *您是否已將裝置註冊到裝置管理中，以執行企業政策？* <br>***d.****您是否已將裝置鎖定至單一應用程式（播放器）資訊站？*<br>***e.*** *您是否已制定標準作業程式(SOP)，以隨時間安裝作業系統安全性更新？*<br>***f.****您是否已遵循使用中作業系統的安全性最佳實務，例如防惡意軟體、非管理使用者？* |
| **應用程式安全性** | ***a.*** *您是否已停用生產用的管理員UI、頻道切換器和活動UI?* <br>***b.****您是否已將生產日誌級別降到最低？*<br>***c.*** *您是否使用https連線至AEM?* <br>***d.****您使用的是CA簽名憑證或企業PKI? （非自簽憑證）*<br>***e.****&#x200B;您是否使用TLS而非SSL v3?*<br>*** f.****您在註冊時，是否正在驗證裝置和AEM上的註冊Token?*<br> ***g.*** *您是否已將所使用的資料分類，且裝置上沒有PII或PHI?*<br> ***h.*** *您是否已將所使用的資料分類，且裝置上沒有個人識別資訊(PII)或受保護的健康資訊(PHI)?*<br> ***i.*** *您是否已設定監控電子郵件，並且您是否有SOP可回應監控電子郵件和處理非ping裝置？* |
| **存取控制** | ***a.*** *您是否在內部識別和管理了基於角色的訪問控制(RBAC)?* <br>***b.****您是否遵循最少權限原則，使用Adobe的最佳實務來提供作者、管理員和播放器的存取權？* |

### 下載安全性檢查清單 {#download-checklist}

若要下載AEM Screens Security Checklist，請按一 [下這裡](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf)。
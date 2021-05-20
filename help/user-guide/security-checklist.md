---
title: 安全性檢查清單
seo-title: 安全性檢查清單
description: 本頁面會說明主要安全性領域，並列出各種問題和考量事項。
seo-description: 此頁面說明了安全性檢查清單
feature: 管理畫面
role: Administrator
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# AEM Screens安全性檢查清單{#security-checklist}

AEM Screens安全性檢查清單頁面以問題和考量事項的檢查清單，說明主要安全性領域。

## 檢查清單表{#checklist-table}

| **安全區** | **檢查清單** | **是/否/不適用** |
|---|---|---|
| **AEM和Screens軟體更新** | ***a.*** *已套用最新的Adobe Experience Manager(AEM)Service Pack嗎？* <br>***b.***  *已套用最新的AEM Screens Feature Pack嗎？* <br>***c.*** *您是否使用AEM Screens Player下載中最新推出的AEM Screens  [Player軟體](https://download.macromedia.com/screens/)?* |
| **物理安全** | ***a.*** *您是否禁用了所有不必要的埠？* <br>***b.***  *您有安全的佈線和硬體嗎？* <br>***c.*** *您是否使用任何容器（如果適用）?* |
| **網路安全** | ***a.*** *您是否為看板設備使用隔離子網？* <br>***b.***  *隔離子網是否允許訪問包括AEM、Adobe Analytics或其他必需服務在內的必需端點？* <br>***c.*** *您是否使用企業最佳做法保護了Wi-Fi?* <br>***d.*** *如果使用同步播放，您是否僅允許主設備上的WebSocket使用TCP 24503?* <br>***e.*** *您是否已取消封鎖播放器裝置的IP位址範圍，讓只有授權裝置才能存取作者上的註冊服務？* |
| **作業系統安全性** | ***a.*** *您是否已升級到作業系統的最新版本並應用了所有必要的安全補丁？* <br>***b.您*** *是否禁用了所有不必要的服務並刪除了不必要的應用程式？* <br>***c.*** *您是否已將設備註冊到設備管理中以實施企業策略？* <br>***d.*** *您是否將裝置鎖定至單一應用程式（播放器）資訊站？* <br>***e.*** *您是否已制定標準作業程式(SOP)以隨時間安裝作業系統安全更新？*<br>***f.*** *您是否遵循使用中作業系統的安全最佳做法，如防惡意軟體、非管理用戶？* |
| **應用程式安全性** | ***a.您*** *是否已停用生產用的管理員UI、管道切換器和活動UI?* <br>***b.*** *您是否已將生產記錄層級最小化？* <br>***c.*** *您是否使用https連線至AEM?* <br>***d.*** *您是使用CA簽名證書還是企業PKI?（非自簽名證書）*<br>***e.*** *您是否使用TLS而非SSL v3?*<br>***f.*** *您在註冊時正在驗證裝置和AEM上的註冊Token嗎？*<br> ***g.*** *您是否已分類所使用的資料，且裝置上沒有PII或PHI?*<br> ***h.*** *您是否已分類所使用的資料，且裝置上沒有個人識別資訊(PII)或受保護的健康資訊(PHI)?*<br> ***i.*** *您是否已配置監控電子郵件，並且是否已部署SOP來響應監控電子郵件和處理非ping設備？* |
| **存取控制** | ***a.您*** *內部是否已識別並管理角色型存取控制(RBAC)?* <br>***b.*** *您是否遵循最低權限原則，使用Adobe的最佳實務來提供對作者、管理員和播放器的存取權？* |

### 下載安全檢查清單{#download-checklist}

若要下載AEM Screens安全性檢查清單，請按一下[這裡](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf)。

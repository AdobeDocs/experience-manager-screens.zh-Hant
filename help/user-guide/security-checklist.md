---
title: 安全性檢查清單
description: 透過問題和考量事項清單瞭解AEM Screens的主要安全性領域。
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# AEM Screens安全性檢查清單 {#security-checklist}

AEM Screens安全性檢查清單頁面說明主要安全性區域，並提供問題和考量事項檢查清單。

## 檢查清單表格 {#checklist-table}

| **安全區域** | **檢查清單** | **是/否/NA** |
|---|---|---|
| **AEM和Screens軟體更新** | **答：** *是否已套用最新的Adobe Experience Manager (AEM) Service Pack？* <br>**b.** *是否已套用最新的AEM Screens Feature Pack？* <br>**c.** *您使用最新可用的AEM Screens Player軟體嗎？ [AEM Screens播放器下載](https://download.macromedia.com/screens/)？* |
| **實體安全性** | **答：** *您是否已停用所有不必要的連線埠？* <br>**b.** *您是否已保護接線與硬體？* <br>**c.** *您是否使用任何容器（如適用）？* |
| **網路安全性** | **答：** *您是否為招牌裝置使用隔離的子網路？* <br>**b.** *隔離的子網路是否允許存取必要的端點，包括AEM、Adobe Analytics或其他必要的服務？* <br>**c.** *您是否使用企業最佳實務來保護您的Wi-Fi？* <br>**d.** *如果使用同步播放，您是否只允許在主要裝置上使用WebSocket的TCP 24503？* <br>**e.** *您是否已解除封鎖播放器裝置的IP位址範圍，讓只有授權裝置才能存取編寫執行個體上的註冊服務？* |
| **作業系統安全性** | **答：** *您是否已升級至作業系統的最新版本，並套用所有必要的安全性修補程式？* <br>**b.** *您是否已停用所有不必要的服務並移除不必要的應用程式？* <br>**c.** *您是否已將裝置註冊到裝置管理以強制執行企業原則？* <br>**d.** *您是否已將裝置鎖定至單一應用程式（播放器）資訊站？* <br>**e.** *您是否已制定標準作業程式(SOP)，以便隨著時間推移安裝作業系統安全性更新？*<br>**f.***您是否遵循使用中作業系統的安全性最佳實務，例如防惡意程式碼軟體、非系統管理使用者？* |
| **應用程式安全性** | **答：** *您是否針對生產環境停用管理員UI、管道切換器和活動UI？* <br>**b.** *您是否將生產環境的記錄層級降到最低？* <br>**c.** *您使用https連線到AEM嗎？* <br>**d.** *您是否使用CA簽署的憑證或企業PKI？ （不是自我簽署憑證）*<br>**e.***您使用TLS而非SSL v3嗎？*<br>**f.** *註冊時，您是否正在裝置和AEM上驗證註冊權杖？*<br> **g.** *您是否將正在使用的資料分類，而且裝置上沒有PII或PHI？*<br> **h.** *您是否已分類正在使用的資料，且裝置上沒有個人識別資訊(PII)或受保護的健康資訊(PHI)？*<br> **i.** *您是否已設定監視電子郵件？ 您有回應監控電子郵件和處理非釘選裝置的SOP嗎？* |
| **存取控制** | **答：** *您是否有內部識別並管理的角色型存取控制(RBAC)？* <br>**b.** *您是否遵循Adobe最佳實務為作者、管理員和玩家提供存取許可權的最低許可權原則？* |

### 下載安全性檢查清單 {#download-checklist}

若要下載AEM Screens安全性檢查清單，請按一下 [此處](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).

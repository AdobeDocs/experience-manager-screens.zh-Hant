---
title: 安全核對表
seo-title: Security Checklist
description: 本頁介紹了主要安全領域，並列出了問題和注意事項。
seo-description: The page describes Security Checklist
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# AEM Screens安全檢查表  {#security-checklist}

AEM Screens安全檢查表頁介紹了關鍵安全領域，並列出了問題和注意事項。

## 核對清單表 {#checklist-table}

| **安全區** | **核對表** | **是/否/不適用** |
|---|---|---|
| **和屏AEM幕軟體更新** | ***a.*** *是否已應用最新的Adobe Experience Manager(AEM)服務包？* <br>***b.***  *是否已應用最新的AEM Screens功能包？* <br>***c.*** *您是否使用最新的AEM Screens播放器軟體 [AEM Screens播放器下載](https://download.macromedia.com/screens/)?* |
| **物理安全** | ***a.*** *是否已禁用所有不必要的埠？* <br>***b.***  *您是否保護了佈線和硬體？* <br>***c.*** *是否使用任何容器（如果適用）?* |
| **網路安全** | ***a.*** *您是否正在為標牌設備使用隔離子網？* <br>***b.***  *隔離子網是否允許訪問所需的端點，AEM包括Adobe Analytics或其他必需服務？* <br>***c.*** *您是否使用企業最佳實踐保護了您的Wi-Fi?* <br>***d.*** *如果使用同步播放，是否僅允許主設備上的WebSocket使用TCP 24503?* <br>***e.*** *您是否已解除阻止播放器設備的IP地址範圍，以便只有授權的設備才能訪問作者的註冊服務？* |
| **作業系統安全** | ***a.*** *您是否已升級到最新版本的作業系統並應用了所有必要的安全修補程式？* <br>***b.*** *您是否禁用了所有不必要的服務並刪除了不必要的應用程式？* <br>***c.*** *您是否已將設備註冊到設備管理中以實施企業策略？* <br>***d.*** *是否已將設備鎖定到單個應用程式（播放器）亭？* <br>***e.*** *您是否已準備好標準操作過程(SOP)，以隨時間推移安裝作業系統安全更新？*<br>***f*** *您是否遵循了使用中的作業系統的安全最佳做法，如防惡意軟體軟體、非管理用戶？* |
| **應用程式安全** | ***a.*** *是否禁用了生產管理UI、Channel Switcher和Activity UI?* <br>***b.*** *是否已最小化生產日誌級別？* <br>***c.*** *是否使用https連接AEM?* <br>***d.*** *您使用的是CA簽名證書還是企業PKI? （非自簽名證書）*<br>***e.*** *是否使用TLS而不是SSL v3?*<br>***f*** *是否正在驗證設備上的註冊令牌，以及AEM在註冊時？*<br> ***g*** *您是否對正在使用的資料進行了分類，並且設備上不存在PII或PHI?*<br> ***h*** *您是否對正在使用的資料進行了分類，並且設備上不存在個人識別資訊(PII)或受保護的健康資訊(PHI)?*<br> ***我。*** *您是否配置了監視電子郵件，並且您是否具有SOP來響應監視電子郵件和處理非ping設備？* |
| **存取控制** | ***a.*** *您是否在內部識別和管理基於角色的訪問控制(RBAC)?* <br>***b.*** *您是否遵循了「最少權限」原則，使用Adobe提供的最佳做法向作者、管理員和玩家提供訪問權限？* |

### 正在下載安全檢查清單 {#download-checklist}

要下載AEM Screens安全檢查表，請按一下 [這裡](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf)。

---
title: AEM Screens專案角色與責任
seo-title: AEM Screens Project Roles  and Responsibilities
description: 此頁面說明AEM Screens專案角色和職責
seo-description: The page describes AEM Screens Project Roles  and Responsibilities
exl-id: 9377625b-529a-4b46-89d9-f526de398639
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 6%

---

# 專案角色與責任 {#roles-responsibilities}

身為經驗豐富的 AEM 實作者，您可能會看到這些角色被稱為&#x200B;*「作者」*、*「開發人員」*&#x200B;和&#x200B;*「IT/技術人員」*。

在典型的AEM Screens專案中，角色會進一步細化，因為每個角色在專案中都有重要用途。

下圖顯示本指南中提及的角色。

![](/help/assets/project-roles-revised.png)

>[!NOTE]
>
> 其中許多角色可能是內部或外包，視每個專案的設定方式而定。

## 定義角色 {#roles}

下節提供目標對象的概觀：

### Adobe {#adobe-audience}

Adobe包括Adobe Managed Services資源，例如CSE （客戶成功工程師）和Adobe支援。

### AEM 實作人員 {#aem-implementors}

AEM實作者負責執行開發和整合工作，以開發AEM的使用者體驗、自訂範本和後端整合。

透過此程式，系統也會擷取並傳遞處理最終客戶UX （使用者體驗）引數所需的自訂功能。

AEM實作者通常會在一段時間內分階段將自訂功能部署到位置。 例如，他們可能會先建立對基本回圈視訊或靜態圖形內容播放的支援。 下一個階段可能包括啟用透過動態範本和中繼資料標籤支援播放當地語系化內容的能力，而其他階段則包含透過觸控熒幕、感應器、動態觸發器等支援互動式元素。

### AV 整合廠商 {#av-integrators}

A/V整合商是硬體廠商/合作夥伴。 這是處理零售設計和網站準備的一方，包括硬體採購、設定和部署。 通常是簽約的協力廠商，可以存取網路營運中心(NOC)。 在許多情況下，A/V整合商是專案所有者，因為它在啟動後持續參與。

AV Integrator負責與終端客戶進行探索，以定義需求，決定設計、建置和有效管理數位看板硬體部署所需的專案範圍。

#### 考慮硬體合作夥伴 {#selecting-hardware-partner}

選擇合適的硬體合作夥伴至關重要。 下列問題必須考量：

1. 服務等級合約的條款為何？

1. 全球涵蓋範圍為何？

1. 是否提供24小時支援？

1. 如何管理這些裝置？

1. 什麼是主動式監視和警告系統？

### 商業策略師 {#business-strategist}

業務策略人員代表公司的決策者。 此角色主要參與探索和需求階段，也是專案的主要驅動因素。

他們負責定義需求和設定KPI量度。 業務策略可能如下所示：

* 行銷或，
* 銷售經理數位策略經理創意/內容管理。

創意和內容管理團隊與策略團隊密切合作，將需求轉化為客戶體驗。 它們推動整體UX設計和組織內容，以補充品牌。

創意和內容管理可能如下所示：

* 創意公司或，
* 品牌管理員

### 專案經理 {#project-managers}

專案經理通常會管理AEM Screens部署的整個部署。 專案經理是整個指定專案實作的牽頭人，負責設定時間表、處理團隊需求和溝通、應對挑戰，並確保目標得以實現。

>[!NOTE]
>
>若要詳細瞭解數位看板專案的不同角色和責任以及目標對象，請造訪 **[專案角色與責任](https://helpx.adobe.com/experience-manager/6-5/screens/using/project-roles-responsibilities.html)**.


## 專案階段 {#project-stages}

為了支援成功的數位看板部署，通常會將專案分成3個階段。  這些階段通常稱為 **天**. 這些不是常值，而是專案每個主要階段的指派。

1. 第一個階段稱為 *第0天*. 此階段包含完整定義專案範圍所需的所有售前和探索工作。
1. 第二個階段， *第一天*，是指部署作業中包含的所有活動。
1. 第三個也是最後一個階段 *第二天* 指所有持續運作和支援元素，作為整體解決方案的一部分。

>[!NOTE]
>
>雖然本指南主要強調&#x200B;*第一天*&#x200B;和&#x200B;*第二天*，但要執行一個成功的數位告示牌專案，必須注意全部三個階段。
>
>觀看其他影片： **[專案管理與部署](https://helpx.adobe.com/experience-manager/6-5/screens/using/project-management-and-deployment.html)** 瞭解專案前期製作、專案啟動和專案進度。

## RACI圖表 {#raci-chart}

以下是使用角色定義的範例RACI圖表。

>[!NOTE]
>
>此圖表並非為了精確遵循，但提供AEM Screens專案中常見任務和考量事項的範例。

### RACI定義 {#raci-definitions}

* **負責的**：完成任務所需完成的工作。

* **負責**：委派工作，並且是在任務完成前最後稽核該任務的一方。

* **已諮詢**：檢閱任務或交付專案以提供輸入。

* **已通知**：隨時瞭解任務進度，但不參與交付專案的詳細資訊。

以下是使用角色定義的範例RACI圖表，並提供AEM Screens專案中常見任務和考量事項的範例。

下表總結列出 **第0天：售前注意事項**：

| **階段** | **A/V整合器** | **AEM實作人員** | **業務策略** | **內容管理** |
|---|---|---|---|---|
| 團隊組成與廠商選擇 | I | I | RA | RA |
| 角色與職責協定 | RA | RA | RA | RA |
| 與策略目標一致 | CI | I | RA | RA |
| 報告需求和ROI識別 | I | C | RA | C |
| 現場造訪與硬體需求 | RA | I | C | C |
| 支援程式定義 | C | I | RA | I |
| 定義工作範圍和專案計畫 | RA | RA | C | C |

下表總結列出 **第一天：專案實作（應用程式設計）**：

| **階段** | **A/V整合器** | **AEM實作人員** | **業務策略** | **內容管理** |
|---|---|---|---|---|
| 角色與職責協定 | RA | RA | RA | RA |
| 與專案計畫及排程保持一致 | RA | RA | C | C |
| 評估目前的伺服器環境 | I | RA | I | I |
| UX設計需求 | I | RA | C | RA |
| 技術需求驗證 | I | RA | RA | C |
| 架構設計 | I | RA | I | I |
| 使用UI設計驗證資料結構 | I | RA | C | C |
| 應用程式開發 | RA | RA | RA | RA |
| AEM Screens專案設定 | I | RA | C | I |
| Analytics實施 | I | RA | C | - |
| 測試和部署 | RA | C | RA | I |
| 伺服器設定 | I | RA | I | I |
| 內容更新計畫 | I | RA | C | C |
| 計畫試生產到生產轉換 | RA | RA | I | I |
| 知識轉移 | RA | RA | I | I |

下表總結列出 **第一天：專案實作（零售整備）**：

| **階段** | **A/V整合器** | **AEM實作人員** | **業務策略** | **內容管理** |
|---|---|---|---|---|
| 硬體訂購與儲存 | RA | I | I | I |
| 零售入門排程 | I | I | C | RA |
| 中繼使用者驗收測試 | I | C | RA |  |
| 硬體大量組態 | RA | I | C | I |
| 啟動後支援協定 | RA | C | RA | C |

下表總結列出 **第一天：第一天：專案實作（硬體）**：

| **階段** | **A/V整合器** | **AEM實作人員** | **業務策略** | **內容管理** |
|---|---|---|---|---|
| 角色與職責協定 | RA | RA | RA | RA |
| 零售設計包括佈線作業 | - | - | - | - |
| 播放器硬體選擇 | RAC | - | - | - |
| 主裝置的裝置管理 | RA | I | - | - |
| 裝置訂購與儲存與設定 | RA | CI | I | - |
| 支援程式定義 | RA | I | RA | C |

>[!NOTE]
>
>角色會在第二天變更（啟動後支援）。

* **作者**：內容管理+策略

* **開發人員**：通常是AEM Screens實作團隊的成員，或移轉至內部開發團隊

* **技術人員**：由AV整合商簽約或屬於同一家公司。

下表總結列出 **第二天：上市後支援RACI圖表**：

| **階段** | **作者** | **開發人員** | **技術人員** |
|---|---|---|---|
| *第二天：上市後支援* |
| 角色與職責協定 | RA | RA | RA |
| 第1級支援 | I | I | RA |
| 第2級支援 | I | C | RA |
| 第3級支援 | I | RA | C |
| 內容更新 | RA | I | I |
| 評估UX成功率並找出需改善的領域 | RA | C | I |

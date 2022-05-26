---
title: 蒂森玩家
description: 本頁介紹Tizen Player的安裝和工作。
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: 8d4a7b2bc436d822c673a00437ee895c8ef5cb6f
workflow-type: tm+mt
source-wordcount: '1242'
ht-degree: 0%

---

# 實現Tizen播放器 {#tizen-player}

## 安裝Tizen Player {#installing-tizen-player}

按照以下步驟為AEM Screens實施Tizen Player:

1. 導航到 [AEM Screens播放器下載](https://download.macromedia.com/screens/) 下載Tizen播放器。

1. 安裝Tizen播放器 *(.zip)* 檔案。

## 設定http伺服器 {#setting-local-server}

>[!NOTE]
> 解壓zip檔案，並通過 `http server`。 ( `http server` 不需要是本地或Apache伺服器)。

請遵循下列步驟：

1. 複製兩個提取的檔案，如 `AEMScreensPlayer.wgt` 和 `sssp_config.xml` 到本地Apache Web伺服器的根目錄。

   >[!NOTE]
   >的 `AEMScreensPlayer.wgt`是Tizen播放器的實際應用 `sssp_config.xml` 包含有關此映射的資訊，可幫助您將其安裝到Tizen設備上。

1. 獲取本地HTTP伺服器的IP或URL(以及包含步驟2中提取的檔案的資料夾的路徑（如果提取到子資料夾而不是根資料夾）

1. Tizen播放器從本地伺服器下載安裝程式。

### 命名Tizen播放器 {#name-tizen}

您可以為Tizen播放器指定用戶友好的設備名稱，從而將指定的設備名稱發送給Adobe Experience Manager(AEM)。 此功能不僅允許您命名Tizen播放器，還允許您輕鬆分配適當的內容。

>[!NOTE]
>您只能在註冊前選擇播放器名稱。 註冊玩家後，玩家名稱將不能再更改。

按照以下步驟配置Tizen播放器中的名稱：

1. 按一下遙控器上的菜單按鈕。
1. 導航到 **網路** —> **設備名稱** 為播放器指定名稱。

### 在Samsung設備上配置更新 {#config-updates}

按照Samsung設備上的以下步驟在設備上完成AEM Screens播放器的安裝：

1. 導航到Samsung設備並開啟。

1. 按一下 **菜單** 按鈕，向下滾動到 **系統** 的下界。

1. 向下滾動並選擇 **通過** 選項並將其更改為 **URL啟動程式** 的雙曲餘切值。
   ![影像](/help/user-guide/assets/tizen/rms-2.png)

1. 設定URL啟動程式後，按 **首頁** 按鈕。

1. 導航到 **URL啟動程式設定** 並輸入本地主機伺服器的IP地址，然後按一下 **完成**。
   >[!NOTE]
   >Tizen播放器應能連接到http伺服器。

1. 現在，AEM Screens播放器應自動在您的三星設備上安裝和啟動。

   >[!NOTE]
   >Tizen設備和 `http` 伺服器應該能夠相互連接，即伺服器應該可以訪問到Tizen播放器。


## 免除SameSite Cookie問題的用戶代理 {#exempting-user-agents}

>[!IMPORTANT]
>**本節適用於Adobe Experience Manager(AEM)6.5.5和AEM6.5.7**
>有些瀏覽器引擎與 *SameSite=無* 在6.5到6.7頒發的登AEM錄令牌中使AEM用的屬性。通常，通過將瀏覽器升級到最新的可用版本可以解決此問題。 在某些情況下，可能無法進行此類升級，例如，使用智慧顯示器、機頂盒或具有嵌入式瀏覽引擎的其他設備。

按照以下步驟，在使用 *SameSite=無*:

1. 升級到Adobe Experience Manager(AEM)Service Pack 6.5.7。

1. 重新啟AEM動後，轉到 `/system/console/configMgr` 並搜索 **Adobe花崗岩令牌驗證處理程式**。 設定 **同一站點** 值 **無**。

1. 您應看到新選項 *要免除類似屬性的用戶代理*。 使用與不相容的用戶代理對應的規則運算式來填充 *SameSite=無* 屬性。
   >[!NOTE]
   >請參閱 [SameSite=無：已知不相容的客戶端](https://www.chromium.org/updates/same-site/incompatible-clients) 的子菜單。 對於Tizen玩家，使用regex: `(.*)Tizen(.*)`。

1. 根據您的6.5.5及以上實例註冊TizenAEM播放器，它應正常註冊和顯示內容。

## 遠程設定Tizen Player {#remote-provisioning}

遠程配置Tizen Player使您無需費盡心機即可部署成百上千個三星Tizen顯示器。 它避免了使用伺服器URL和批量註冊碼等參數來配置每個播放器的繁瑣的人工操作，在螢幕as a Cloud Service配置雲模式和雲令牌的情況下。

此功能允許您遠程配置Tizen播放器，並可根據需要集中更新這些配置。 你只需要 `HTTP` 用於承載Tizen應用程式的伺服器 `(wgt and xml file)` 和文本編輯器以保存 `config.json` 參數。

確保已在Tizen設備上配置了URL啟動程式地址，即「Home Button —> URL Launcher設定」。
在 `HTTP` 承載Tizen應用程式的伺服器，將檔案 `config.json` 與 `wgt` 的子菜單。 檔案名必須為 `config.json`。
Tizen播放器將安裝，啟動時（以及每次重新啟動）將檢查並應用 `config.json` 的子菜單。

### JSON策略示例 {#example-json}

```java
{
  "server":  "http://your-aem-instance.com:4502",
  "registrationKey": "AdobeRocks!!",
  "enableAdminUI": true,
  "enableOSD": true,
  "enableActivityUI": true
}
```

### 策略屬性和用途 {#policy-attributes}

下表概述了策略及其功能。

>[!NOTE]
>策略配置將得到嚴格強制執行，不會在播放器的管理UI中手動覆蓋。 要允許對特定策略進行手動播放器配置，請不要在策略配置中指定策略，例如，如果要允許對重新啟動計畫進行手動配置，請不要指定密鑰 `rebootSchedule` 的子菜單。 每次重新載入播放器時都會讀取策略配置。

| **策略名稱** | **目的** |
|---|---|
| 伺服器 | 到Adobe Experience Manager(AEM)伺服器的URL。 |
| 註冊密鑰 | 用於使用預共用密鑰對設備進行批量註冊。 |
| 解析度 | 設備的解析度。 |
| 重新引導計畫 | 重新啟動播放器的計畫。 |
| enableAdminUI | 啟用Admin UI以在現場配置設備。 在完全配置並在生產中將其設定為false。 |
| 啟用OSD | 啟用通道切換器UI，以便用戶在設備上切換通道。 在完全配置並投入生產後，請考慮將其設定為false。 |
| enableActivityUI | 啟用以顯示下載和同步等活動的進度。 在完全配置並投入生產後啟用故障排除和禁用。 |
| 雲模式 | 如果希望Tizen播放器連接到螢幕as a Cloud Service，則設定為true。 設定為false以連接到AMS或on-Prem AEM。 |
| 雲令牌 | 註冊令牌，用於根據螢幕as a Cloud Service註冊。 |


## 將Tizen設備註冊到Samsung Remote Management Service(RMS) {#enroll-tizen-device-rms}

按照以下步驟將Tizen設備註冊到Samsung Remote Management Service(RMS)並遠程配置URL啟動程式：

>[!NOTE]
>驗證網路設定和監視器。

1. 導航到 **菜單** -> **網路** -> **伺服器網路設定** 按 **輸入**。

1. 導航至伺服器地址並鍵入MagicInfo URL訪問，然後按 **完成**。

1. 設定TLS（如果需要）。 導航到埠，然後從伺服器中選擇埠號，然後按一下 **保存**。

1. 導航到 **設備** 頁籤，並檢查您剛配置的設備。 找到設備後，按一下複選框並選擇 **批准**。

   >![影像](/help/user-guide/assets/tizen/rms-3.png)

1. 填寫所需資訊並選擇設備組。 按一下 **確定** 完成審批流程。

   >![影像](/help/user-guide/assets/tizen/rms-7.png)

1. 一旦設備獲得批准，它應出現在設備清單中。 按一下 *資訊* 按鈕， **我**，如下圖所示。

   >![影像](/help/user-guide/assets/tizen/rms-6.png)

1. 將顯示設備資訊對話框。 選擇 **設備資訊** 按鈕 **編輯**。

   >![影像](/help/user-guide/assets/tizen/rms-5.png)

1. 編輯設備選項並選擇 **設定** 頁籤。 導航到 **URL啟動程式** 並輸入承載wgt和 `SSSP config file` 安裝 `SSSP` 如下圖所示。

   ![影像](/help/user-guide/assets/tizen/rms-9.png)

1. 按一下 **保存** 的子菜單。

### 使用螢幕遙控器 {#using-remote-control}

AEM Screens提供遠程控制功能。 在此處瞭解有關此功能的詳細資訊： [螢幕遙控](implementing-remote-control.md)

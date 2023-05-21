---
title: 實施Windows 10 Player
seo-title: Implementing Windows 10 Player
description: 按照本頁瞭解有關配置AEM ScreensWindows 10播放器的資訊。
seo-description: Follow this page to learn about configuring AEM Screens Windows 10 player.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: Administering Screens, Windows Player
role: Admin
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: 97bc64ce3c01ac2de301b17bf9f8610662d45f88
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 1%

---

# 實施Windows 10 Player {#implementing-windows-player}

本節介紹配置AEM ScreensWindows 10播放器。 它提供了配置檔案的資訊以及可用選項以及用於開發和測試的設定的建議。

## 安裝Windows Player {#installing-windows-player}

要實施Windows Player forAEM Screens，請安裝Windows Player forAEM Screens。

訪問 [**6AEM.5播放器下載**](https://download.macromedia.com/screens/) 的子菜單。

>[!NOTE]
>Windows播放器中沒有窗口模式。 它總是全屏模式。

### 設定AEM Screens6.5.5 Service Pack環境 {#fp-environment-setup}

>[!NOTE]
>如果使用的是AEM Screens6.5.5 Service Pack，則必須為Windows播放器設定環境。

設定 **登錄令牌Cookie的SameSite屬性** 從 **松** 至 **無** 從 **Adobe Experience ManagerWeb控制台配置** 和發佈AEM實例。

請遵循下列步驟：

1. 導航到 **Adobe Experience ManagerWeb控制台配置** 使用 `http://localhost:4502/system/console/configMgr`。

1. 搜索 *Adobe花崗岩令牌驗證處理程式*。

1. 設定 **登錄令牌Cookie的SameSite屬性** 從 **松** 至 **無**。
   ![影像](/help/user-guide/assets/granite-updates.png)

1. 按一下「**儲存**」。

### Ad-Hoc方法 {#ad-hoc-method}

Ad-Hoc方法允許您安裝最新的Windows Player(*.exe*)。 訪問 [**6AEM.5播放器下載**](https://download.macromedia.com/screens/) 的子菜單。

下載應用程式後，請按照播放器上的步驟完成即席安裝：

1. 長按左上角以開啟管理面板。
1. 導航到 **配置** 從左側操作菜單中，輸入要連接到的實AEM例的位置（地址），然後按一下 **保存**。
1. 導航到 **設備** **註冊** 連結以檢查設備註冊過程的狀態。

>[!NOTE]
>
>如果 **州** 是 **已註冊**，您會注意到 **設備ID** 將填充。
>
>如果 **州** 是 **未註冊**，可以使用 **令牌** 註冊設備。

## 命名Windows Player {#name-windows}

您可以為Windows播放器指定用戶友好的設備名稱，從而將指定的設備名稱發送給Adobe Experience Manager(AEM)。 此功能不僅允許您命名Windows播放器，還允許您輕鬆分配適當的內容。

>[!NOTE]
>您只能在註冊前選擇播放器名稱。 註冊玩家後，玩家名稱將不能再更改。

按照以下步驟在Windows播放器中配置名稱：

1. 按一下 **開始** —> **運行**
1. 輸入 `system.cpl`
1. 使用電腦名稱頁籤設定電腦的主機名

## 更改Windows Installer中的預設選項 {#changing-default-options}

按照本部分瞭解如何更改Windows Installer中的預設選項和可用自定義項清單。

## 使用CLI(PowerShell)進行安裝 {#install-powershell}

1. 建立自定義位置 **專用** 例如：
   `C:\Users\User\screens-player`)
1. 安裝
   `aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\screens-player`
1. 開啟
   `Start-Process C:\Users\User\screens-player\AEMScreensPlayer.exe`

**範例**

```shell
C:\Users\User\Downloads> mkdir screens-player

C:\Users\User\Downloads> .\aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\Downloads\screens-player

C:\Users\User\Downloads> Start-Process C:\Users\User\Downloads\screens-player\AEMScreensPlayer.exe
```

## Windows Player批量註冊 {#bulk-registration}

在實施Windows播放器時，不需要手動配置每個播放器。 相反，您可以在配置JSON檔案經過測試並準備部署後更新它。

配置將確保所有玩家ping配置檔案中提供的同一伺服器。 您仍必須手動註冊每個玩家。

按照以下步驟配置Windows 10 Player:

1. 安裝Windows Player。
1. 在下查找配置檔案 ***%appdata%\com.adobe.aem.screens.player\config***。
1. 使用下面的資訊更新配置JSON，然後將同一資料夾複製到播放器所在的所有系統。

### 策略屬性 {#policy-attributes}

下表匯總了策略屬性，其中包含供參考的示例策略JSON:

| **策略名稱** | **用途** |
|---|---|
| 伺服器 | 到Adobe Experience Manager(AEM)伺服器的URL。 |
| 解析度 | 設備的解析度。 |
| 重新引導計畫 | 重新啟動播放器的計畫。 |
| enableAdminUI | 啟用Admin UI以在現場配置設備。 在完全配置並在生產中將其設定為false。 |
| 啟用OSD | 啟用通道切換器UI，以便用戶在設備上切換通道。 在完全配置並投入生產後，請考慮將其設定為false。 |
| enableActivityUI | 啟用以顯示下載和同步等活動的進度。 在完全配置並投入生產後啟用故障排除和禁用。 |

#### 示例策略JSON檔案 {#example-policy-json-file}

```
{
    "server": "https://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

## 啟用Kiosk模式 {#enabling-kiosk-mode}

在部署Windows播放器時，必須啟用Kiosk模式，以便Windows案頭上不顯示其他應用程式或任務欄。

>[!CAUTION]
>
>Adobe建議使用設備管理解決方案來啟用Windows自助伺服器。 如果您沒有啟用Kiosk模式的設備管理解決方案，請按照以下步驟操作。 此方法使用Windows 10企業版和教育類版中提供的Shell Launcher功能。 Microsoft推薦的任何非UWP應用手段也可用於啟用Kiosk，特別是在其他Windows版本上。

按照以下步驟啟用Kiosk模式：

>[!NOTE]
>
>在執行以下步驟之前，請確保使用Windows 10企業版或教育版。

1. 啟用Shell啟動程式。

   請參閱部分 ***配置Shell啟動程式*** 在 **[殼啟動程式](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** Windows支援頁面，以獲取更多資訊。

1. 建立一個非管理用戶（如果您還沒有），以用於Kiosk。 這可以是本地用戶或域用戶。
1. 從中為該Kiosk用戶安裝Windows播放器 [AEM Screens播放器下載](https://download.macromedia.com/screens/) 的子菜單。
1. 請參閱 [使用Shell Launcher建立Windows 10自助服務站](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) 以修改PowerShell指令碼以獲取詳細資訊。

   修改PowerShell指令碼，將用戶名替換為您建立的用戶名。 確保應用程式執行檔的路徑正確。 這將將自定義shell設定為Kiosk用戶的windows播放器應用程式，並將其他用戶的預設設定設定為explorer.exe。

1. 以管理員身份運行PowerShell指令碼。
1. 重新啟動並登錄Kiosk用戶和播放器應用程式應立即啟動。

### 疑難排解 {#troubleshooting}

如果您以Kiosk用戶身份登錄時出現黑屏，則表示您可能錯誤地指定了Windows播放器執行檔的路徑。 以管理員身份登錄，驗證並重新運行指令碼。

Windows播放器的預設安裝路徑是：

***C:\Users\&amp;lt；您的用戶>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens播放器.exe***

連結中的示例指令碼將啟用和禁用自定義shell。 因此，您可能需要將指令碼拆分為兩個，並啟用/禁用以下適用行：

>[!NOTE]
>
>在某些Windows環境中， PowerShell指令碼可能受策略（尤其是未簽名的指令碼）的限制。 要運行指令碼，可能需要暫時禁用並重新啟用此限制以運行指令碼。 開啟PowerShell窗口，然後使用這些命令。
>
>*set-execution策略非限制*  — 臨時取消限制
>
>*set-executionpolicy受限制*  — 在運行指令碼後重新啟用限制

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### 使用螢幕遙控器 {#using-remote-control}

AEM Screens提供遠程控制功能。 在此處瞭解有關此功能的詳細資訊： [螢幕遙控](implementing-remote-control.md)
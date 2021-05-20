---
title: 實作Windows 10 Player
seo-title: 實作Windows 10 Player
description: 請詳閱本頁面，了解如何設定AEM Screens Windows 10播放器。
seo-description: 請詳閱本頁面，了解如何設定AEM Screens Windows 10播放器。
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: 管理螢幕， Windows Player
role: Administrator
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 1%

---

# 實作Windows 10 Player {#implementing-windows-player}

本節說明如何設定AEM Screens Windows 10播放器。 它提供設定檔案的資訊，以及可用選項和建議，說明要用於開發和測試的設定。

## 安裝Windows Player {#installing-windows-player}

若要實作適用於AEM Screens的Windows Player，請安裝適用於AEM Screens的Windows Player。

請造訪&#x200B;[**AEM 6.5播放器下載**](https://download.macromedia.com/screens/)頁面。

>[!NOTE]
>Windows播放器中沒有視窗模式。 一律為全螢幕模式。

### 設定AEM Screens 6.5.5 Service Pack {#fp-environment-setup}的環境

>[!NOTE]
>如果您使用AEM Screens 6.5.5 Service Pack，則必須為Windows Player設定環境。

從&#x200B;**Lax**&#x200B;將登入代號Cookie **的** SameSite屬性從&#x200B;**Adobe Experience Manager Web Console設定為** None **在所有AEM製作和發佈執行個體上設定**。

請遵循下列步驟：

1. 導覽至&#x200B;**Adobe Experience Manager Web Console
使用`http://localhost:4502/system/console/configMgr`進行配置**。

1. 搜尋&#x200B;*AdobeGranite代號驗證處理常式*。

1. 將登入代號Cookie **的** SameSite屬性從&#x200B;**Lax**&#x200B;設定為&#x200B;**None**。
   ![影像](/help/user-guide/assets/granite-updates.png)

1. 按一下「**儲存**」。

### 臨機方法{#ad-hoc-method}

Ad-Hoc方法可讓您安裝最新的Windows Player(*.exe*)。 請造訪&#x200B;[**AEM 6.5播放器下載**](https://download.macromedia.com/screens/)頁面。

下載應用程式後，請依照播放器上的步驟完成臨機安裝：

1. 長按左上角以開啟「管理面板」。
1. 從左側操作菜單導航到&#x200B;**配置**，並輸入要連接的AEM實例的位置（地址），然後按一下&#x200B;**保存**。
1. 從左側操作菜單導航到&#x200B;**Device** **Registration**&#x200B;連結，以檢查設備註冊過程的狀態。

>[!NOTE]
>
>如果&#x200B;**State**&#x200B;為&#x200B;**REGISTERED**，您會注意到將填入&#x200B;**Device id**&#x200B;欄位。
>
>如果&#x200B;**State**&#x200B;為&#x200B;**UNECROSTERD**，則可以使用&#x200B;**Token**&#x200B;註冊設備。

## 更改Windows Installer {#changing-default-options}中的預設選項

請按照本節了解如何更改Windows Installer中的預設選項和可用自定義項清單。

## 使用CLI(PowerShell){#install-powershell}進行安裝

1. 為Screens Player建立專用的&#x200B;**自訂位置，例如：**
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

## Windows Player的批量註冊{#bulk-registration}

實作Windows播放器時，您不需要手動設定每個播放器。 反之，您可以在設定JSON檔案經過測試並準備好進行部署後加以更新。

配置將確保所有播放器ping配置檔案中提供的相同伺服器。 您仍須手動註冊每個播放器。

請依照下列步驟來設定Windows 10 Player:

1. 安裝Windows Player。
1. 在&#x200B;***%appdata%\com.adobe.aem.screens.player\config.json***&#x200B;下找到配置檔案。
1. 使用下列資訊更新設定JSON，然後複製相同的資料夾至播放器所在的所有系統。

### 策略屬性{#policy-attributes}

下表匯總了具有示例策略JSON的策略屬性以供參考：

| **策略名稱** | **用途** |
|---|---|
| 伺服器 | Adobe Experience Manager(AEM)伺服器的URL。 |
| 解析度 | 裝置的解析度。 |
| rebootSchedule | 重新啟動播放器的排程。 |
| enableAdminUI | 啟用管理員UI以在網站上設定裝置。 在完全設定後並在生產環境中設為false。 |
| enableOSD | 啟用通道切換器UI，讓使用者在裝置上切換通道。 在完全設定並在生產環境中設定為false時，請考慮將其設為false。 |
| enableActivityUI | 啟用以顯示活動的進度，例如下載和同步。 完全設定後在生產環境中啟用疑難排解功能並加以停用。 |

#### 策略JSON檔案示例{#example-policy-json-file}

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

## 啟用Kiosk模式{#enabling-kiosk-mode}

在部署Windows播放器時，必須啟用Kiosk模式，這樣其他應用程式或任務欄就不會出現在Windows案頭上。

>[!CAUTION]
>
>Adobe建議使用裝置管理解決方案來啟用Windows適用的Kiosk。 如果您沒有啟用Kiosk模式的裝置管理解決方案，請依照下列步驟操作。 此方法使用Windows 10企業版和Edu中提供的Shell啟動器功能。 對於非UWP應用程式，Microsoft建議的任何其他方法也可以應用於啟用Kiosk，特別是在其他Windows版本上。

請依照下列步驟啟用Kiosk模式：

>[!NOTE]
>
>執行以下步驟之前，請確保您使用Windows 10企業版或教育版。

1. 啟用殼啟動器。

   有關詳細資訊，請參閱&#x200B;**[Shell啟動器](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)**&#x200B;頁中的&#x200B;***配置殼層啟動器***&#x200B;部分，該頁由Microsoft Windows支援提供。

1. 建立要用於資訊站的非管理用戶（如果您尚未建立）。 這可以是本機或網域使用者。
1. 從[AEM Screens Player下載](https://download.macromedia.com/screens/)頁面為Kiosk使用者安裝Windows Player。
1. 有關詳細資訊，請參閱[使用殼層啟動器建立Windows 10資訊站](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher)以修改PowerShell指令碼。

   修改PowerShell指令碼，將用戶名替換為您建立的用戶名。 確保應用程式執行檔的路徑正確。 這會將自訂殼層設為Kiosk使用者的Windows播放器應用程式，並將其他使用者的預設設為explorer.exe。

1. 以管理員身份運行PowerShell指令碼。
1. 重新啟動並登入，Kiosk使用者和播放器應用程式應該會立即啟動。

### 疑難排解 {#troubleshooting}

如果您以Kiosk用戶身份登錄時出現黑屏，則表示您可能錯誤指定了Windows Player執行檔的路徑。 以管理員身分重新登入，並驗證並重新執行指令碼。

Windows player的預設安裝路徑為：

***C:\Users\&amp;lt；您的用戶>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

連結中的範例指令碼將啟用和停用自訂殼層。 因此，您可能需要將指令碼拆分為兩個，並啟用/禁用以下適用行：

>[!NOTE]
>
>在某些Windows環境中， PowerShell指令碼可能受策略（尤其是未簽名的指令碼）的限制。 要運行指令碼，您可能需要暫時禁用並重新啟用此限制以運行指令碼。 開啟PowerShell窗口，然後使用這些命令。
>
>*set-executionpolicy unrestricted*  — 暫時移除限制
>
>*set-executionpolicy restricted*  — 在執行指令碼後重新啟用限制

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

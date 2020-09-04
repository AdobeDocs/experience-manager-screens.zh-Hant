---
title: 實作Windows 10 Player
seo-title: 實作Windows 10 Player
description: 請依照本頁來瞭解如何設定AEM Screens Windows 10播放器。
seo-description: 請依照本頁來瞭解如何設定AEM Screens Windows 10播放器。
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
translation-type: tm+mt
source-git-commit: 2ab8496cebb81864a8354ad5dcb8d72bc1e44c13
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 1%

---


# 實作Windows 10 Player {#implementing-windows-player}

本節說明如何設定AEM Screens Windows 10播放器。 它提供設定檔、可用選項和建議的資訊，說明要用於開發和測試的設定。

## 安裝Windows Player {#installing-windows-player}

若要實作適用於AEM畫面的Windows Player，請安裝適用於AEM畫面的Windows Player。

請造訪 [**AEM 6.5播放器下載頁面**](https://download.macromedia.com/screens/) 。

>[!NOTE]
>Windows Player中沒有窗口模式。 一律為全螢幕模式。

### 設定AEM Screens 6.5.5 Service Pack的環境 {#fp-environment-setup}

>[!NOTE]
>如果您使用AEM Screens 6.5.5 Service Pack，您必須為Windows Player設定環境。

將 **Adobe Experience Manager Web Console的登入Token Cookie的****SameSite屬性從** Lax **設為** None，從 **** Adobe Experience Manager Web主控台設定所有AEM作者和發佈例項上的SameSite屬性。

請遵循下列步驟：

1. 導覽至 **Adobe Experience Manager Web Console使用設定**`http://localhost:4502/system/console/configMgr`。

1. 搜尋 *Adobe Granite Token驗證處理常式*。

1. 將登入 **Token Cookie的SameSite屬性從****Lax設為****None**。
   ![影像](/help/user-guide/assets/granite-updates.png)

1. 按一下&#x200B;**「儲存」**。

### 臨機方法 {#ad-hoc-method}

臨機方法可讓您安裝最新的Windows Player(*.exe*)。 請造 [**訪AEM 6.5播放器下載頁面**](https://download.macromedia.com/screens/) 。

下載應用程式後，請依照播放器上的步驟完成臨機安裝：

1. 長按左上角以開啟管理面板。
1. 從左 **側動作功能表導覽至** 「設定」，然後輸入您要連線至的AEM例項的位置（位址），然後按一下「 **儲存」**。
1. 從左側的 **動作功能表導** 覽至「裝置註冊 **** 」連結，以檢查裝置註冊程式的狀態。

>[!NOTE]
>
>如果「 **狀態** 」為「已注 **冊**」，您會注意到 **「裝置id** 」欄位將會填入。
>
>如果狀 **態為****UNECRISTERED**，您可以使用 **Token** 來註冊裝置。

### 批量伺服器配置：使用一個配置註冊多個Windows 10播放器 {#bulk-server-configuration-registering-multiple-windows-players-with-one-configuration}

在安裝Windows播放器後，您可以使用一個配置註冊多個播放器。

>[!NOTE]
>
>**Windows Player大量註冊**
>
>實作Windows播放器時，您不需要手動設定每個播放器。 您可以在設定JSON檔案經過測試並準備好進行部署後，再加以更新。
>
>配置將確保所有播放器ping配置檔案中提供的同一伺服器。 您仍必須手動註冊每個播放器。

請依照下列步驟來設定Windows 10 Player:

1. 安裝Windows Player。
1. 在 ***%appdata%\com.adobe.aem.screens.player\config.json下尋找設定檔案***。
1. 使用下列資訊更新設定JSON，然後將相同資料夾複製到播放器所在的所有系統。

### 策略屬性 {#policy-attributes}

下表匯總了策略屬性，其中包含範例策略JSON以供參考：

| **原則名稱** | **目的** |
|---|---|
| 伺服器 | Adobe Experience Manager(AEM)伺服器的URL。 |
| 解析度 | 裝置的解析度。 |
| rebootSchedule | 重新啟動播放器的排程。 |
| enableAdminUI | 啟用管理員UI以在網站上設定裝置。 在完全設定並投入生產時，設為false。 |
| enableOSD | 啟用頻道切換器UI，讓使用者在裝置上切換頻道。 在完全設定後，請考慮在生產中設定為false。 |
| enableActivityUI | 啟用以顯示活動的進度，例如下載和同步。 啟用疑難排解功能，並在完全設定後在生產中停用。 |

#### 範例原則JSON檔案 {#example-policy-json-file}

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

當您部署Windows播放器時，請務必啟用Kiosk模式，以便其他應用程式或工作列不會出現在Windows案頭上。

>[!CAUTION]
>
>Adobe建議使用裝置管理解決方案來啟用Windows專用的資訊站。 如果您沒有裝置管理解決方案來啟用資訊站模式，請依照下列步驟進行。 此方法使用Windows 10企業版和教育版中提供的Shell Launcher功能。 Microsoft針對非UWP應用程式建議的任何其他方式也可套用至啟用Kiosk（尤其是其他Windows版本）。

請依照下列步驟啟用資訊站模式：

>[!NOTE]
>
>在遵循下列步驟之前，請確定您使用Windows 10企業版或教育版。

1. 啟用Shell Launcher。

   有關詳細信 ***息，請參閱Microsoft Windows支援*** 「在 **[](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** Shell Launcher中配置Shell Launcher」一節。

1. 建立非管理使用者（如果您尚未使用）以用於資訊站。 此用戶可以是本地用戶或域用戶。
1. 從 [AEM Screens Player下載頁面為該Kiosk使用者安裝Windows播放器](https://download.macromedia.com/screens/) 。
1. 如需詳 [細資訊，請參閱「使用Shell Launcher建立Windows 10kiosk](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) 」以修改PowerShell指令碼。

   修改PowerShell指令碼，將用戶名替換為您建立的用戶名。 確保應用程式執行檔的路徑正確。 這會將自訂shell設為kiosk使用者的Windows播放器應用程式，並將其他使用者的預設值設為explorer.exe。

1. 以管理員身份運行PowerShell指令碼。
1. 重新啟動並登入Kiosk使用者，播放器應用程式應該會立即啟動。

### 疑難排解 {#troubleshooting}

如果您以Kiosk使用者身分登入時出現黑幕，表示您可能未正確指定Windows播放器可執行檔的路徑。 以管理員身份登錄，驗證並重新運行指令碼。

Windows Player的預設安裝路徑為：

***C:\Users\&amp;lt;your user>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

連結中的範例指令碼將啟用和停用自訂殼層。 因此，您可能需要將指令碼拆分為兩行，並啟用／禁用以下適用行：

>[!NOTE]
>
>在某些Windows環境中， PowerShell指令碼可能受到策略（尤其是未簽名的指令碼）的限制。 要運行指令碼，您可能需要暫時禁用並重新啟用此限制以運行指令碼。 開啟PowerShell窗口，然後使用這些命令。
>
>*set-executionpolicy unrestricted* —— 暫時移除限制
>
>*set-executionpolicy restricted* —— 在執行指令碼後重新啟用限制

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```


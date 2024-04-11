---
title: 實作Windows 10 Player
description: 瞭解如何設定AEM Screens Windows 10播放器。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
docset: aem65
feature: Administering Screens, Windows Player
role: Admin
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: a8055c5f859e401f7b1da4f5d95f1268dee243ad
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 1%

---

# 實作Windows 10 Player {#implementing-windows-player}

本節說明如何設定AEM Screens Windows 10 Player。 它提供設定檔和可用選項的資訊，以及開發和測試使用哪些設定的建議。

## 安裝Windows Player {#installing-windows-player}

若要實作適用於AEM Screens的Windows Player，請安裝適用於AEM Screens的Windows Player。

造訪 [**AEM 6.5播放器下載**](https://download.macromedia.com/screens/) 頁面。

>[!NOTE]
>Windows Player中沒有視窗模式。 永遠是全熒幕模式。

### 為AEM Screens 6.5.5 Service Pack設定環境 {#fp-environment-setup}

>[!NOTE]
>如果您使用AEM Screens 6.5.5 Service Pack，請為Windows Player設定環境。

設定 **登入權杖Cookie的SameSite屬性** 從 **鬆散** 至 **無** 從 **Adobe Experience Manager Web主控台設定** 在所有AEM作者和發佈執行個體上。

請遵循下列步驟：

1. 瀏覽至 **Adobe Experience Manager Web主控台設定** 使用 `http://localhost:4502/system/console/configMgr`.

1. 搜尋 *AdobeGranite權杖驗證處理常式*.

1. 設定 **登入權杖Cookie的SameSite屬性** 從 **鬆散** 至 **無**.
   ![影像](/help/user-guide/assets/granite-updates.png)

1. 按一下「**儲存**」。

### 臨機方法 {#ad-hoc-method}

Ad-Hoc方法可讓您安裝最新的Windows Player (*.exe*)。 造訪 [**AEM 6.5播放器下載**](https://download.macromedia.com/screens/) 頁面。

下載應用程式後，請依照播放器上的步驟完成隨選安裝：

1. 長按左上角以開啟「管理」面板。
1. 瀏覽至 **設定** 從左側動作選單中輸入您要連線的AEM執行個體的位置（位址），然後按一下 **儲存**.
1. 導覽至 **裝置** **註冊** 從左側動作功能表連結，以便您檢視裝置註冊程式的狀態。

>[!NOTE]
>
>如果 **狀態** 是 **已註冊**，請注意 **裝置ID** 欄位會填入。
>
>如果 **狀態** 是 **未註冊**，您可以使用 **Token** 以註冊裝置。

## 命名Windows Player {#name-windows}

您可以將好記的裝置名稱指派給您的Windows播放器，藉此將指派的裝置名稱傳送給Adobe Experience Manager (AEM)。 此功能不僅可讓您為Windows播放器命名，也可讓您輕鬆指派適當的內容。

>[!NOTE]
>您只能在註冊之前選擇播放器名稱。 播放器註冊後，播放器名稱就無法再變更。

請依照下列步驟，在Windows Player中設定名稱：

1. 按一下 **開始** > **執行**.
1. 輸入 `system.cpl`.
1. 使用電腦名稱標籤來設定電腦的主機名稱。

## 變更Windows Installer中的預設選項 {#changing-default-options}

請依照本章節的說明進行，以便您瞭解如何變更Windows Installer中的預設選項以及可用的自訂清單。

## 使用CLI進行安裝(PowerShell) {#install-powershell}

1. 建立自訂位置 **專用** 例如，對於Screens播放器：
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

## 大量註冊Windows Player {#bulk-registration}

實作Windows Player時，您不需要手動設定每個播放器。 您可以在配置JSON檔案經過測試並準備好部署後進行更新。

此設定確保所有播放器都會偵測到設定檔案中提供的相同伺服器。 手動註冊每個播放器。

請依照下列步驟設定Windows 10 Player：

1. 安裝Windows Player。
1. 尋找下的設定檔 ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. 使用以下資訊更新設定JSON，然後將相同的資料夾複製到播放器所在的所有系統。

### 原則屬性 {#policy-attributes}

下表摘要列出原則JSON範例作為參考的原則：


| **原則名稱** | **用途** |
|---|---|
| 伺服器 | Adobe Experience Manager (AEM)伺服器的URL。 |
| 註冊金鑰 | 用於使用預先共用金鑰的大量裝置註冊。 |
| 解析度 | 裝置的解析度。 |
| rebootSchedule | 重新啟動播放器的排程。 |
| enableAdminUI | 啟用管理員UI來設定站台上的裝置。 在完全設定並投入生產後，設為false。 |
| enableOSD | 啟用頻道切換器UI，讓使用者在裝置上切換頻道。 在完全設定並投入生產後，請考慮將設為false 。 |
| enableactivityui | 啟用，以便顯示下載和同步等活動的進度。 啟用以進行疑難排解，並在完全設定後停用。 |
| cloudMode | 如果您希望Windows Player以as a Cloud Service方式連線至Screens，請設為true。 設為false可連線至AMS或內部部署AEM。 |
| cloudToken | 註冊Token以針對Screensas a Cloud Service註冊。 |

#### 原則JSON檔案範例 {#example-policy-json-file}

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

## 啟用資訊站模式 {#enabling-kiosk-mode}

部署Windows Player時，請務必啟用Kiosk模式，以免其他應用程式或工作列出現在Windows案頭上。

>[!CAUTION]
>
>Adobe建議使用裝置管理解決方案來啟用Windows的Kiosk。 如果您沒有裝置管理解決方案可啟用Kiosk模式，請依照下列步驟進行。 此方法使用Windows 10企業版和Edu中可用的殼層啟動器功能。 您也可以套用Microsoft針對非UWP應用程式建議的任何其他方法，以啟用Kiosk，尤其是在其他Windows版本上。

請依照下列步驟啟用Kiosk模式：

>[!NOTE]
>
>在依照下列步驟執行之前，請確定您使用的是Windows 10 Enterprise或Education。

1. 啟用殼層啟動器。

   另請參閱 ***設定殼層啟動器*** 在 **[殼層啟動器](https://learn.microsoft.com/en-us/windows/iot/iot-enterprise/customize/shell-launcher)** 詳細資訊，請參閱Microsoft®Windows支援頁面。

1. 建立一個非管理使用者（如果您還沒有的話），以用於Kiosk。 這可以是本機或網域使用者。
1. 從安裝該Kiosk使用者的Windows Player [AEM Screens播放器下載](https://download.macromedia.com/screens/) 頁面。
1. 另請參閱 [使用Shell啟動器建立Windows 10資訊站](https://learn.microsoft.com/en-us/windows/configuration/assigned-access/shell-launcher/?tabs=intune) 修改PowerShell指令碼以取得詳細資訊。

   修改PowerShell指令碼，讓您可以用您建立的使用者名稱取代使用者名稱。 請確定應用程式可執行檔的路徑正確無誤。 這會將自訂殼層設定為Kiosk使用者的Windows Player應用程式，並將其他使用者的預設設定為explorer.exe。

1. 以系統管理員身分執行PowerShell指令碼。
1. 重新開機並以Kiosk使用者身分登入，播放器應用程式應該會立即啟動。

### 疑難排解 {#troubleshooting}

如果您在以Kiosk使用者身分登入後出現黑屏，表示您可能未正確指定Windows Player可執行檔的路徑。 以管理員身分重新登入，然後驗證並重新執行指令碼。

Windows Player的預設安裝路徑為：

***C:\Users\&lt;your user=&quot;&quot;>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

連結中的範例指令碼會啟用和停用自訂殼層。 因此，請將指令碼分割為兩個並啟用/停用以下適用的行：

>[!NOTE]
>
>在某些Windows環境中，PowerShell指令碼可能會受到原則的限制（尤其是未簽署的指令碼）。 若要執行指令碼，請暫時停用並重新啟用此限制以執行指令碼。 開啟PowerShell視窗並使用這些指令。
>
>*`set-executionpolicy unrestricted`*  — 暫時移除限制。
>
>*`set-executionpolicy restricted`*  — 在執行指令碼後重新啟用限制。

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### 使用Screens遙控器 {#using-remote-control}

AEM Screens提供遠端控制功能。 若要進一步瞭解此功能，請前往這裡： [熒幕遙控器](implementing-remote-control.md)
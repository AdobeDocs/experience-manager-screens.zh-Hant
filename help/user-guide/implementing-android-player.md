---
title: 實作Android Player
seo-title: Android Player的實作
description: 請依照本頁瞭解Android Watchdog的實作，此解決方案可從當機中復原播放器。
seo-description: 請依照本頁瞭解Android Watchdog的實作，此解決方案可從當機中復原播放器。
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
translation-type: tm+mt
source-git-commit: 319a80a7fe3d68cbc16108eb302def390b445838
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 1%

---


# 實作Android Player {#implementing-android-player}

本節說明如何設定Android播放器。 它提供設定檔、可用選項和建議的資訊，說明要用於開發和測試的設定。

此外， **Watchdog** 是從當機中恢復播放器的解決方案。 應用程式需要向監視程式服務註冊，然後定期向其處於活動狀態的服務發送消息。 如果監視程式服務未在規定時間內收到保持活動消息，則服務會嘗試重新啟動設備以進行乾淨的恢復（如果它具有足夠的權限）或重新啟動應用程式。

## 安裝Android Player {#installing-android-player}

若要實作適用於AEM畫面的Android Player，請安裝適用於AEM畫面的Android Player。

請造訪 [**AEM 6.5播放器下載頁面**](https://download.macromedia.com/screens/) 。

### 設定AEM Screens 6.5.5功能套件及更新版本的環境 {#fp-environment-setup}

如果您使用AEM Screens 6.5.5 Feature Pack，則必須為Android Player設定環境。

請遵循下列步驟：

1. 導覽至 **Adobe Experience Manager Web Console使用設定**`http://localhost:4502/system/console/configMgr`。

1. 搜尋 *Adobe Granite Token驗證處理常式*。

1. 將登入 **Token Cookie的SameSite屬性從****Lax設為****None**。
   ![影像](/help/user-guide/assets/granite-updates.png)

1. 按一下&#x200B;**「儲存」**。


### 臨機方法 {#ad-hoc-method}

臨機方法可讓您安裝最新的Android Player(*.exe*)。 請造 [**訪AEM 6.5播放器下載頁面**](https://download.macromedia.com/screens/) 。

下載應用程式後，請依照播放器上的步驟完成臨機安裝：

1. 長按左上角以開啟管理面板。
1. 從左 **側動作功能表導覽至** 「設定」，然後輸入您要連線至的AEM例項的位置（位址），然後按一下「 **儲存」**。

1. 從左側的 **動作功能表導** 覽至「裝置註冊 **** 」連結，以檢查裝置註冊程式的狀態。

>[!NOTE]
>
>如果「 **狀態** 」為「已注 **冊**」，您會注意到 **「裝置id** 」欄位將會填入。
>
>如果狀 **態為****UNECRISTERED**，您可以使用 **Token** 來註冊裝置。

## 實作Android Watchdog {#implementing-android-watchdog}

由於Android的架構，重新啟動裝置需要應用程式具備系統權限。 為此，您需要使用製造商的簽名密鑰來簽署應用程式，否則看門狗會重新啟動播放器應用程式，而不會重新啟動裝置。

### 使用製造商金鑰的Android標誌 {#signage-of-android-apks-using-manufacturer-keys}

若要存取Android的某些特權API，例如 *PowerManager* 或 *HDMIControlServices*，您必須使用製造商的金鑰來簽署android apk。

>[!CAUTION]
>
>先決條件：
>
>您應先安裝Android SDK，然後再執行下列步驟。

請依照下列步驟，使用製造商的金鑰簽署Android應用程式：

1. 從Google Play或 [AEM Screens Player下載頁面下載應用程式](https://download.macromedia.com/screens/) 。
1. 從製造商取得平台金鑰以取得 *pk8* 和 *pem* 檔案

1. 使用尋找~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;，在android sdk中找到apksigner工具
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. 在Android sdk中尋找郵遞區號對齊工具的路徑
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensalfixed.apk
1. 使用 ***adb安裝將aemscreensaldium*** .apk安裝到設備

## Android Watchdog實作 {#android-watchdog-implementation}

跨Android監視程式服務是使用 *AlarmManager以cordova增效模組實作*。

下圖顯示了監視程式服務的實現：

![chlimage_1-31](assets/chlimage_1-31.png)

**1. 初始化** ：在初始化cordova增效模組時，會檢查權限，以查看我們是否擁有系統權限，進而查看重新啟動權限。 如果滿足這兩個條件，則會建立「待重新啟動的意圖」，否則會建立「待重新啟動的意圖」（基於其「啟動活動」）。

**2. Keep Alive Timer** A keep alive timer用於每15秒觸發一個事件。 在此情況下，您必須取消現有的待定意圖（以重新啟動或重新啟動應用程式），並在相同的60秒內註冊新的待定意圖（實際上是延遲重新啟動）。

>[!NOTE]
>
>在Android中， *AlarmManager* 用於註冊 *pendingIntents* ，即使應用程式當機且其警報傳送不精確於API 19(Kitkat)，仍可執行。 在計時器的間隔和 *AlarmManager的pendingIntent的警報之間**保持一定間隔* 。

**3. 應用程式當機** —在發生當機時，註冊於AlarmManager的「待重新啟動的pendingIntent for Reboot」不再重設，因此會執行應用程式的重新啟動或重新啟動（視cordova增效模組初始化時的可用權限而定）。

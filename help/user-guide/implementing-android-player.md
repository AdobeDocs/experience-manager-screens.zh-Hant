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
source-git-commit: b439cfab068dcbbfab602ad8d31aaa2781bde805
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 1%

---


# 實作Android Player {#implementing-android-player}

本節說明如何設定Android播放器。 它提供設定檔、可用選項和建議的資訊，說明要用於開發和測試的設定。

此外，**Watchdog**&#x200B;是從當機中恢復播放器的解決方案。 應用程式需要向監視程式服務註冊，然後定期向其處於活動狀態的服務發送消息。 如果監視程式服務未在規定時間內收到保持活動消息，則服務會嘗試重新啟動設備以進行乾淨的恢復（如果它具有足夠的權限）或重新啟動應用程式。

## 安裝Android Player {#installing-android-player}

若要實作適用於AEM畫面的Android Player，請安裝適用於AEM畫面的Android Player。

請造訪&#x200B;[**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/)頁面。

### 設定AEM Screens 6.5.5 Service Pack {#fp-environment-setup}的環境

>[!NOTE]
>如果您使用AEM Screens 6.5.5 Service Pack，則必須為Android Player設定環境。

在所有AEM作者和發佈例項上，將登入Token Cookie **的** SameSite屬性從&#x200B;**Lax**&#x200B;設為&#x200B;**None**，從&#x200B;**Adobe Experience Manager Web Console Configuration**&#x200B;設定。

請遵循下列步驟：

1. 使用&#x200B;**導覽至「Adobe Experience Manager Web Console設定」。**`http://localhost:4502/system/console/configMgr`

1. 搜尋&#x200B;*Adobe Granite Token驗證處理常式*。

1. 將login-token Cookies的&#x200B;**SameSite屬性從** Lax **設為** None **。**
   ![影像](/help/user-guide/assets/granite-updates.png)

1. 按一下&#x200B;**「儲存」**。


### 臨機方法{#ad-hoc-method}

臨機方法可讓您安裝最新的Android Player(*.exe*)。 請造訪&#x200B;[**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/)頁面。

下載應用程式後，請依照播放器上的步驟完成臨機安裝：

1. 長按左上角以開啟管理面板。
1. 從左側動作功能表導覽至&#x200B;**Configuration**，然後輸入您要連線至的AEM例項位置（位址），然後按一下「儲存&#x200B;**a3/>」。**

1. 從左側操作菜單導航到&#x200B;**設備****註冊**&#x200B;連結，以檢查設備註冊過程的狀態。

>[!NOTE]
>
>如果&#x200B;**State**&#x200B;是&#x200B;**REGISTERED**，您會注意到&#x200B;**Device id**&#x200B;欄位將會填入。
>
>如果&#x200B;**State**&#x200B;是&#x200B;**UNECROVERED**，則可使用&#x200B;**Token**&#x200B;註冊裝置。

## 實作Android Watchdog {#implementing-android-watchdog}

由於Android的架構，重新啟動裝置需要應用程式具備系統權限。 為此，您需要使用製造商的簽名密鑰來簽署應用程式，否則看門狗會重新啟動播放器應用程式，而不會重新啟動裝置。

### 使用製造商金鑰{#signage-of-android-apks-using-manufacturer-keys}的Android標誌

若要存取部分Android的特權API，例如&#x200B;*PowerManager*&#x200B;或&#x200B;*HDMIControlServices*，您必須使用製造商的金鑰簽署android apk。

>[!CAUTION]
>
>先決條件：
>
>您應先安裝Android SDK，然後再執行下列步驟。

請依照下列步驟，使用製造商的金鑰簽署Android應用程式：

1. 從Google Play或[AEM Screens Player下載](https://download.macromedia.com/screens/)頁面下載應用程式
1. 從製造商獲取平台密鑰，以獲取&#x200B;*pk8*&#x200B;和&#x200B;*pem*&#x200B;檔案

1. 使用尋找~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;，在android sdk中找到apksigner工具
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. 在Android sdk中尋找郵遞區號對齊工具的路徑
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaldified.apk
1. 使用adb安裝安裝至裝置，安裝&#x200B;***aemscreensalpid.apk***

## Android Watchdog實施{#android-watchdog-implementation}

跨Android監視程式服務是使用&#x200B;*AlarmManager*&#x200B;以cordova增效模組實作。

下圖顯示了監視程式服務的實現：

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Initialization**&#x200B;在初始化cordova增效模組時，會檢查權限，以查看我們是否擁有系統權限，進而查看重新啟動權限。 如果滿足這兩個條件，則會建立「待重新啟動的意圖」，否則會建立「待重新啟動的意圖」（基於其「啟動活動」）。

**2.保持活動計時器**&#x200B;使用保持活動計時器每15秒觸發一個事件。 在此情況下，您必須取消現有的待定意圖（以重新啟動或重新啟動應用程式），並在相同的60秒內註冊新的待定意圖（實際上是延遲重新啟動）。

>[!NOTE]
>
>在Android中，*AlarmManager*&#x200B;用於註冊&#x200B;*pendingIntents*，即使應用程式當機且其警報傳送與API 19(Kitkat)不精確，&lt;a0/>AlarmManager&lt;a1/>仍可執行。 在計時器的間隔和&#x200B;*AlarmManager的* *pendingIntent的*&#x200B;報警之間保持一定的間隔。

**3.應用程式當機**&#x200B;在當機時，向AlarmManager註冊的待重新引導方式不再重設，因此它會執行應用程式的重新引導或重新啟動（視cordova增效模組初始化時的可用權限而定）。

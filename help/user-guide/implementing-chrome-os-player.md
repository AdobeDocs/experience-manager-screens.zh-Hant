---
title: 實作Chrome OS Player
description: 瞭解如何使用Chrome Management Console實作Chrome OS Player。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 0%

---

# 實作Chrome OS Player {#implementing-chrome-os-player}

本節說明如何使用「Chrome管理主控台」實作Chrome OS Player。

## 使用Chrome管理主控台 {#using-chrome-management-console}

請依照下列步驟設定Chrome管理主控台：

1. 註冊Chrome管理主控台。 您必須取得Chrome管理主控台的授權。 如需詳細資訊，請連絡[Google支援](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995)以管理Chrome裝置設定。
1. 將您的Chrome作業系統裝置註冊至網域，並等待15分鐘讓裝置與Chrome管理控制檯同步。 若要進一步瞭解如何註冊Chrome裝置，請按一下[這裡](https://support.google.com/chrome/a/answer/1360534?hl=en)。
1. Chrome網站商店提供Chrome Player。

>[!NOTE]
>
>建議使用裝置管理解決方案(例如Chrome管理主控台)來部署及管理Chrome作業系統裝置。 雖然本檔案提供Chrome管理主控台的實作，但其他廠商也聲稱提供類似的功能。 請連絡裝置管理軟體的廠商。

## 命名Chrome作業系統播放器 {#name-chrome}

您可以指派好記的裝置名稱給您的Chrome Player，然後將指派的裝置名稱傳送給Adobe Experience Manager (AEM)。 此功能不僅可讓您為Chrome Player命名，也讓您輕鬆指派適當的內容。

>[!NOTE]
>您只能在註冊之前選擇播放器名稱。 播放器註冊後，播放器名稱就無法再變更。

請依照下列步驟，在Chrome Player中設定名稱：

1. 您可以選擇允許音訊/視訊整合經銷商或IT管理員設定資產ID和位置，作為企業註冊的一部分。

   ![影像](/help/user-guide/assets/chrome-device/chrome1.png)

1. 當您註冊裝置時，畫面會顯示選項。

   ![影像](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. 您可以將資產ID設為企業註冊的一部分並在Chrome Management Console中設定。

   ![影像](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Chrome播放器必須註冊企業註冊，且Chrome播放器必須透過Chrome Management Console部署，否則資產ID會傳回空白(例如Chrome作為擴充功能)。 裝置名稱僅在註冊時記錄。 Adobe Experience Manager (AEM)不會擷取未來的變更。

### 啟用資訊站模式 {#enabling-kiosk-mode}

請依照下列步驟啟用Kiosk模式：

1. 登入Chrome Developer Console。

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. 瀏覽至&#x200B;**裝置管理** > **Chrome管理** > **裝置設定**。
1. 向下捲動至&#x200B;**資訊站設定**&#x200B;並按一下&#x200B;**管理資訊站應用程式**。

   ![資訊站](assets/kiosk.png)

1. 按一下Chrome線上應用程式商店中的AEM Screens Player。

   >[!NOTE]
   >
   >最近發佈的應用程式可能需要約15分鐘才會出現在此清單中。

1. 從&#x200B;**自動啟動Kiosk應用程式**&#x200B;下拉式清單中按一下&#x200B;**AEM Screens Player**。

   視網路而定，變更可能需要幾分鐘才會生效。 建議重新開機。

#### 正在檢查遠端裝置狀態 {#checking-remote-device-status}

1. 登入Chrome Developer Console。
1. 瀏覽至&#x200B;**裝置管理** > **Chrome裝置**，然後按一下您要控制的裝置。
1. 按一下&#x200B;**系統活動和疑難排解**。
1. 檢查裝置的&#x200B;**重新開機裝置**&#x200B;和&#x200B;**熒幕擷取**&#x200B;內容。 您也可以檢查裝置狀態與健全狀態資訊。

>[!NOTE]
>
>這些設定可在裝置註冊後幾分鐘啟用。 每個選項都可隨時間啟用。

### 設定Chrome作業系統播放器的遠端設定 {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player是啟用Kiosk的應用程式，也可啟用Chrome作業系統播放器的遠端原則設定。

請依照下列步驟，設定播放器的各種選項：

1. 登入Chrome管理主控台。
1. 按一下&#x200B;**裝置管理** > **Chrome管理** > **應用程式管理**。 AEM Screens Player會顯示在清單中。
1. 按一下應用程式&#x200B;**AEM Screens Player**。
1. 按一下&#x200B;**資訊站設定**，然後按一下您的組織（*如果使用測試環境*）。
1. 按一下&#x200B;**上傳組態檔**&#x200B;並上傳組態原則（*JSon檔案*）。
1. 按一下「**儲存**」。重新啟動裝置，以便同步處理原則。

>[!NOTE]
>
>重新啟動裝置，以便同步原則變更。

#### 原則JSON檔案範例 {#example-policy-json-file}

```java
{
  "server": {
    "Value": "https://aemscreensdemo.adobeitc.com"
  },
  "resolution": {
    "Value": "auto"
  },
  "rebootSchedule": {
    "Value": "at 4:00am"
  },
  "enableAdminUI": {
    "Value": true
  },
  "enableOSD": {
    "Value": true
  },
  "enableActivityUI": {
    "Value": true
  }
}
```

### 原則屬性和用途 {#policy-attributes-and-purpose}

下表摘要列出這些原則及其功能。

| **原則名稱** | **用途** |
|---|---|
| 伺服器 | Adobe Experience Manager (AEM)伺服器的URL。 |
| 註冊金鑰 | 用於使用預先共用金鑰的大量裝置註冊。 |
| 解析度 | 裝置的解析度。 |
| rebootSchedule | 重新啟動播放器的排程。 |
| enableAdminUI | 啟用管理員UI來設定站台上的裝置。 在完全設定並投入生產後，設為false。 |
| enableOSD | 啟用頻道切換器UI，讓使用者在裝置上切換頻道。 在完全設定並投入生產後，請考慮將設為false 。 |
| enableactivityui | 啟用，以便顯示下載和同步等活動的進度。 啟用以進行疑難排解，並在完全設定後停用。 |
| cloudMode | 如果您希望Chrome Player連線至Screensas a Cloud Service，請設為true。 設為false可連線至AMS或內部部署AEM。 |
| cloudToken | 註冊Token以註冊Screensas a Cloud Service。 |

>[!NOTE]
>
>原則設定會嚴格執行，且播放器的管理員UI不會手動覆寫。 若要允許特定原則的手動播放器設定，請勿在&#x200B;***原則設定***&#x200B;中指定原則。 例如，如果您要允許手動設定重新開機排程，請勿在原則設定中指定索引鍵&#x200B;***rebootSchedule***。

### 使用Screens遠端控制 {#using-remote-control}

AEM Screens提供遠端控制功能。 若要深入瞭解此功能，請前往下列位置： [Screens遙控器](implementing-remote-control.md)

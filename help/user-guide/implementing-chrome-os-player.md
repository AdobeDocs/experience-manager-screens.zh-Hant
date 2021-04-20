---
title: 實作Chrome OS Player
seo-title: 實作Chrome OS Player
description: 請依照本頁瞭解使用Chrome管理控制台實作Chrome OS Player的相關資訊。
seo-description: 請依照本頁瞭解使用Chrome管理控制台實作Chrome OS Player的相關資訊。
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---


# 實作Chrome OS Player {#implementing-chrome-os-player}

本節說明如何使用Chrome Management Console實作Chrome OS Player。

## 使用Chrome Management Console {#using-chrome-management-console}

請依照下列步驟來設定chrome管理主控台：

1. 註冊Chrome Management Console。 您必須取得Chrome Management Console的授權。 如需詳細資訊，請連絡[Google支援](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995)以「管理Chrome裝置」設定。
1. 將您的Chrome OS裝置註冊至網域，等待15分鐘，讓裝置與Chrome管理主控台同步。 若要進一步瞭解註冊chrome裝置，請按一下[這裡](https://support.google.com/chrome/a/answer/1360534?hl=en)。
1. Chrome Player將可在Chrome Web商店取用。

>[!NOTE]
>
>建議使用裝置管理解決方案（例如Chrome Management Console）來部署及管理Chrome OS裝置。 不過，本檔案提供Chrome Management Console的實作，也有其他廠商聲稱提供類似的功能。 請聯絡您的裝置管理軟體廠商。

### 啟用Kiosk模式{#enabling-kiosk-mode}

請依照下列步驟啟用資訊站模式：

1. 登入Chrome Developer Console。

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. 瀏覽至&#x200B;**裝置管理** > **鉻管理** > **裝置設定**。
1. 向下滾動到&#x200B;**Kiosk Settings** ，然後按一下&#x200B;**Manage Kiosk Applications**。

   ![kisk](assets/kiosk.png)

1. 從Chrome Web Store選取「AEM Screens播放器」。

   >[!NOTE]
   >
   >最近發佈的應用程式可能需要大約15分鐘才會出現在此清單中。

1. 從&#x200B;**自動啟動資訊站應用程式**&#x200B;下拉式清單中選取&#x200B;**AEM Screens播放器**。

   視網路而定，變更可能需要幾分鐘的時間才能生效。 建議重新啟動。

#### 正在檢查遠程設備狀態{#checking-remote-device-status}

1. 登入Chrome Developer Console。
1. 瀏覽至「裝置管理&#x200B;**** > **Chrome Devices**」，並選取您要控制的裝置。
1. 按一下「**System Activity and troubleshooting**（系統活動和故障排除）」。
1. 檢查設備的&#x200B;**Reboot Device**&#x200B;和&#x200B;**Screen Capture**&#x200B;屬性。 您也可以檢查裝置狀態和健康資訊。

>[!NOTE]
>
>請注意，這些設定可能會在裝置註冊後數分鐘內啟用。 每個選項可能會隨著時間而啟用。

### 設定Chrome OS播放器的遠端設定{#configuring-remote-configuration-of-chrome-os-players}

AEM Screens播放器是啟用Kiosk的應用程式，也可啟用Chrome OS播放器的遠端政策設定。

請依照下列步驟來設定播放器的各種選項：

1. 登入Chrome Management Console。
1. 按一下「裝置管理&#x200B;**** > **Chrome Management** > **應用程式管理**」。 AEM Screens播放器會顯示在清單中。
1. 按一下應用程式&#x200B;**AEM Screens播放器**。
1. 按一下&#x200B;**Kiosk settings**&#x200B;並選擇您的組織（如果使用測試環境&#x200B;*）。*
1. 按一下&#x200B;**上傳設定檔案**&#x200B;並上傳設定原則（*Json檔案*）。
1. 按一下「**儲存**」。您必須重新啟動設備才能同步策略。

>[!NOTE]
>
>重新啟動設備以同步策略更改。

#### 範例原則JSON檔案{#example-policy-json-file}

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

### 策略屬性和用途{#policy-attributes-and-purpose}

下表總結了策略及其功能。

| **原則名稱** | **目的** |
|---|---|
| *伺服器* | Adobe Experience Manager伺服器的URL |
| *解析度* | Chrome OS裝置的解析度 |
| *rebootSchedule* | 重新啟動Chrome播放器的排程 |
| *enableAdminUI* | 為技術人員啟用管理員UI，以便現場配置設備。 在完全設定並投入生產時，設為false。 |
| *enableOSD* | 啟用頻道切換器UI，讓使用者在裝置上切換頻道。 在完全設定後，請考慮在生產中設定為false。 |
| *enableActivityUI* | 啟用以顯示活動的進度，例如下載和同步。 啟用疑難排解功能，並在完全設定後在生產中停用。 |

>[!NOTE]
>
>原則設定會嚴格強制執行，不會在播放器的管理UI中手動覆寫。 要允許對特定策略進行手動播放器配置，請不要在&#x200B;***策略配置中指定策略，例如，如果要允許對重新引導計畫進行手動配置，請不要在策略配置中指定鍵*** rebootSchedule ***。***

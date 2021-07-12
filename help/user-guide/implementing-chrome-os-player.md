---
title: 實作Chrome OS Player
seo-title: 實作Chrome OS Player
description: 請詳閱本頁，了解如何使用Chrome管理控制台實作Chrome OS Player。
seo-description: 請詳閱本頁，了解如何使用Chrome管理控制台實作Chrome OS Player。
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: 管理畫面
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---

# 實作Chrome OS Player  {#implementing-chrome-os-player}

本節說明如何使用Chrome管理主控台實作Chrome OS Player。

## 使用Chrome管理控制台 {#using-chrome-management-console}

請依照下列步驟來設定chrome管理主控台：

1. 註冊Chrome管理控制台。 您需要取得Chrome管理控制台的授權。 如需詳細資訊，請聯絡[Google支援](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995)以管理Chrome裝置設定。
1. 將Chrome OS裝置註冊至網域，等待15分鐘，讓裝置與Chrome管理主控台同步。 若要進一步了解註冊Chrome裝置，請按一下[這裡](https://support.google.com/chrome/a/answer/1360534?hl=en)。
1. Chrome Web商店將提供Chrome播放器。

>[!NOTE]
>
>若要部署及管理Chrome OS裝置，建議使用Chrome管理控制台之類的裝置管理解決方案。 雖然本檔案提供Chrome管理控制台的實作，但也有其他廠商聲稱可提供類似的功能。 請聯繫設備管理軟體的供應商。

## 命名Chrome OS播放器 {#name-chrome}

您可以指派好記的裝置名稱給Chrome播放器，借此將指派的裝置名稱傳送至Adobe Experience Manager(AEM)。 此功能不僅可讓您為Chrome播放器命名，也可讓您輕鬆指派適當的內容。

請依照下列步驟，在Chrome播放器中設定名稱：

1. 您可以選擇允許AV整合商或IT管理員在企業註冊過程中設定資產ID和位置。

   ![影像](/help/user-guide/assets/chrome-device/chrome1.png)

1. 當您可以註冊設備時，將顯示選項。

   ![影像](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. 您可以在企業註冊以及Chrome管理控制台中設定資產ID。

   ![影像](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Chrome播放器必須登入企業註冊，且Chrome播放器必須透過Chrome管理控制台部署，否則資產ID將傳回空白（例如，以Chrome為擴充功能）。 設備名稱僅在註冊時記錄。 Adobe Experience Manager(AEM)將不會擷取未來的變更。

### 啟用Kiosk模式 {#enabling-kiosk-mode}

請依照下列步驟啟用Kiosk模式：

1. 登入Chrome開發人員控制台。

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. 瀏覽至&#x200B;**裝置管理** > **Chrome管理** > **裝置設定**。
1. 向下捲動至&#x200B;**Kiosk Settings** ，然後按一下&#x200B;**Manage Kiosk Applications**。

   ![資訊站](assets/kiosk.png)

1. 從Chrome線上應用程式商店中選取AEM Screens播放器。

   >[!NOTE]
   >
   >最近發佈的應用程式可能需要15分鐘才會出現在此清單中。

1. 從&#x200B;**自動啟動Kiosk應用程式**&#x200B;下拉式清單中選取&#x200B;**AEM Screens播放器**。

   視網路而定，變更可能需要幾分鐘才會生效。 建議重新啟動。

#### 檢查遠程設備狀態 {#checking-remote-device-status}

1. 登入Chrome開發人員控制台。
1. 瀏覽至&#x200B;**裝置管理** > **Chrome裝置**，並選取您要控制的裝置。
1. 按一下「**系統活動和疑難解答**」。
1. 檢查設備的&#x200B;**重新啟動設備**&#x200B;和&#x200B;**螢幕捕獲**&#x200B;屬性。 您也可以檢查裝置狀態和健康資訊。

>[!NOTE]
>
>請注意，這些設定可能會在裝置註冊後幾分鐘內啟用。 隨著時間推移，每個選項都可能啟用。

### 設定Chrome OS播放器的遠端設定 {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player是啟用Kiosk的應用程式，也可為Chrome OS播放器啟用遠端原則設定。

請依照下列步驟設定播放器的各種選項：

1. 登入Chrome管理控制台。
1. 按一下「**裝置管理** > **Chrome管理** > **應用程式管理**」。 AEM Screens播放器會顯示在清單中。
1. 按一下應用程式&#x200B;**AEM Screens Player**。
1. 按一下&#x200B;**Kiosk設定**&#x200B;並選取您的組織（若使用測試環境&#x200B;*）。*
1. 按一下&#x200B;**上傳配置檔案**&#x200B;並上傳配置策略（*Json檔案*）。
1. 按一下「**儲存**」。必須重新啟動設備才能同步策略。

>[!NOTE]
>
>重新啟動設備以同步策略更改。

#### 策略JSON檔案示例 {#example-policy-json-file}

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

### 策略屬性和用途 {#policy-attributes-and-purpose}

下表概括了策略及其功能。

| **策略名稱** | **用途** |
|---|---|
| *伺服器* | Adobe Experience Manager伺服器的URL |
| *解析度* | Chrome OS裝置的解析度 |
| *rebootSchedule* | 重新啟動Chrome播放器的排程 |
| *enableAdminUI* | 啟用管理員UI，讓技術人員在現場配置設備。 在完全設定後並在生產環境中設為false。 |
| *enableOSD* | 啟用通道切換器UI，讓使用者在裝置上切換通道。 在完全設定並在生產環境中設定為false時，請考慮將其設為false。 |
| *enableActivityUI* | 啟用以顯示活動的進度，例如下載和同步。 完全設定後在生產環境中啟用疑難排解功能並加以停用。 |

>[!NOTE]
>
>原則設定會強制執行，且不會在播放器的管理員UI中手動覆寫。 要允許為特定策略進行手動播放器配置，請勿在&#x200B;***策略配置中指定策略，例如，如果要允許重新啟動計畫進行手動配置，請勿在策略配置中指定鍵*** rebootSchedule ***。***

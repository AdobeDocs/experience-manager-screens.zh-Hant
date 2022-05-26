---
title: 實現Chrome OS Player
seo-title: Implementing Chrome OS Player
description: 按照本頁瞭解如何使用Chrome管理控制台實現Chrome OS Player。
seo-description: Follow  this page to learn about the implementation of the Chrome OS Player using the Chrome Management Console.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: 8d4a7b2bc436d822c673a00437ee895c8ef5cb6f
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 0%

---

# 實現Chrome OS Player  {#implementing-chrome-os-player}

本節介紹如何使用Chrome管理控制台實現Chrome OS Player。

## 使用Chrome管理控制台 {#using-chrome-management-console}

按照以下步驟設定chrome管理控制台：

1. 註冊Chrome管理控制台。 您需要獲得Chrome管理控制台的許可證。 聯繫人 [Google支援](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995) 以管理Chrome設備設定以獲取詳細資訊。
1. 將Chrome OS設備註冊到域，等待15分鐘，以便設備與Chrome管理控制台同步。 要瞭解有關註冊chrome設備的詳細資訊，請按一下 [這裡](https://support.google.com/chrome/a/answer/1360534?hl=en)。
1. Chrome Player將在Chrome Web商店中提供。

>[!NOTE]
>
>建議為部署和管理Chrome OS設備提供設備管理解決方案，如Chrome管理控制台。 儘管本文檔為Chrome管理控制台提供了實施，但也有其他供應商聲稱提供了類似的功能。 請與設備管理軟體的供應商聯繫。

## 命名Chrome OS播放器 {#name-chrome}

您可以為Chrome播放器指定用戶友好的設備名稱，從而將指定的設備名稱發送給Adobe Experience Manager(AEM)。 此功能不僅允許您命名Chrome播放器，還允許您輕鬆分配適當的內容。

>[!NOTE]
>您只能在註冊前選擇播放器名稱。 註冊玩家後，玩家名稱將不能再更改。

按照以下步驟在Chrome播放器中配置名稱：

1. 您可以根據需要允許AV整合商或IT管理員將資產ID和位置設定為企業註冊的一部分。

   ![影像](/help/user-guide/assets/chrome-device/chrome1.png)

1. 當您註冊設備時，系統會向您提供選項。

   ![影像](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. 您可以將資產ID設定為企業註冊的一部分，也可以在Chrome管理控制台中進行設定。

   ![影像](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >必須在企業註冊中註冊Chrome播放器，並且必須通過Chrome管理控制台部署Chrome播放器，否則資產ID將返回空白（例如，chrome作為擴展）。 設備名稱僅在註冊時記錄。 Adobe Experience Manager()不會接受未來的變AEM化。

### 啟用Kiosk模式 {#enabling-kiosk-mode}

按照以下步驟啟用Kiosk模式：

1. 登錄到Chrome Developer Console。

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. 瀏覽到 **設備管理** > **Chrome管理** > **設備設定**。
1. 向下滾動到 **Kiosk設定** 按一下 **管理Kiosk應用程式**。

   ![亭](assets/kiosk.png)

1. 從Chrome Web Store中選擇AEM Screens播放器。

   >[!NOTE]
   >
   >最近發佈的應用可能需要大約15分鐘才能顯示在此清單中。

1. 選擇 **AEM Screens選手** 從 **自動啟動資訊亭應用** 下拉清單。

   根據網路的不同，更改可能需要幾分鐘才能生效。 建議重新啟動。

#### 檢查遠程設備狀態 {#checking-remote-device-status}

1. 登錄到Chrome Developer Console。
1. 瀏覽到 **設備管理** > **Chrome設備** 並選擇要控制的設備。
1. 按一下 **系統活動和故障排除**。
1. 檢查 **重新啟動設備** 和 **螢幕捕獲** 設備的屬性。 您還可以檢查設備狀態和運行狀況資訊。

>[!NOTE]
>
>請注意，這些設定可能在設備註冊後幾分鐘內啟用。 每個選項可能會隨著時間而啟用。

### 配置Chrome OS播放器的遠程配置 {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens播放器是啟用Kiosk的應用程式，它還為Chrome OS播放器啟用遠程策略配置。

按照以下步驟配置播放器的各種選項：

1. 登錄到Chrome管理控制台。
1. 按一下 **設備管理** > **Chrome管理** > **應用程式管理**。 清單中顯示AEM Screens播放器。
1. 按一下應用程式 **AEM Screens選手**。
1. 按一下 **Kiosk設定** 選擇您的組織(*如果使用test環境*)。
1. 按一下 **上載配置檔案** 並上載配置策略(*Json檔案*)。
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

下表概述了策略及其功能。

| **策略名稱** | **目的** |
|---|---|
| *伺服器* | 指向Adobe Experience Manager伺服器的URL |
| *解析度* | Chrome OS設備的解析度 |
| *重新引導計畫* | 重新啟動Chrome播放器的計畫 |
| *enableAdminUI* | 為技術人員啟用管理用戶介面以在現場配置設備。 在完全配置並在生產中將其設定為false。 |
| *啟用OSD* | 啟用通道切換器UI，以便用戶在設備上切換通道。 在完全配置並投入生產後，請考慮將其設定為false。 |
| *enableActivityUI* | 啟用以顯示下載和同步等活動的進度。 在完全配置並投入生產後啟用故障排除和禁用。 |

>[!NOTE]
>
>策略配置將得到嚴格強制執行，不會在播放器的管理員UI上手動覆蓋。 要允許為特定策略手動配置播放器，請不要在 ***策略配置，*** 例如，如果要允許手動配置重新啟動計畫，請不要指定鍵 ***重新引導計畫*** 的子菜單。

### 使用螢幕遙控器 {#using-remote-control}

AEM Screens提供遠程控制功能。 在此處瞭解有關此功能的詳細資訊： [螢幕遙控](implementing-remote-control.md)

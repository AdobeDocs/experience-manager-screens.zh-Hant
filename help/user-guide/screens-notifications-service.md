---
title: AEM Screens Notifications Service
seo-title: AEM Screens Notifications Service
description: 請依照本頁進一步瞭解如何監控裝置活動。
seo-description: 請依照本頁進一步瞭解如何監控裝置活動。
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# AEM Screens Notifications Service{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens Notifications Service***，說明您可在其中監視裝置活動的功能。

本節涵蓋下列主題：

* **綜覽**
* **設定電子郵件設定**
* **電子郵件通知**
* **範例使用案例**

>[!CAUTION]
>
>只有在您已安裝AEM 6.3.2 Feature Pack 3或AEM 6.4.1 Screens Feature Pack 1時，才能使用此AEM Screens功能。
>
>若要存取此功能套件，您必須聯絡Adobe支援並要求存取權。 一旦您擁有權限，就可從「套件共用」下載。

## 概覽 {#overview}

***AEM Screens Notifications Service***，可讓管理員在AEM Screens播放器在可設定的時段內未ping通時收到電子郵件。

此服務可在OSGi web控制台中配置。

## 設定電子郵件設定 {#configuring-email-settings}

請依照下列步驟來設定電子郵件通知設定：

1. 開啟 **Adobe Experience Manager Web Console設定**。
1. 開啟 **畫面裝置電子郵件監控服務**。

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. 定義下列欄位以設定電子郵件的設定：

   **裝置路徑** ：輸入您要監視之畫面專案的路徑。 路徑通常是 `/home/users/screens/<Name of your project>`。

   例如，如果您的專案是 **We.Retail**，您會以 ***/home/users/screens/we-retail的形式使用專案路徑***。

   >[!NOTE]
   >
   >指定裝置使用者所在的專案路徑。

   **排程頻率** ：指定此螢幕應傳送電子郵件的時間（例如，5:00 pm或17:00）或頻率（例如，1）。

   **Ping超時** ：這指定設備在其後應被視為不可訪問的間隔（分鐘）。

   **SMTP伺服器** ：指定用於發送電子郵件的SMTP伺服器。

   **SMTP埠** ：輸入SMTP埠。

   **使用TLS** 傳輸層安全性(TLS)可以使用與SMTP伺服器的安全通信。

   建議使用TLS來確保與公司郵件伺服器的安全連接。 請洽詢您的郵件管理員，以取得適當的值。

   **username** 指定傳送電子郵件的使用者名稱。

   **密碼** ：指定傳送電子郵件的密碼。

   **收件者** ：指定收件者的電子郵件地址。

   >[!NOTE]
   >
   >您只能輸入一個電子郵件地址。 若要傳送大量電子郵件，請與相關使用者建立群組或散發清單。

1. 按一 **下「儲存** 」，以透過電子郵件為您的AEM Screens裝置設定螢幕活動。

## Email Notification {#email-notification}

一旦您設定了電子郵件通知的設定，您就會收到一封電子郵件通知，其中包含實際裝置的連結，該連結會報告為閒置。

存取該連結會直接導覽至裝置控制面板。

只有在至少有一個裝置未因指定的ping逾時而ping通，且仍未在產生電子郵件時ping通時，才會傳送電子郵件。

### 範例使用案例 {#example-use-cases}

以下範例說明從「畫面裝置電子郵件監視服務」設定屬性時需參考的少數案例。

**方案1**:

如果您將排程頻率設定為1:00 am，而ping逾時設定為60，則如果您的螢幕裝置在12:00 pm至1:00 pm之間未ping通訊，您會收到電子郵件通知，確認裝置未活動。

**方案2**:

如果您將排程頻率設為1，而ping逾時設為60，則如果您的「螢幕」裝置在一天中的任何特定時間未ping一次，您會收到確認裝置閒置的電子郵件通知。

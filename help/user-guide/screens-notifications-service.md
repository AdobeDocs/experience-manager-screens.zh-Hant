---
title: AEM Screens通知服務
seo-title: AEM Screens通知服務
description: 請依照本頁面，深入了解如何監控裝置活動。
seo-description: 請依照本頁面，深入了解如何監控裝置活動。
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
feature: 製作畫面
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# AEM Screens通知服務{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens通知服務***，說明您可監控裝置活動的功能。

本節涵蓋下列主題：

* **概覽**
* **配置電子郵件設定**
* **電子郵件通知**
* **範例使用案例**

>[!CAUTION]
>
>只有在您已安裝AEM 6.3.2 Feature Pack 3或AEM 6.4.1 Screens Feature Pack 1時，才能使用此AEM Screens功能。
>
>若要存取此Feature Pack，您必須聯絡Adobe支援並要求存取權。 擁有權限後，您就可以從「封裝共用」下載。

## 概覽 {#overview}

***AEM Screens通知服務***，可讓管理員在AEM screens播放器的可設定時段內未ping通時，收到電子郵件。

可在OSGi Web控制台中配置此服務。

## 配置電子郵件設定 {#configuring-email-settings}

請依照下列步驟來設定電子郵件通知設定：

1. 開啟&#x200B;**Adobe Experience Manager Web控制台配置**。
1. 開啟&#x200B;**螢幕設備電子郵件監視服務**。

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. 定義下列欄位以配置電子郵件的設定：

   **設** 備路徑輸入要監視的螢幕項目的路徑。路徑通常為`/home/users/screens/<Name of your project>`。

   例如，如果您的專案為&#x200B;**We.Retail**，您將使用專案路徑作為&#x200B;***/home/users/screens/we-retail***。

   >[!NOTE]
   >
   >指定裝置使用者所在的專案路徑。

   **排** 程頻率指定此監視器應傳送電子郵件的時間（例如下午5:00或17:00）或頻率（例如1），以小時為單位。

   **Ping超** 時這指定了以分鐘為單位的時間間隔，在此時間間隔之後，設備應被視為不可訪問。

   **SMTP伺** 服器指定用於發送電子郵件的SMTP伺服器。

   **SMTP** 埠輸入SMTP埠。

   **使** 用TLSTransport Layer Security(TLS)可以使用與SMTP伺服器的安全通信。

   建議使用TLS來安全連線至公司郵件伺服器。 請洽詢您的郵件管理員以取得適當的值。

   **** username指定傳送電子郵件的使用者名稱。

   **** password指定傳送電子郵件的密碼。

   **** 收件者指定收件者的電子郵件地址。

   >[!NOTE]
   >
   >您只能輸入一個電子郵件地址。 若要傳送大量電子郵件，請與相關使用者建立群組或通訊組清單。

1. 按一下&#x200B;**儲存**，透過電子郵件為您的AEM Screens裝置設定監視器活動。

## 電子郵件通知 {#email-notification}

設定電子郵件通知的設定後，您會收到電子郵件通知，其中包含實際裝置（據報未活動）的連結。

存取該連結會直接導覽至裝置控制面板。

只有在至少有一個設備未因指定的Ping超時而Ping，並且在生成電子郵件時仍未Ping時，才會發送電子郵件。

### 範例使用案例 {#example-use-cases}

以下範例將說明幾個可參考的案例，以從Screens裝置電子郵件監控服務設定屬性。

**案例1**:

如果您將排程頻率設為上午1:00，而Ping逾時設為60，則如果您的Screens裝置在中午12:00至下午1:00之間沒有Ping，您會收到確認裝置閒置的電子郵件通知。

**案例2**:

如果您將排程頻率設為1，將Ping逾時設為60，則如果您的Screens裝置在一天中的任何特定時間沒有Ping一次，您會收到確認裝置閒置的電子郵件通知。

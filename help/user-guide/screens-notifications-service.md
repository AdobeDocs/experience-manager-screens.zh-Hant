---
title: AEM Screens通知服務
seo-title: AEM Screens Notifications Service
description: 按照本頁瞭解有關如何監視設備活動的詳細資訊。
seo-description: Follow this page to learn more about how you can monitor device activity.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# AEM Screens通知服務{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens通知服務***，介紹可監視設備活動的功能。

本節介紹以下主題：

* **概觀**
* **配置電子郵件設定**
* **電子郵件通知**
* **示例用例**

>[!CAUTION]
>
>只有安裝了功能包3或螢幕功能包1AEM，才可以使用此AEM Screens功AEM能。
>
>要訪問此功能包，必須聯繫Adobe支援並請求訪問。 擁有權限後，您可以從包共用下載它。

## 概觀 {#overview}

***AEM Screens通知服務***，允許管理員在螢幕播放AEM器在可配置的時間段內未ping通時接收電子郵件。

可以在OSGi Web控制台中配置此服務。

## 配置電子郵件設定 {#configuring-email-settings}

按照以下步驟配置電子郵件通知設定：

1. 開啟 **Adobe Experience ManagerWeb控制台配置**。
1. 開啟 **螢幕設備電子郵件監視服務**。

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. 定義以下欄位以配置電子郵件的設定：

   **設備路徑** 輸入要監視的螢幕項目的路徑。 路徑通常 `/home/users/screens/<Name of your project>`。

   例如，如果項目 **We.Retail**，將項目路徑用作 ***/home/users/screens/weretail***。

   >[!NOTE]
   >
   >指定設備用戶所在的項目路徑。

   **計畫頻率** 指定此監視器發送電子郵件的時間（例如，下午5:00或17:00）或頻率（以小時為單位）（例如，1）。

   **Ping超時** 這指定了設備在其後被視為不可訪問的間隔（以分鐘為單位）。

   **SMTP伺服器** 指定用於發送電子郵件的SMTP伺服器。

   **SMTP埠** 輸入SMTP埠。

   **使用TLS** 傳輸層安全性(TLS)使您能夠使用與SMTP伺服器的安全通信。

   建議使用TLS來安全連接到公司郵件伺服器。 請與郵件管理員聯繫以瞭解相應的值。

   **用戶名** 指定發送電子郵件的用戶名。

   **密碼** 指定發送電子郵件的密碼。

   **收件人** 指定收件人的電子郵件地址。

   >[!NOTE]
   >
   >您只能輸入一個電子郵件地址。 要發送批量電子郵件，請與相關用戶建立組或通訊組清單。

1. 按一下 **保存** 通過電子郵件為您的AEM Screens設備配置監視器活動。

## 電子郵件通知 {#email-notification}

設定電子郵件通知的配置後，您將收到一封電子郵件通知，該通知將包含到實際設備的連結，該設備被報告為不活動。

訪問該連結將直接導航到設備儀表板。

僅當至少有一個設備在給定的ping超時未ping通並且在生成電子郵件時仍未ping通時，才會發送電子郵件。

### 示例使用案例 {#example-use-cases}

以下示例介紹了幾個可供參考的方案，以從螢幕設備電子郵件監視服務配置屬性。

**方案1**:

如果將計畫頻率設定為上午1:00,ping超時設定為60，則如果螢幕設備在下午12:00至下午1:00之間未ping通，您將收到電子郵件通知，確認設備不活動。

**方案2**:

如果將計畫頻率設定為1，將ping超時設定為60，則如果螢幕設備在一天中任何特定時間沒有ping一次，您將收到確認設備不活動的電子郵件通知。

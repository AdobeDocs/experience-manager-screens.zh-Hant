---
title: AEM Screens通知服務
description: 深入瞭解如何監視AEM Screens的裝置活動。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# AEM Screens通知服務{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens通知服務***&#x200B;說明監視裝置活動。

本節涵蓋下列主題：

* **概觀**
* **正在設定電子郵件設定**
* **電子郵件通知**
* **範例使用案例**

<!-- OBSOLETE NOTE>
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3.2 Feature Pack 3 or AEM 6.4.1 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. After you have permissions you can download it from Package Share. -->

## 概觀 {#overview}

***AEM Screens Notifications Service***&#x200B;可讓AEM Screens Player在可以設定的時間內未執行Ping命令，管理員即可收到電子郵件。

此服務可在OSGi Web主控台中設定。

## 正在設定電子郵件設定 {#configuring-email-settings}

請依照下列步驟設定電子郵件通知設定：

1. 開啟&#x200B;**Adobe Experience Manager Web主控台組態**。
1. 開啟&#x200B;**Screens裝置電子郵件監視服務**。

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. 定義下列欄位，以便您設定電子郵件的設定：

   **裝置路徑** — 輸入要監視的Screens專案路徑。 路徑通常是`/home/users/screens/<Name of your project>`。

   例如，如果您的專案是&#x200B;**`We.Retail`**，請將專案路徑用為&#x200B;***/home/users/screens/we-retail***。

   >[!NOTE]
   >
   >指定裝置使用者所在的專案路徑。

   **排程頻率** — 指定時間（例如，下午5:00或17:00）或此監視器應傳送電子郵件的頻率（例如，1）。

   **Ping逾時** — 此欄位會指定間隔（分鐘），在此間隔後裝置應視為無法連線。

   **SMTP伺服器** — 指定用於傳送電子郵件的SMTP伺服器。

   **SMTP連線埠** — 輸入SMTP連線埠。

   **使用TLS** — 傳輸層安全性(TLS)可讓您使用與SMTP伺服器的安全通訊。

   Adobe建議您使用TLS以安全地連線至公司郵件伺服器。 請洽詢您的郵件管理員以取得適當的值。

   **使用者名稱** — 指定用於傳送電子郵件的使用者名稱。

   **密碼** — 指定傳送電子郵件的密碼。

   **收件者** — 指定收件者的電子郵件地址。

   >[!NOTE]
   >
   >您只能輸入一個電子郵件地址。 若要傳送大量電子郵件，請使用相關使用者建立群組或通訊群組清單。

1. 按一下&#x200B;**儲存**，透過電子郵件為您的AEM Screens裝置設定監視器活動。

## 電子郵件通知 {#email-notification}

設定電子郵件通知的設定後，您會收到電子郵件通知，其中包含實際裝置的連結，該實際裝置已回報為閒置。

存取該連結會直接將您導覽至裝置控制面板。

只有符合以下條件時才傳送電子郵件：

* 至少有一個裝置在指定的ping逾時期間未執行ping動作，而且
* 在產生電子郵件時仍未發出Ping。

### 範例使用案例 {#example-use-cases}

以下範例說明一些案例，以供從Screens裝置電子郵件監視服務設定屬性時參考。

**案例1**

您設定排程頻率為凌晨1:00，Ping逾時為60。 接著，如果您的AEM Screens裝置在下午12:00到1:00之間未執行Ping命令，您會收到電子郵件通知，確認裝置未使用中。

**案例2**

您已將排程頻率設為1，並將Ping逾時設為60。 然後，如果您的AEM Screens裝置未在一天中的任意特定時間立即ping通，您會收到電子郵件通知，確認裝置處於非使用狀態。

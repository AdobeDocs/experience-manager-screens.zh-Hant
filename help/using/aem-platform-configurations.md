---
title: AEM 平台組態
seo-title: AEM 平台組態
description: 此頁面說明AEM平台設定
seo-description: 此頁面說明AEM平台設定
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 19%

---

# AEM 平台組態  {#platform-configurations}

>[!NOTE]
>
>此活動的一般利益相關者是AEM實施者。

請依照下列章節來設定AEM平台設定，以開始使用AEM畫面。

## 伺服器配置 {#server-configurations}

要設定伺服器配置，請參閱服 [務器配置](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration)。

## 作者——發佈 {#author-publish}

若要設定作者發佈，請參閱「在AEM畫 [面中設定作者和發佈」](https://helpx.adobe.com/tw/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>如果只有一個作者和一個發佈，則您只需要遵循在[「在 AEM Screens 中設定作者和發佈」](https://helpx.adobe.com/tw/experience-manager/6-5/screens/using/author-and-publish.html)頁面中&#x200B;**「在作者上設定複製代理」**&#x200B;下方的步驟。

## Dispatcher Configurations {#dispatcher-configurations}

Dispatcher 是 Adobe Experience manager 的快取和/或負載平衡工具。使用 AEM 的 Dispatcher 也有助於保護您的 AEM 伺服器不受攻擊。因此，您可以搭配使用 Dispatcher 與企業級 Web 伺服器，以提高 AEM 例項的安全性。

請參閱「 **[Dispatcher Configurations for AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** 」（針對AEM Screens專案重點說明設定dispatcher的准則）。

## 安裝FFMpeg和視訊轉譯 {#installing-ffmpeg}

依照適當作業系統（通常為RHEL）的步驟安裝FFMpeg:

1. 如果透過啟用EPEL和RPMFusion進行安裝，您可以安裝所有串流轉碼器，以擴大對FFmpeg轉換的支援
1. 如果AAC轉碼器標示為實驗性，則ffmpeg轉換將失敗。 若要避免在視訊描述檔中新增-strict -2（在AEM 6.3中為/etc/dam/video，並在AEM 6.4中移至/libs/settings/dam/video）
   >[!NOTE]
   >
   > 請注意，-strict -2必須是參數清單中的最後一個參數。 此外，在AEM 6.4中，您需要將 */libs/settings/dam/video下的節點複製至* /conf/global/settings/dam/video *，如「* Video Renditions」中所述 [](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html)。
1. 確認正在進行視訊轉換，以及正在建立轉譯。

## 密碼限制 {#password-restrictions}

AEM的密碼原則必須在AMS例項上停用。 This can ofterly configured in the web console using *com.adobe.cq.screens.device.impl.DeviceService* Refer to **Password Restrictions** section[in Configuring Author and Publish in AEM Screens](https://helpx.adobe.com/tw/experience-manager/6-5/screens/using/author-and-publish.html)

## 設定環境 {#setting-up-environments}

為您的Adobe Experience Manager(AEM)版本安裝並執行下列最新版本套件：

* AEM Service Pack
* 螢幕功能套件
* AEM Cumulative Fix Pack

除了上述外，請識別所需的任何開發套件（例如WCM Corecomponents）或協力廠商工具套件（例如SAP Hybris）。
在您的本機開發環境中安裝相同的軟體套件。 指示客戶在其所有QA、Stage和Production伺服器上都採用相同的設定。 不相符的伺服器組態會在部署和測試時造成問題。

>[!NOTE]
>
>若要安裝最新的AEM畫面功能套件，請參閱版 [本說明](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js)。

## 設定ACL {#setting-up-acls}

設定ACL將說明如何分離項目，以便讓每個個人或團隊處理自己的項目。

Refer  to [Setting up ACLs](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) for more details.

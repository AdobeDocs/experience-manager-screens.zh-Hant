---
title: AEM 平台組態
seo-title: AEM Platform Configurations
description: 本頁介紹平AEM台配置
seo-description: The page describes AEM Platform Configurations
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 21%

---

# AEM 平台組態  {#platform-configurations}

>[!NOTE]
>
>此活動的典型利益相關方是AEM實施者。

按照以下各節設定AEM平台配置以開始使用AEM Screens。

## 伺服器配置 {#server-configurations}

要設定伺服器配置，請參閱 [伺服器配置](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration)。

## 作者 — 發佈 {#author-publish}

要設定作者發佈，請參閱 [在AEM Screens配置作者和發佈](https://helpx.adobe.com/tw/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>如果只有一個作者和一個發佈，則您只需要遵循在[「在 AEM Screens 中設定作者和發佈」](https://helpx.adobe.com/tw/experience-manager/6-5/screens/using/author-and-publish.html)頁面中&#x200B;**「在作者上設定複製代理」**&#x200B;下方的步驟。

## Dispatcher 設定 {#dispatcher-configurations}

Dispatcher 是 Adobe Experience manager 的快取和/或負載平衡工具。使用 AEM 的 Dispatcher 也有助於保護您的 AEM 伺服器不受攻擊。因此，您可以搭配使用 Dispatcher 與企業級 Web 伺服器，以提高 AEM 例項的安全性。

請參閱 **[用於AEM Screens的調度程式配置](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** 它突出了為AEM Screens項目配置調度程式的指南。

## 安裝FFMpeg和視頻格式副本 {#installing-ffmpeg}

按照相應作業系統（通常為RHEL）的步驟安裝FFMpeg:

1. 如果通過啟用EPEL和RPMFsion進行安裝，則可以安裝所有gstreamer編解碼器以擴大對FFmpeg轉換的支援
1. 如果AAC編解碼器被標籤為實驗性，則ffmpeg轉換將失敗。 為避免將 — strict -2添加到視頻配置檔案(AEM6.3中的/etc/dam/video，並在6.4中移到/libs/settings/dam/videoAEM)
   >[!NOTE]
   >
   > 請注意，-strict -2必須是參數清單中的最後一個參數。 此外，AEM在6.4中，您需要複製 */libs/settings/dam/video* 至 */conf/global/settings/dam/video* 如所述 [視頻格式副本](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html)。
1. 驗證是否正在進行視頻轉換並且正在建立格式副本。

## 密碼限制 {#password-restrictions}

需要在AEMAMS實例上禁用的密碼策略。 可以使用螢幕設備服務在Web控制台中交替配置 *com.adobe.cq.screens.device.impl.DeviceService*
請參閱 **密碼限制** 部分[在AEM Screens配置作者和發佈](https://helpx.adobe.com/tw/experience-manager/6-5/screens/using/author-and-publish.html)

## 設定環境 {#setting-up-environments}

為您的Adobe Experience Manager版本安裝並運行以下軟體包的最新版本(AEM):

* AEM Service Pack
* 螢幕功能包
* AEM 累積修正套件

除了上述內容外，還要確定所需的任何開發包（例如，WCM核心元件）或第三方工具包（例如，SAP Hybris）。
在本地開發環境中安裝相同的軟體包。 指示您的客戶機在其所有QA、Stage和Production伺服器上採用相同的配置。 不匹配的伺服器配置在部署和測試時會出現問題。

>[!NOTE]
>
>要安裝最新的AEM Screens功能包，請參閱 [發行說明](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js)。

## 設定ACL {#setting-up-acls}

設定ACL可說明如何分離項目，以便每個個人或團隊處理其自己的項目。

請參閱 [設定ACL](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) 的子菜單。

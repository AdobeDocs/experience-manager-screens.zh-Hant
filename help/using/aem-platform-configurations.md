---
title: AEM 平台組態
seo-title: AEM 平台組態
description: 本頁說明AEM平台組態
seo-description: 本頁說明AEM平台組態
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 21%

---

# AEM 平台組態  {#platform-configurations}

>[!NOTE]
>
>此活動的一般利害關係人為AEM實作者。

請依照下節所述來設定AEM平台設定，以開始使用AEM Screens。

## 伺服器配置{#server-configurations}

要設定伺服器配置，請參閱[伺服器配置](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration)。

## 作者發佈{#author-publish}

若要設定作者發佈，請參閱[在AEM Screens中設定作者和發佈](https://helpx.adobe.com/tw/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>如果只有一個作者和一個發佈，則您只需要遵循在[「在 AEM Screens 中設定作者和發佈」](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)頁面中&#x200B;**「在作者上設定複製代理」**&#x200B;下方的步驟。

## Dispatcher設定{#dispatcher-configurations}

Dispatcher 是 Adobe Experience manager 的快取和/或負載平衡工具。使用 AEM 的 Dispatcher 也有助於保護您的 AEM 伺服器不受攻擊。因此，您可以搭配使用 Dispatcher 與企業級 Web 伺服器，以提高 AEM 例項的安全性。

請參閱&#x200B;**[AEM Screens的Dispatcher設定](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** ，其中反白標示為AEM Screens專案設定Dispatcher的准則。

## 安裝FFMpeg和視頻格式副本{#installing-ffmpeg}

按照相應OS（通常是RHEL）的步驟安裝FFMpeg :

1. 如果通過啟用EPEL和RPMFusion進行安裝，則可以安裝所有gstreamer編解碼器，以擴大對FFmpeg轉換的支援
1. 如果AAC轉碼器標示為實驗性，則ffmpeg轉換會失敗。 為了避免此情況，請在視訊設定檔中新增 — strict -2(AEM 6.3中為/etc/dam/video，並在AEM 6.4中移至/libs/settings/dam/video)
   >[!NOTE]
   >
   > 請注意，-strict -2必須是參數清單中的最後一個參數。 此外，在AEM 6.4中，您需要將&#x200B;*/libs/settings/dam/video*&#x200B;下的節點複製到&#x200B;*/conf/global/settings/dam/video*，如[Video Renditions](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html)中所述。
1. 確認正在進行視訊轉換，且正在建立轉譯。

## 密碼限制{#password-restrictions}

AEM的密碼原則必須在AMS例項上停用。 您可以使用Screens裝置服務&#x200B;*com.adobe.cq.screens.device.impl.DeviceService*，在Web主控台中交替設定此設定
請參閱[在AEM Screens中設定作者和發佈](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)中的&#x200B;**密碼限制**&#x200B;區段

## 設定環境{#setting-up-environments}

針對您的Adobe Experience Manager(AEM)版本，安裝並執行下列最新版套件：

* AEM Service Pack
* Screens Feature Pack
* AEM Cumulative Fix Pack

除了上述項目外，請識別任何開發套件（例如WCM Core）
元件)或第三方工具包（例如SAP Hybris）。
在您的本機開發環境上安裝相同的軟體套件。 指示您的用戶端在其所有QA、預備和生產伺服器上採用相同的設定。 不匹配的伺服器配置在部署和測試時會造成問題。

>[!NOTE]
>
>若要安裝最新的AEM Screens Feature Pack，請參閱[發行說明](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js)。

## 設定ACL {#setting-up-acls}

設定ACL說明如何隔離專案，讓每個人或團隊都能處理各自的專案。

有關詳細資訊，請參閱[設定ACL](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html)。

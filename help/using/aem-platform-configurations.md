---
title: AEM平台組態
description: 頁面說明AEM平台組態
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---

# AEM平台組態 {#platform-configurations}

>[!NOTE]
>
>此活動的一般利害關係人是AEM實作人員。

若要開始使用AEM Screens，請遵循下列區段來設定AEM平台設定

## 伺服器設定 {#server-configurations}

若要設定伺服器設定，請參閱[伺服器設定](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration)。

## Author-Publish {#author-publish}

請參閱[在AEM Screens中設定作者與發佈](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)。

>[!NOTE]
>
>如果只有一個Author和一個Publish，您只能按照[在AEM Screens中設定Author和Publish &#x200B;](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)頁面中&#x200B;**在Author**&#x200B;上設定Replication Agent下的步驟操作。

## Dispatcher 設定 {#dispatcher-configurations}

Dispatcher是Adobe Experience Manager的快取與負載平衡工具。 使用 AEM 的 Dispatcher 也有助於保護您的 AEM 伺服器不受攻擊。因此，您可以將Dispatcher搭配企業級網頁伺服器使用，以提高AEM執行個體的安全性。

請參閱&#x200B;**[AEM Screens的Dispatcher設定](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)**，其中強調為AEM Screens專案設定Dispatcher的指引。

## 安裝FFMpeg和視訊轉譯 {#installing-ffmpeg}

請依照適當作業系統（通常是RHEL）的步驟安裝FFMpeg：

1. 如果透過啟用EPEL和RPMFusion進行安裝，您可以安裝所有的gstreamer轉碼器，以擴大對FFmpeg轉換的支援
1. 如果AAC轉碼器標示為實驗性，ffmpeg轉換會失敗。 若要避免此問題，請新增`-strict -2`至視訊設定檔(`/etc/dam/video` (在AEM 6.3中)並移至`/libs/settings/dam/video in AEM 6.4`)

   >[!NOTE]
   >
   >`-strict -2`必須是引數清單中的最後一個引數。 此外，在AEM 6.4中，將&#x200B;*/libs/settings/dam/video*&#x200B;底下的節點複製到&#x200B;*/conf/global/settings/dam/video*，如[Video Renditions](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions)中所述。
1. 確認已進行視訊轉換，且正在建立轉譯。

## 密碼限制 {#password-restrictions}

必須在AMS執行個體上停用AEM的密碼原則。 也可以使用Screens裝置服務&#x200B;*com.adobe.cq.screens.device.impl.DeviceService*，在Web主控台中交替進行設定
請參閱[在AEM Screens中設定作者和發佈](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)中的&#x200B;**密碼限制**&#x200B;區段

## 設定環境 {#setting-up-environments}

針對您的Adobe Experience Manager (AEM)版本安裝並執行下列套件的最新版本：

* AEM Service Pack
* Screens Feature Pack
* AEM Cumulative Fix Pack

除了上述內容，請識別任何開發套件(例如WCM Core
元件)或所需的協力廠商工具組（例如SAP Hybris）。
在本機開發環境中安裝相同的軟體套件。 指示您的使用者端在其所有QA、Stage及生產伺服器上採用相同的設定。 不相符的伺服器設定會在部署和測試時造成問題。

>[!NOTE]
>
>若要安裝最新的AEM Screens Feature Pack，請參閱[發行說明](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/aem-screens-introduction)。

## 設定ACL {#setting-up-acls}

設定ACL說明如何區隔專案，讓每個個人或團隊處理自己的專案。

如需詳細資訊，請參閱[設定ACL](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/administering/setting-up-acls)。

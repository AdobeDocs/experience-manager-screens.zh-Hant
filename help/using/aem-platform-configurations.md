---
title: AEM平台組態
description: 此頁面說明AEM平台組態
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 3%

---

# AEM平台組態  {#platform-configurations}

>[!NOTE]
>
>此活動的典型利害關係人是AEM實作人員。

若要開始使用AEM Screens，請遵循以下區段來設定AEM平台設定

## 伺服器設定 {#server-configurations}

若要設定伺服器組態，請參閱 [伺服器設定](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration).

## Author-Publish {#author-publish}

另請參閱 [在AEM Screens中設定作者和發佈](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

>[!NOTE]
>
>如果只有一個「作者」和一個「發佈」，您只能遵循下的步驟 **在作者上設定復寫代理** 在 [在AEM Screens中設定作者和發佈](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish) 頁面。

## Dispatcher 設定 {#dispatcher-configurations}

Dispatcher是Adobe Experience Manager的快取與負載平衡工具。 使用 AEM 的 Dispatcher 也有助於保護您的 AEM 伺服器不受攻擊。因此，您可以將Dispatcher搭配企業級網頁伺服器使用，以提高AEM執行個體的安全性。

另請參閱 **[適用於AEM Screens的Dispatcher設定](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)** 它會強調為AEM Screens專案設定Dispatcher的准則。

## 安裝FFMpeg和視訊轉譯 {#installing-ffmpeg}

請依照適當作業系統（通常是RHEL）的步驟安裝FFMpeg：

1. 如果透過啟用EPEL和RPMFusion進行安裝，您可以安裝所有的gstreamer轉碼器，以擴大對FFmpeg轉換的支援
1. 如果AAC轉碼器標示為實驗性，ffmpeg轉換會失敗。 若要避免此新增 `-strict -2` 至視訊設定檔(AEM 6.3中的/etc/dam/video，並移至AEM 6.4中的/libs/settings/dam/video)

   >[!NOTE]
   >
   >此 `-strict -2` 必須是引數清單中的最後一個引數。 此外，在AEM 6.4中，複製 */libs/settings/dam/video* 至 */conf/global/settings/dam/video* 如中所述 [視訊轉譯](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions).
1. 確認已進行視訊轉換，且正在建立轉譯。

## 密碼限制 {#password-restrictions}

必須在AMS執行個體上停用AEM的密碼原則。 這可以在Web主控台中使用Screens裝置服務進行交替設定 *com.adobe.cq.screens.device.impl.DeviceService*
另請參閱 **密碼限制** 中的區段[在AEM Screens中設定作者和發佈](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)

## 設定環境 {#setting-up-environments}

針對您的Adobe Experience Manager (AEM)版本安裝並執行下列套件的最新版本：

* AEM Service Pack
* Screens Feature Pack
* AEM Cumulative Fix Pack

除了上述內容，請識別所需的任何開發套件（例如WCM核心元件）或協力廠商工具套件（例如SAP Hybris）。
在本機開發環境中安裝相同的軟體套件。 指示您的使用者端在其所有QA、Stage及生產伺服器上採用相同的設定。 不相符的伺服器設定會在部署和測試時造成問題。

>[!NOTE]
>
>若要安裝AEM Screens的最新Feature Pack，請參閱 [發行說明](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/aem-screens-introduction).

## 設定ACL {#setting-up-acls}

設定ACL說明如何區隔專案，讓每個個人或團隊處理自己的專案。

請參閱 [設定ACL](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/setting-up-acls) 以取得更多詳細資料。

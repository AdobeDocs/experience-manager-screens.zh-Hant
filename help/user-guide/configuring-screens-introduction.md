---
title: 設定和部署AEM Screens
description: AEM Screens Player適用於Android&amp；trade；、Chrome作業系統、iOS和Windows。 瞭解AEM Screens的設定和部署。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
role: Admin
level: Intermediate
exl-id: 8cf4240c-1d6c-441d-b8a0-f01516455543
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 1%

---

# 設定和部署AEM Screens {#configuring-and-deploying-aem-screens}

此頁面說明如何在裝置上安裝和設定Screens播放器。

## 伺服器設定 {#server-configuration}

>[!IMPORTANT]
>
>AEM Screens Player不使用跨網站請求偽造(CSRF)權杖。 因此，若要設定AEM伺服器以準備用於AEM Screens，請允許空白反向連結以略過反向連結篩選器。

## 健康情況檢查架構 {#health-check-framework}

健康情況檢查架構可讓使用者在執行AEM Screens專案之前，先檢查是否已設定兩個必要的設定。

它可讓使用者驗證以下兩個設定檢查以執行AEM Screens專案，即檢查以下兩個篩選器的狀態：

1. **允許空的反向連結**
2. **https**

請依照下列步驟，檢查這兩個重要設定是否已為AEM Screens啟用：

1. 導覽至[Adobe Experience Manager Web主控台Sling健康狀態檢查](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=)。

   ![個資產](assets/health-check1.png)


2. 按一下&#x200B;**執行選取的健康情況檢查**，這樣您就可以執行上述兩個屬性的驗證。

   如果兩個篩選器皆已啟用，則&#x200B;**Screens設定健康情況服務**&#x200B;會將&#x200B;**結果**&#x200B;顯示為&#x200B;**確定**，且兩個設定皆已啟用。

   ![個資產](assets/health-check2.png)

   如果停用其中一個或兩個篩選器，則會顯示通知給使用者，如下圖所示。

   如果兩個篩選器皆已停用，則會顯示下列警報：
   ![個資產](assets/health-check3.png)

>[!NOTE]
>
>* 若要啟用&#x200B;**Apache Sling反向連結篩選器**，請參閱[允許空的反向連結要求](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests)。
>* 若要啟用&#x200B;**HTTP**&#x200B;服務，請參閱[Apache Felix Jetty型HTTP服務](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service)。

### 先決條件 {#prerequisites}

以下要點有助於設定和AEM伺服器，以便用於AEM Screens。

#### 允許空的反向連結請求 {#allow-empty-referrer-requests}

1. 透過AEM執行個體>槌子圖示> **作業** > **網頁主控台**，瀏覽至&#x200B;**Adobe Experience Manager Web主控台設定**。

   ![影像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web主控台組態**&#x200B;開啟。 搜尋Sling查閱者。

   若要搜尋Sling查閱者屬性，請按&#x200B;**Command+F**&#x200B;搜尋&#x200B;**Mac**，然後按&#x200B;**Control+F**&#x200B;搜尋&#x200B;**Windows**。

1. 勾選&#x200B;**允許空白**&#x200B;選項，如下圖所示。

   ![影像](assets/config/empty-ref2.png)

1. 按一下&#x200B;**儲存**&#x200B;以啟用Apache Sling查閱者篩選允許空白。


#### Apache Felix Jetty型HTTP服務 {#allow-apache-felix-service}

1. 透過AEM執行個體>槌子圖示> **作業** > **網頁主控台**，瀏覽至&#x200B;**Adobe Experience Manager Web主控台設定**。

   ![影像](assets/config/empty-ref1.png)

1. **Adobe Experience Manager Web主控台組態**&#x200B;開啟。 搜尋Apache Felix Jetty型HTTP服務。

   若要搜尋此屬性，請按下&#x200B;**Command+F** (針對&#x200B;**Mac**)和&#x200B;**Control+F** （針對&#x200B;**Windows**）。

1. 核取&#x200B;**啟用HTTP**&#x200B;選項，如下圖所示。

   ![影像](assets/config/config-1.png)

1. 按一下[儲存]以啟用&#x200B;*Http*&#x200B;服務。****

#### 啟用AEM Screens的Touch UI {#enable-touch-ui-for-aem-screens}

AEM Screens需要TOUCH UI，無法搭配Adobe Experience Manager (AEM)的Classic UI使用。

1. 瀏覽至`*<yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*`
1. 請確定&#x200B;**預設編寫UI模式**&#x200B;設定為&#x200B;**觸控式**，如下圖所示

或者，您也可以使用yourAuthorInstance *>*&#x200B;工具（槌子圖示） > **作業** > **Web主控台**&#x200B;執行相同的設定，並搜尋&#x200B;**WCM編寫UI模式服務**。

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>您一律可以使用使用者偏好設定為特定使用者啟用傳統UI。

#### NOSAMPLECONTENT執行模式中的AEM {#aem-in-nosamplecontent-runmode}

在生產環境中執行AEM會使用&#x200B;**NOSAMPLECONTENT**&#x200B;執行模式。 從移除&#x200B;*X-Frame-Options=SAMEORIGIN*&#x200B;標頭（在其他回應標頭區段中）

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`。

您必須移除此專案，AEM Screens Player才能播放線上頻道。

#### 密碼限制 {#password-restrictions}

有了對&#x200B;***DeviceServiceImpl***&#x200B;的最新變更，您不必移除密碼限制。

您可以透過下列連結設定&#x200B;***DeviceServiceImpl***，在建立熒幕裝置使用者的密碼時啟用密碼限制：

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

請依照下列步驟設定&#x200B;***DeviceServiceImpl***：

1. 透過您的AEM執行個體>槌子圖示> **作業** > **網頁主控台**，瀏覽至&#x200B;**Adobe Experience Manager Web主控台設定**。

1. **Adobe Experience Manager Web主控台組態**&#x200B;開啟。 搜尋`*deviceservice*`。 若要搜尋屬性，請按下&#x200B;**Command+F** (適用於macOS)和&#x200B;**Control+F** (適用於Microsoft® Windows)。

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher 設定 {#dispatcher-configuration}

若要瞭解如何為AEM Screens專案設定Dispatcher，請參閱[為AEM Screens專案設定Dispatcher](dispatcher-configurations-aem-screens.md)。

#### Java™編碼 {#java-encoding}

將&#x200B;***Java™編碼***&#x200B;設定為Unicode。 例如，`*Dfile.encoding=Cp1252*`無法運作。

>[!NOTE]
>
>在生產環境中使用AEM Screens Server適用的HTTPS 。

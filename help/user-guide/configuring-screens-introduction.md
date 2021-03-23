---
title: 配置和部署AEM Screens
seo-title: 設定和部署畫面
description: AEM Screens播放器適用於Android、Chrome OS、iOS和Windows。 本頁說明AEM Screens的配置和部署，並摘要播放器裝置的h/w選擇准則。
seo-description: AEM Screens播放器適用於Android、Chrome OS、iOS和Windows。 本頁說明AEM Screens的配置和部署，並摘要播放器裝置的h/w選擇准則。
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
role: 管理員
level: 中級
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 0%

---


# 配置和部署AEM Screens{#configuring-and-deploying-aem-screens}

本頁說明如何在您的裝置上安裝和設定畫面播放器。

## 伺服器配置{#server-configuration}

>[!NOTE]
>
>**重要**:
>
>AEM Screens播放器不會使用跨網站偽造要求(CSRF)代號。 因此，為了設定和伺服器AEM可供AEM Screens使用，請允許空的反向連結，以略過反向連結篩選。

## Health Check Framework {#health-check-framework}

Health Check framework允許用戶在運行AEM Screens項目之前檢查是否設定了兩個必要的配置。

它允許用戶驗證以下兩個配置檢查以運行AEM Screens項目，即檢查以下兩個篩選器的狀態：

1. **允許空的反向連結**
2. **https**

請遵循下列步驟，檢查是否為AEM Screens啟用了這兩個重要配置：

1. 導覽至[Adobe Experience Manager網站主控台Sling Health Check](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=)。

   ![資產](assets/health-check1.png)


2. 按一下&#x200B;**執行所選健康檢查**&#x200B;以運行上述兩個屬性的驗證。

   如果同時啟用了這兩個篩選器，則&#x200B;**Screens Configuration Health Service**&#x200B;將&#x200B;**Result**&#x200B;顯示為&#x200B;**OK**，並且兩個配置都啟用。

   ![資產](assets/health-check2.png)

   如果一個或兩個篩選器都被禁用，則會為用戶顯示警報，如下圖所示。

   如果同時禁用了這兩個過濾器，以下警報將顯示：
   ![資產](assets/health-check3.png)

>[!NOTE]
>
>* 若要啟用&#x200B;**Apache Sling Referrer Filter**，請參閱[Allow Empty Referrer Requests](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests)。
>* 要啟用&#x200B;**HTTP**&#x200B;服務，請參閱[Apache Felix Jetty Based HTTP Service](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service)。


### 必備條件 {#prerequisites}

以下關鍵點有助於配置和服AEM務器以便準備用於AEM Screens。

#### 允許空的反向連結請求{#allow-empty-referrer-requests}

1. 導航至&#x200B;**Adobe Experience ManagerWeb控制台配置**(通過實例AEM—>槌子表徵圖—> **操作** —> **Web控制台**)。

   ![影像](assets/config/empty-ref1.png)

1. **Adobe Experience ManagerWeb控制台** 配置開啟。搜尋sling referrer。

   若要搜尋sling referrer屬性，請按&#x200B;**Command+F**&#x200B;以取得&#x200B;**Mac**&#x200B;和&#x200B;**Control+F**&#x200B;取得&#x200B;**Windows**。

1. 選中&#x200B;**允許空**&#x200B;選項，如下圖所示。

   ![影像](assets/config/empty-ref2.png)

1. 按一下&#x200B;**Save**&#x200B;以啟用Apache Sling Referrer Filter Allow Empty。


#### 基於Apache Felix Jetty的HTTP服務{#allow-apache-felix-service}

1. 導航至&#x200B;**Adobe Experience ManagerWeb控制台配置**(通過實例AEM—>槌子表徵圖—> **操作** —> **Web控制台**)。

   ![影像](assets/config/empty-ref1.png)

1. **Adobe Experience ManagerWeb控制台** 配置開啟。搜尋以Apache Felix Jetty為基礎的HTTP服務。

   要搜索此屬性，請按&#x200B;**Command+F**&#x200B;鍵（對於&#x200B;**Mac**），按&#x200B;**Control+F**&#x200B;鍵（對於&#x200B;**Windows**）。

1. 選中&#x200B;**ENABLE HTTP**&#x200B;選項，如下圖所示。

   ![影像](assets/config/config-1.png)

1. 按一下&#x200B;**保存**&#x200B;以啟用&#x200B;*http*&#x200B;服務。

#### 為AEM Screens啟用Touch UI {#enable-touch-ui-for-aem-screens}

AEM Screens需要TOUCH UI，而且無法與Adobe Experience Manager的CLASSIC UI搭配使用(AEM)。

1. 導覽至&#x200B;*&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. 請確定&#x200B;**預設編寫UI模式**&#x200B;已設為&#x200B;**TOUCH**，如下圖所示

或者，您也可以使用AuthorInstance *->*&#x200B;工具（槌子圖示）-> **Operations** -> **Web Console**&#x200B;執行相同的設定，並搜尋&#x200B;**WCM編寫UI模式服務**。

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>您隨時都可以使用使用者偏好設定，為特定使用者啟用Classic UI。

#### 在AEMNOSAMPLECONTENT運行模式{#aem-in-nosamplecontent-runmode}中

在生AEM產中運行使用&#x200B;**NOSAMPLECONTENT**&#x200B;運行模式。 將&#x200B;*X-Frame-Options=SAMEORIGIN*&#x200B;標題（在其他回應標題區段中）從

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`。

這是AEM Screens播放器播放線上頻道的必要項。

#### 密碼限制{#password-restrictions}

對&#x200B;***DeviceServiceImpl***&#x200B;進行最新變更後，您不必移除密碼限制。

您可以從以下連結配置&#x200B;***DeviceServiceImpl***，以在為螢幕設備用戶建立密碼時啟用密碼限制：

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

請依照下列步驟配置&#x200B;***DeviceServiceImpl***:

1. 導航至&#x200B;**Adobe Experience ManagerWeb控制台配置**(通過實例AEM—>槌子表徵圖—> **操作** —> **Web控制台**)。

1. **Adobe Experience ManagerWeb控制台** 配置開啟。搜索&#x200B;*deviceservice*。 要搜索屬性，請按&#x200B;**Command+F**（適用於macOS）和&#x200B;**Control+F**（適用於Microsoft Windows）。

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher Configuration {#dispatcher-configuration}

要瞭解如何為AEM Screens項目配置調度程式，請參閱[為AEM Screens項目配置調度程式](dispatcher-configurations-aem-screens.md)。

#### Java編碼{#java-encoding}

將&#x200B;***Java encoding***&#x200B;設為Unicode。 例如，*Dfile.encoding=Cp1252*&#x200B;將無法運作。

>[!NOTE]
>**建議：**
>建議在生產使用中使用HTTPS給AEM Screens伺服器。









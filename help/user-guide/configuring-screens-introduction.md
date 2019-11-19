---
title: 設定和部署AEM畫面
seo-title: 設定和部署畫面
description: AEM Screens播放器適用於Android、Chrome OS、iOS和Windows。 本頁面說明AEM畫面的設定和部署，並摘要播放器裝置的h/w選取方針。
seo-description: AEM Screens播放器適用於Android、Chrome OS、iOS和Windows。 本頁面說明AEM畫面的設定和部署，並摘要播放器裝置的h/w選取方針。
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 設定和部署AEM畫面 {#configuring-and-deploying-aem-screens}

本頁說明如何在您的裝置上安裝和設定畫面播放器。

## 安裝AEM Screens Player {#installing-aem-screens-player}

AEM Screens播放器適用於Android、Chrome OS、iOS和Windows。

若要下 **載AEM Screens Player**，請造訪 [**AEM 6.5 Player下載頁面**](https://download.macromedia.com/screens/) 。

>[!NOTE]
>
>下載最新的播放器(*.exe*)後，請依照播放器上的步驟完成臨機安裝：
>
>1. 長按左上角以開啟管理面板。
>1. 從左側 **動作功能表導覽至** 「設定」，然後在 **Server中輸入AEM例項的位置位址，然後按一下「儲** 存」 ****。
>1. 按一下左 **側動作功能表** 中的「註冊」連結，以及下列步驟以完成裝置註冊程式。
>



### 其他資源 {#additional-resources}

如需深入資訊，請參閱下列主題：

* 若要下載Android Player，請造 **訪Google Play**。 若要瞭解實作Android Watchdog的相關資訊，請參閱實 [作Android播放器](implementing-android-player.md)。

* 若要實作Chrome OS Player，請參閱 [Chrome Management Console](implementing-chrome-os-player.md) ，以取得詳細資訊。

* 若要設定AEM Screens Windows player，請參閱「 [實作Windows Player](implementing-windows-player.md)」。

## Server Configuration {#server-configuration}

>[!NOTE]
>
>**重要**:
>
>AEM Screens播放器不會使用跨網站偽造要求(CSRF)代號。 因此，若要設定AEM伺服器並讓AEM伺服器準備好用於AEM畫面，請允許空的反向連結，以略過反向連結篩選。

### 必備條件 {#prerequisites}

下列關鍵點可協助您設定AEM伺服器並讓AEM伺服器準備好用於AEM畫面：

#### 允許空的反向連結請求 {#allow-empty-referrer-requests}

1. 導覽至**Adobe Experience Manager Web Console設定**，透過AEM實例—&gt;槌子圖示—&gt; **Operations** —&gt; **Web Console**。

   ![screen_shot_2019-07-31at91253am](assets/screen_shot_2019-07-31at91253am.png)

1. **Adobe Experience Manager Web Console設定隨即開啟** 。 搜尋sling referrer。

   若要搜尋sling referrer屬性，請按 **Command+F** for **Mac** , **Control+F** for **** Windows。

   ![screen_shot_2019-07-31at91728am](assets/screen_shot_2019-07-31at91728am.png)

1. 勾選「允許空白」**選項，如下圖所示。

   ![screen_shot_2019-07-31at91807am](assets/screen_shot_2019-07-31at91807am.png)

1. 按一 **下「儲存** 」以啟用Apache Sling Referrer Filter Allow Empty。

#### 為AEM螢幕啟用Touch UI {#enable-touch-ui-for-aem-screens}

AEM Screens需要TOUCH UI，無法與Adobe Experience Manager(AEM)的CLASSIC UI搭配使用。

1. 導覽至 *&lt;yourAuthorInstance&gt;/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. 請確定「預 **設編寫UI** 」模式已設 **為TOUCH**，如下圖所示

或者，您也可以使用*&lt;yourAuthorInstance&gt; *-&gt;* tools（槌子圖示）* -&gt; **Operations** -&gt;** Web Console**執行相同的設定，並搜尋 **WCM編寫UI模式服務**。

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>您隨時都可以使用使用者偏好設定，為特定使用者啟用Classic UI。

#### NOSAMPLECONTENT執行模式中的AEM {#aem-in-nosamplecontent-runmode}

在生產中執行AEM會使 **用NOSAMPLECONTENT** 執行模式。 從&#x200B;*RemovetheX-Frame-Options=SAMEORIGIN* （在其他回應標題區段中）

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

這是AEM Screens Player播放線上頻道的必要項。

#### 密碼限制 {#password-restrictions}

對 ***DeviceServiceImpl進行最新變更***，您不必移除密碼限制。

您可以從 ***下列連結設定DeviceServiceImpl*** ，以在為畫面裝置使用者建立密碼時啟用密碼限制：

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

請依照下列步驟來設定 ***DeviceServiceImpl***:

1. 導覽至**Adobe Experience Manager Web Console設定**，透過AEM實例—&gt;槌子圖示—&gt; **Operations** —&gt; **Web Console**。

1. **Adobe Experience Manager Web Console設定**開啟。 搜尋裝置服務。 要搜索屬性，請按 **Command+F** ( **Mac)和Control+F(****Windows)** ( **** Windows)。

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Dispatcher Configuration {#dispatcher-configuration}

若要瞭解如何為AEM Screens專案設定分派程式，請參閱「為AEM Screens專案 [設定Dispatcher」](dispatcher-configurations-aem-screens.md)。

#### Java編碼 {#java-encoding}

將 ***Java編碼設為*** Unicode。 例如， *Dfile.encoding=Cp1252* 將無法運作。

>[!NOTE]
>
>**建議：**
>
>建議在生產使用中，將HTTPS用於AEM Screens Server。


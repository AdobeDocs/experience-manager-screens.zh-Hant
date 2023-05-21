---
title: 使用編輯器嵌入REACT應AEM用SPA程式並與AEM Screens分析整合
seo-title: Embedding a REACT application using the AEM SPA Editor and Integrating with AEM Screens Analytics
description: 請按照本頁瞭解如何使用REACT(或Angular)嵌入互動式單頁應用程式AEM，並了SPA解如何使用可由業務專業人員配置的編輯器AEM，以及如何將互動式應用程式與離線Adobe Analytics整合。
seo-description: Follow this page to learn how to embed an interactive single page application using REACT (or Angular) using the AEM SPA editor that can be configured by business professionals in AEM and also how to integrate your interactive application with offline Adobe Analytics.
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 7dc7d07e-cd94-4ce1-a106-98669be62046
source-git-commit: ffc44dbf1822ff4d0e875ef693d48dece248d555
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# 使用編輯器嵌入REACT應AEM用SPA程式並與AEM Screens分析整合 {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

本節介紹如何使用REACT(或Angular)嵌入互動式單頁應用程式AEM,SPA該編輯器可由業務專業人員在中配置AEM，以及如何將互動式應用程式與離線Adobe Analytics整合。

## 使用編AEM輯SPA器 {#using-the-aem-spa-editor}

按照以下步驟使用編AEM輯SPA器：

1. 克隆AEM編SPA輯器回購 [https://github.com/adobe/aem-spa-project-archetype。](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >這種原型創造了一個最小的Adobe Experience Manager項目作為你自己項目的SPA起點。 使用此原型時必須提供的屬性允許將此項目的所有部分命名為所需的名稱。

1. 按照自述說明建立編AEM輯器SPA原型項目：

   ```
   mvn clean install archetype:update-local-catalog
   mvn archetype:crawl
   
   mvn archetype:generate \
   -DarchetypeCatalog=internal \
   -DarchetypeGroupId=com.adobe.cq.spa.archetypes \
   -DarchetypeArtifactId=aem-spa-project-archetype \
   -DarchetypeVersion=1.0.3-SNAPSHOT \
   ```

   >[!NOTE]
   >
   >我們使用 **組ID** 如 ***com.adobe.aem.screens*** 和 **項目ID** 如 ***我的樣SPA例*** （即預設值）。 您可以根據需要選擇自己的。

1. 建立項目後，請使用所選的IDE或編輯器並導入生成的Maven項目。
1. 使用命令部署AEM到本地實例 ***mvn全新安裝 — PautoInstallPackage***。

### 在REACT應用中編輯內容 {#editing-content-in-the-react-app}

要編輯REACT應用中的內容：

1. 導航到 `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` （根據需要替換主機名、埠和項目名）。
1. 您應該能夠編輯Hello world應用程式中顯示的文本。

### 將互動式REACT應用添加到AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

按照以下步驟將互動式REACT應用添加到AEM Screens:

1. 新建AEM Screens項目。 請參閱 [建立和管理項目](creating-a-screens-project.md) 的子菜單。

1. 新建 **應用程式通道** （最好是）（或1x1模板或多區通道） **頻道** 「螢幕」項目的資料夾。

   >[!NOTE]
   >**序列通道** 對於此使用情形，不鼓勵使用，因為它們天生帶有與體驗的交互性質相衝突的幻燈片放映邏輯
   >請參閱 [建立和管理渠道](managing-channels.md) 的子菜單。


1. 編輯任何序列通道，並拖放嵌入的頁面元件。

   請參閱 [將元件添加到通道](adding-components-to-a-channel.md) 的子菜單。

   >[!NOTE]
   >
   >確保在為顯示器分配通道時添加用戶交互事件。

1. 按一下 **編輯** 的子菜單。

   ![screen_shot_2019-02-15at10055am](assets/screen_shot_2019-02-15at100555am.png)

1. 拖放 **嵌入式頁** 或重新使用應用程式通道中的現有元件，並選擇mysamplespa應用程式下的首頁，例如 ***/content/mysamplespa/en/home***。

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. 將通道指定給顯示器。

   >[!NOTE]
   >確保在為顯示器分配通道時添加用戶交互事件。

1. 根據此項目註冊播放器並將其分配給顯示器。 現在，您應該能夠看到您的互動式應用程式在AEM Screens上運行。

   請參閱 [設備註冊](device-registration.md) 詳細瞭解註冊設備。

## 通過SPAAEM Screens將Adobe Analytics與離線功能整合 {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

按照以下步驟通過SPAAEM Screens與Adobe Analytics整合，並提供離線功能：

1. 在AEM Screens配置Adobe Analytics。

   請參閱 [配置Adobe Analytics與AEM Screens](configuring-adobe-analytics-aem-screens.md) 瞭解如何與AEM Screens一起在Adobe Analytics執行排序，以及使用離線Adobe Analytics發送自定義事件。

1. 在您選擇的IDE/編輯器中編輯您的反應應用（尤其是要開始發出事件的文本元件或其他元件）。
1. 在要為元件捕獲的按一下事件或其他事件上，使用標準資料模型添加分析資訊。

   請參閱 [配置Adobe Analytics與AEM Screens](configuring-adobe-analytics-aem-screens.md)的子菜單。

1. 調用AEM Screens分析API以離線保存事件並以突發形式將其發送到Adobe Analytics。

   例如，

   ```
   handleClick() {
       if ((window.parent) && (window.parent.CQ) && (window.parent.CQ.screens) && (window.parent.CQ.screens.analytics))
       {
           var analyticsEvent = {};
           analyticsEvent['event.type'] = 'play'; // Type of event
    analyticsEvent['event.coll_dts'] = new Date().toISOString(); // Start of collecting the event
    analyticsEvent['event.dts_start'] = new Date().toISOString(); // Event start
    analyticsEvent['content.type'] = 'Washing machine'; // Mime Type or product category
    analyticsEvent['content.action'] = 'Path to the washing machine asset in AEM'; // Path in AEM to relevant asset
    analyticsEvent['trn.product'] = 'Washing machine Model number'; // Product being explored
    analyticsEvent['trn.amount'] = 1000; // Product pricing or other numeric value or weight
    analyticsEvent['event.dts_end'] = new Date().toISOString(); // Event end
    analyticsEvent['event.count'] = 100; // Numeric value that may count a number of clicks or keystrokes or wait time in seconds for example
    analyticsEvent['event.value'] = 'My favorite analytics event';
           analyticsEvent['trn.quantity'] = 10; // Quantity of product selection
    analyticsEvent['event.subtype'] = 'end'; // Event subtype if applicable
    window.parent.CQ.screens.analytics.sendTrackingEvent(analyticsEvent);
       }
   }
   ```

   >[!NOTE]
   >
   >播放器韌體會自動將有關播放器及其運行時環境的詳細資訊添加到您發送的自定義分析資料中。 因此，除非絕對必要，否則您可能不需要捕獲低級作業系統/設備詳細資訊。 你只需要關注業務分析資料。

---
title: 使用AEM SPA編輯器內嵌REACT應用程式並與AEM Screens Analytics整合
seo-title: 使用AEM SPA編輯器內嵌REACT應用程式並與AEM Screens Analytics整合
description: 請依照本頁瞭解如何使用AEM SPA編輯器（可由AEM的商業專業人員設定）使用REACT（或Angular）內嵌互動式單頁應用程式，以及如何將互動式應用程式與離線Adobe Analytics整合。
seo-description: 請依照本頁瞭解如何使用AEM SPA編輯器（可由AEM的商業專業人員設定）使用REACT（或Angular）內嵌互動式單頁應用程式，以及如何將互動式應用程式與離線Adobe Analytics整合。
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 0%

---


# 使用AEM SPA編輯器內嵌REACT應用程式，並與AEM Screens Analytics {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}整合

本節說明如何使用AEM SPA編輯器（可由AEM的商業專業人員設定），使用REACT（或Angular）內嵌互動式單頁應用程式，以及如何將互動式應用程式與離線Adobe Analytics整合。

## 使用AEM SPA編輯器{#using-the-aem-spa-editor}

請依照下列步驟來使用AEM SPA編輯器：

1. 複製位於[https://github.com/adobe/aem-spa-project-archetype的AEM SPA Editor repo。](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >此原型會建立最小的Adobe Experience Manager專案，做為您自己SPA專案的起點。 使用此原型時必須提供的屬性允許根據需要命名此項目的所有部分。

1. 請依照讀我檔案的指示建立AEM SPA編輯器原型專案：

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
   >我們使用&#x200B;**GroupId**&#x200B;作為&#x200B;***com.adobe.aem.screens***&#x200B;和&#x200B;**ArtifactId**&#x200B;作為&#x200B;***我的範例SPA***（這是預設值）。 您可以視需要選擇自己的產品。

1. 在建立項目後，請使用您選擇的IDE或編輯器並導入生成的Maven項目。
1. 使用命令&#x200B;***mvn clean install -PautoInstallPackage***&#x200B;部署至您的本機AEM實例。

### 在REACT應用程式中編輯內容{#editing-content-in-the-react-app}

要編輯REACT應用程式中的內容：

1. 導覽至`https://localhost:4502/editor.html/content/mysamplespa/en/home.html`（視適用情況取代主機名、埠和專案名稱）。
1. 您應該可以編輯Hello World應用程式中顯示的文字。

### 將互動式REACT應用程式新增至AEM畫面{#adding-the-interactive-react-app-to-aem-screens}

請依照下列步驟，將互動式REACT應用程式新增至AEM畫面：

1. 建立新的AEM Screens專案。 有關詳細資訊，請參閱[建立和管理項目](creating-a-screens-project.md)。

   >[!NOTE]
   >
   >在畫面專案的&#x200B;**頻道**&#x200B;資料夾中建立頻道時，建立&#x200B;**順序頻道**。
   >
   >
   >有關詳細資訊，請參閱[建立和管理通道](managing-channels.md)。

   ![screen_shot_2019-02-15at100330am](assets/screen_shot_2019-02-15at100330am.png)

1. 編輯任何序列頻道，並拖放內嵌的頁面元件。

   有關詳細資訊，請參閱[將元件添加到通道](adding-components-to-a-channel.md)。

   >[!NOTE]
   >
   >在指派頻道至顯示時，請務必新增使用者互動事件。

1. 按一下操作欄中的&#x200B;**編輯**&#x200B;以編輯序列通道的屬性。

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. 拖放&#x200B;**內嵌頁面**&#x200B;元件，並選取mysamplespa應用程式下的首頁，例如&#x200B;***/content/mysamplespa/en/home***。

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. 針對此專案註冊播放器，您現在應該可以在AEM畫面上看到您的互動式應用程式。

   請參閱[裝置註冊](device-registration.md)以詳細瞭解註冊裝置。

## 透過AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}將SPA與Adobe Analytics與離線功能整合

請依照下列步驟，透過AEM Screens將SPA與Adobe Analytics整合為離線功能：

1. 在AEM畫面中設定Adobe Analytics。

   請參閱「使用AEM Screens設定Adobe Analytics[」以瞭解如何在「使用AEM Screens進行Adobe Analytics中執行排序，以及使用離線Adobe Analytics傳送自訂事件」。](configuring-adobe-analytics-aem-screens.md)

1. 在您選擇的IDE/編輯器中編輯您的反應應用程式（尤其是要開始發出事件的文字元件或其他元件）。
1. 在您要擷取元件的點按事件或其他事件上，使用標準資料模型新增分析資訊。

   如需詳細資訊，請參閱「使用AEM畫面設定Adobe Analytics」。[](configuring-adobe-analytics-aem-screens.md)

1. 呼叫AEM Screens Analytics API，將事件離線儲存並以突發方式傳送至Adobe Analytics。

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
   >播放器韌體會自動將有關播放器及其執行時期環境的更多詳細資料新增至您傳送的自訂分析資料。 因此，除非絕對必要，否則您可能不需要擷取低階作業系統／裝置詳細資訊。 您只需要專注於業務分析資料。


---
title: 使用AEM SPA編輯器內嵌REACT應用程式並與AEM Screens Analytics整合
description: 瞭解如何使用AEM SPA編輯器使用REACT (或Angular)內嵌互動式單頁應用程式。
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 7dc7d07e-cd94-4ce1-a106-98669be62046
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 0%

---

# 使用AEM SPA編輯器內嵌REACT應用程式並與AEM Screens Analytics整合 {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

您可以使用REACT (或Angular)內嵌互動式單頁應用程式。 您可以使用AEM SPA編輯器來執行此操作，由AEM中的商務專業人士進行設定。 您也可以瞭解如何將互動式應用程式與離線Adobe Analytics整合。

## 使用AEM SPA編輯器 {#using-the-aem-spa-editor}

請依照下列步驟使用AEM SPA編輯器：

1. 在[https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)複製AEM SPA Editor存放庫

   >[!NOTE]
   >
   >此原型會建立最低限度的Adobe Experience Manager專案，作為您專屬SPA專案的起點。 使用此原型時必須提供的屬性可讓您根據需要命名此專案的所有部分。

1. 若要建立AEM SPA編輯器原型專案，請依照讀我檔案的說明操作：

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
   >本檔案使用&#x200B;**GroupId**&#x200B;做為&#x200B;***com.adobe.aem.screens***，使用&#x200B;**ArtifactId**&#x200B;做為&#x200B;***我的範例SPA*** （預設）。 您可以視需要選擇自己的網站。

1. 建立專案後，使用您選擇的IDE或編輯器並匯入產生的Maven專案。
1. 使用命令&#x200B;***mvn clean install -PautoInstallPackage***&#x200B;部署到您的本機AEM執行個體。

### 在REACT應用程式中編輯內容 {#editing-content-in-the-react-app}

若要編輯REACT應用程式中的內容：

1. 導覽至`https://localhost:4502/editor.html/content/mysamplespa/en/home.html` （取代適用的主機名稱、連線埠和專案名稱）。
1. 能夠編輯Hello World應用程式中顯示的文字。

### 將互動式REACT應用程式新增至AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

請依照下列步驟，將互動式REACT應用程式新增至AEM Screens：

1. 建立AEM Screens專案。 如需詳細資訊，請參閱[建立和管理專案](creating-a-screens-project.md)。
1. 在您的AEM Screens專案的&#x200B;**Channels**&#x200B;資料夾中建立&#x200B;**應用程式頻道** （最好是） （或1x1範本或多區域頻道）。

   >[!NOTE]
   >不建議針對此使用案例使用&#x200B;**順序頻道**，因為這些頻道本身就包含幻燈片邏輯，與體驗的互動性質衝突。
   >如需詳細資訊，請參閱[建立和管理管道](managing-channels.md)。

1. 編輯任何順序色版，並拖放內嵌的頁面元件。

   如需詳細資訊，請參閱[新增元件至通道](adding-components-to-a-channel.md)。

   >[!NOTE]
   >
   >請務必在指派頻道給顯示區時新增使用者互動事件。

1. 按一下動作列中的[編輯&#x200B;**&#x200B;**]，以便編輯頻道內容。

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. 拖放&#x200B;**內嵌頁面**&#x200B;元件，或重複使用應用程式通道中的現有元件，然後按一下mysamplespa應用程式下的首頁，例如&#x200B;***/content/mysamplespa/en/home***。

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. 將頻道指派給顯示區。

   >[!NOTE]
   >請務必在指派頻道給顯示區時新增使用者互動事件。

1. 針對此專案註冊播放器，並將其指派給顯示區。 您現在可以看到互動式應用程式在AEM Screens上執行。

   如需註冊裝置的詳細資訊，請參閱[裝置註冊](device-registration.md)。

## 透過AEM Screens將SPA與Adobe Analytics與離線功能整合 {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

請依照下列步驟，透過AEM Screens將SPA與Adobe Analytics與離線功能整合：

1. 在AEM Screens中設定Adobe Analytics。

   請參閱[使用AEM Screens設定Adobe Analytics](configuring-adobe-analytics-aem-screens.md)，以取得有關如何使用AEM Screens在Adobe Analytics中執行排序，以及使用離線Adobe Analytics傳送自訂事件的詳細資訊。

1. 在您選擇的IDE/編輯器中編輯您的react應用程式（尤其是文字元件或您要開始發出事件的其他元件）。
1. 在點選事件或您要為元件擷取的其他事件上，使用標準資料模型新增分析資訊。

   如需詳細資訊，請參閱[使用AEM Screens設定Adobe Analytics](configuring-adobe-analytics-aem-screens.md)。

1. 呼叫AEM Screens Analytics API，讓您可以離線儲存事件，並以突發方式傳送至Adobe Analytics。

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
   >播放器韌體會自動將有關播放器及其執行階段環境的更多詳細資訊，新增至您傳送的自訂分析資料。 因此，您可能必須擷取低階作業系統/裝置的詳細資訊，除非有必要。 專注於業務分析資料。

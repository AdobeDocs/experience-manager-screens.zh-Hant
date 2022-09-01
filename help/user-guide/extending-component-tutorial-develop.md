---
title: 擴充AEM Screens元件
seo-title: Extending an AEM Screens Component
description: 下列教學課程將逐步說明擴充現成可用AEM Screens元件的步驟和最佳作法。 擴充影像元件以新增可授權的文字覆蓋。
seo-description: The following tutorial walks through the steps and best practices for extending out of the box AEM Screens components. The Image component is extended to add an authorable text overlay.
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: e316614f-2d40-4b62-a1e5-f30817def742
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '1786'
ht-degree: 2%

---

# 擴充AEM Screens元件 {#extending-an-aem-screens-component}

下列教學課程將逐步說明擴充現成可用AEM Screens元件的步驟和最佳作法。 擴充影像元件以新增可授權的文字覆蓋。

## 總覽 {#overview}

本教學課程適用於剛接觸AEM Screens的開發人員。 在本教學課程中，會擴充Screens影像元件，以建立海報元件。 標題、說明和標誌覆蓋在影像上，以在序列頻道中建立引人入勝的體驗。

>[!NOTE]
>
>開始本教學課程之前，建議您先完成本教學課程： [開發適用於AEM Screens的自訂元件](developing-custom-component-tutorial-develop.md).

![自訂海報元件](assets/2018-05-07_at_4_09pm.png)

自訂海報元件是透過擴充影像元件來建立。

## 必備條件 {#prerequisites}

若要完成本教學課程，您需要執行下列操作：

1. [AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/release-notes.html?lang=zh-Hant) 或 [AEM 6.3](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html) +最新Screens Feature Pack
1. [AEM Screens 播放器](/help/user-guide/aem-screens-introduction.md)
1. 本機開發環境

教學課程步驟和螢幕擷取畫面是使用CRXDE-Lite執行。 [Eclipse](https://experienceleague.adobe.com/docs/experience-manager-64/developing/devtools/aem-eclipse.html) 或 [IntelliJ](https://experienceleague.adobe.com/docs/experience-manager-64/developing/devtools/ht-intellij.html) IDE也可用於完成本教程。 有關使用IDE以 [使用AEM進行開發，可在此處找到](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup.html).

## 專案設定 {#project-setup}

Screens專案的原始碼通常以多模組Maven專案的形式管理。 為加快教學課程的進行，已使用 [AEM專案原型13](https://github.com/adobe/aem-project-archetype). 更多詳細資訊 [若要使用Maven AEM專案原型建立專案，請前往此處](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup.html).

1. 使用 **CRX套件管理** `http://localhost:4502/crx/packmgr/index.jsp)r:`

[取得檔案](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [取得檔案](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **（可選）** 如果使用Eclipse或其他IDE，請下載以下源包。 使用Maven命令將專案部署至本機AEM執行個體：

   **`mvn -PautoInstallPackage clean install`**

   SRC啟動螢幕We.Retail運行項目

[取得檔案](assets/start-poster-screens-weretail-run.zip)

1. 在 **CRX封裝管理器** `http://localhost:4502/crx/packmgr/index.jsp` 安裝了以下兩個軟體包：

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![透過CRX套件管理器安裝的Screens We.Retail執行Ui.Apps和Ui.Content套件](assets/crx-packages.png)

   透過CRX套件管理器安裝的Screens We.Retail執行Ui.Apps和Ui.Content套件

## 建立海報元件 {#poster-cmp}

海報元件會擴展出現的螢幕影像元件。 Sling的機制， `sling:resourceSuperType`，可繼承影像元件的核心功能，而無須複製並貼上。 有關的基本資訊 [您可以在此處找到Sling請求處理。](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/the-basics.html)

海報元件會以全螢幕預覽/生產模式轉譯。 在編輯模式中，請務必以不同方式轉譯元件，以方便編寫序列管道。

1. 在 **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` （或您選擇的IDE） `/apps/weretail-run/components/content`建立 `cq:Component` 已命名 `poster`.

   將下列屬性新增至 `poster` 元件：

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Poster"
       sling:resourceSuperType="screens/core/components/content/image"
       componentGroup="We.Retail Run - Content"/>
   ```

   ![/apps/weretail-run/components/content/poster的屬性](assets/poster.png)

   /apps/weretail-run/components/content/poster的屬性

   設定 `sling:resourceSuperType`屬性等於 `screens/core/components/content/image` 海報元件有效地繼承了影像元件的所有功能。 下面找到的對等節點和檔案 `screens/core/components/content/image` 可以在 `poster` 元件，以覆寫和擴充功能。

1. 複製 `cq:editConfig` 節點下方 `/libs/screens/core/components/content/image.`貼上 `cq:editConfig` 在下面 `/apps/weretail-run/components/content/poster` 元件。

   在 `cq:editConfig/cq:dropTargets/image/parameters` 節點更新 `sling:resourceType` 屬性等於 `weretail-run/components/content/poster`.

   ![edit-config](assets/edit-config.png)

   cq:editConfig的XML表示，如下所示：

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="cq:EditConfig">
       <cq:dropTargets jcr:primaryType="nt:unstructured">
           <image
               jcr:primaryType="cq:DropTargetConfig"
               accept="[image/.*]"
               groups="[media]"
               propertyName="./fileReference">
               <parameters
                   jcr:primaryType="nt:unstructured"
                   sling:resourceType="weretail-run/components/content/poster"
                   imageCrop=""
                   imageMap=""
                   imageRotate=""/>
           </image>
       </cq:dropTargets>
   </jcr:root>
   ```

1. 複製WCM Foundation `image` 對話框 `poster` 元件。

   最簡單的方式是從現有對話方塊開始，然後進行修改。

   1. 從以下位置複製對話框： `/libs/wcm/foundation/components/image/cq:dialog`
   1. 將對話方塊貼到下方 `/apps/weretail-run/components/content/poster`

   ![從/libs/wcm/foundation/components/image/cq:dialog複製到/apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   從/libs/wcm/foundation/components/image/cq:dialog複製到/apps/weretail-run/components/content/poster

   螢幕 `image` 元件被超類到WCM Foundation `image` 元件。 因此， `poster` 元件會從兩者繼承功能。 海報元件的對話方塊由Screens和Foundation對話方塊的組合組成。 的功能 **Sling Resource Merger** 可用來隱藏繼承自超類元件的無關對話方塊欄位和標籤。

1. 更新下方的cq:dialog `/apps/weretail-run/components/content/poster` 以XML表示的以下更改：

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Poster"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/foundation/container">
           <layout
               jcr:primaryType="nt:unstructured"
               sling:resourceType="granite/ui/components/foundation/layouts/tabs"
               type="nav"/>
           <items jcr:primaryType="nt:unstructured">
               <image
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Elements"
                   sling:resourceType="granite/ui/components/foundation/section">
                   <layout
                       jcr:primaryType="nt:unstructured"
                       sling:resourceType="granite/ui/components/foundation/layouts/fixedcolumns"
                       margin="{Boolean}false"/>
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/foundation/container">
                           <items
                               jcr:primaryType="nt:unstructured"
                               sling:hideChildren="[linkURL,size]">
                               <file
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="cq/gui/components/authoring/dialog/fileupload"
                                   autoStart="{Boolean}false"
                                   class="cq-droptarget"
                                   fieldLabel="Image asset"
                                   fileNameParameter="./fileName"
                                   fileReferenceParameter="./fileReference"
                                   mimeTypes="[image]"
                                   multiple="{Boolean}false"
                                   name="./file"
                                   title="Upload Image Asset"
                                   uploadUrl="${suffix.path}"
                                   useHTML5="{Boolean}true"/>
                               <title
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textfield"
                                   fieldLabel="Title"
                                   name="./jcr:title"/>
                               <description
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textarea"
                                   fieldLabel="Description"
                                   name="./jcr:description"/>
                               <position
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
                                   fieldLabel="Text Position"
                                   name="./textPosition">
                                   <items jcr:primaryType="nt:unstructured">
                                       <left
                                           jcr:primaryType="nt:unstructured"
                                           text="Left"
                                           value="left"/>
                                       <center
                                           jcr:primaryType="nt:unstructured"
                                           text="Center"
                                           value="center"/>
                                       <right
                                           jcr:primaryType="nt:unstructured"
                                           text="Right"
                                           value="right"/>
                                   </items>
                               </position>
                               <color
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
                                   fieldLabel="Text Color"
                                   name="./textColor">
                                   <items jcr:primaryType="nt:unstructured">
                                       <light
                                           jcr:primaryType="nt:unstructured"
                                           text="Light"
                                           value="light"/>
                                       <dark
                                           jcr:primaryType="nt:unstructured"
                                           text="Dark"
                                           value="dark"/>
                                   </items>
                               </color>
                           </items>
                       </column>
                   </items>
               </image>
               <accessibility
                   jcr:primaryType="nt:unstructured"
                   sling:hideResource="{Boolean}true"/>
           </items>
       </content>
   </jcr:root>
   ```

   屬性 `sling:hideChildren`= `"[linkURL,size]`」 `items` 節點，確保 **linkURL** 和 **大小** 欄位會從對話方塊中隱藏。 僅從海報對話方塊移除這些節點是不夠的。 屬性 `sling:hideResource="{Boolean}true"` 在「協助工具」標籤上，可用來隱藏整個標籤。

   對話方塊中新增了兩個選取欄位，供作者控制標題和說明的文字位置和顏色。

   ![海報 — 最終對話結構](assets/2018-05-03_at_4_49pm.png)

   海報 — 最終對話結構

   此時， `poster` 元件可新增至 **空閒通道** 頁面（位於「We.Retail Run」專案中）: `http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`.

   ![海報對話欄位](assets/poster-dialog-full.png)

   海報對話欄位

1. 在下方建立檔案 `/apps/weretail-run/components/content/poster` 已命名 `production.html.`

   將下列項目填入檔案：

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/production.html
   
   */-->
   <div data-sly-use.image="image.js"
        data-duration="${properties.duration}"
        class="cmp-poster"
        style="background-image: url(${request.contextPath @ context='uri'}${image.src @ context='uri'});">
       <div class="cmp-poster__text
                   cmp-poster__text--${properties.textPosition @ context='attribute'}
                   cmp-poster__text--${properties.textColor @ context='attribute'}">
           <h1 class="cmp-poster__title">${properties.jcr:title}</h1>
            <h2 class="cmp-poster__description">${properties.jcr:description}</h2>
       </div>
    <img class="cmp-poster__logo" src="/content/dam/we-retail-run/logos/we-retail-run_dark.png" alt="we-retail-logo" />
   </div>
   ```

   以上是海報元件的生產標籤。 HTL指令碼覆寫 `screens/core/components/content/image/production.html`. 此 `image.js` 是伺服器端指令碼，可建立類似POJO的影像物件。 然後，可以呼叫影像物件來呈現 `src` 作為內嵌樣式背景影像。

   `The h1` 和h2標籤會根據元件屬性顯示「標題」和「說明」： `${properties.jcr:title}` 和 `${properties.jcr:description}`.

   圍繞 `h1` 和 `h2` 標籤是div包裝函式，包含三個含有「 `cmp-poster__text`」。 的值 `textPosition` 和 `textColor` 屬性可用來根據作者的對話方塊選取來變更轉譯的CSS類別。 在下一節中，會寫入用戶端程式庫的CSS，以在顯示中啟用這些變更。

   元件中也包含標誌作為覆蓋。 在此範例中，We.Retail標誌的路徑會在DAM中以硬式編碼撰寫。 根據使用案例，建立對話欄位，將標誌路徑設為動態填入的值，可能更有意義。

   另請注意，BEM（區塊元素修飾元）標籤法會與元件搭配使用。 BEM是CSS編碼慣例，可讓您更輕鬆建立可重複使用的元件。 BEM是使用的標籤法 [AEM核心元件](https://github.com/adobe/aem-core-wcm-components/wiki/CSS-coding-conventions). <!-- DEAD LINK More info can be found at: [https://getbem.com/](https://getbem.com/) -->

1. 在下方建立檔案 `/apps/weretail-run/components/content/poster` 已命名 `edit.html.`

   將下列項目填入檔案：

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/edit.html
   
   */-->
   
   <div class="aem-Screens-editWrapper ${image.cssClass} cmp-poster" data-sly-use.image="image.js" data-emptytext="${'Poster' @ i18n, locale=request.locale}">
       <img class="cmp-poster__image" src="${request.contextPath}${image.src @ context='uri'}" width="100%" />
       <div class="cmp-poster__text
              cmp-poster__text--${properties.textPosition @ context='attribute'}
          cmp-poster__text--${properties.textColor @ context='attribute'}">
         <p class="cmp-poster__title">${properties.jcr:title}</p>
         <p class="cmp-poster__description">${properties.jcr:description}</p>
       </div>
   </div>
   ```

   以上是 **編輯** 海報元件的標籤。 HTL指令碼覆寫 `/libs/screens/core/components/content/image/edit.html`. 標注類似於 `production.html` 標籤，並在影像的頂部顯示標題和說明。

   此 `aem-Screens-editWrapper`已新增，以便不會在編輯器中以全螢幕呈現元件。 此 `data-emptytext` 屬性可確保在未填入影像或內容時顯示預留位置。

## 建立用戶端程式庫 {#clientlibs}

用戶端資料庫提供組織及管理AEM實作所需CSS和JavaScript檔案的機制。 使用的詳細資訊 [您可以在此處找到用戶端程式庫。](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=en)

AEM Screens元件在編輯模式和預覽/生產模式中呈現的呈現方式不同。 系統會建立兩組用戶端程式庫，一組用於編輯模式，另一組用於預覽/生產。

1. 為海報元件的用戶端程式庫建立資料夾。

   下方 `/apps/weretail-run/components/content/poster,`建立名為 `clientlibs`.

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. 在 `clientlibs` 資料夾建立名為 `shared` 類型 `cq:ClientLibraryFolder.`

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. 將以下屬性添加到共用客戶端庫：

   * `allowProxy` | 布林值 | `true`
   * `categories` |字串[] | `cq.screens.components`

   ![/apps/weretail-run/components/content/poster/clientlibs/shared的屬性](assets/2018-05-03_at_1026pm-1.png)

   /apps/weretail-run/components/content/poster/clientlibs/shared的屬性

   此 `categories` 屬性是識別用戶端程式庫的字串。 此 `cq.screens.components` 類別會在「編輯」和「預覽/生產」模式中使用。 因此，任何在 `shared` clientlib在所有模式中都已載入。

   最佳作法是絕不直接公開任何路徑至生產環境中的/apps。 此 `allowProxy` 屬性可確保透過前置詞參考用戶端程式庫CSS和JS `/etc.clientlibs`. 有關 [可在此處找到allowProxy屬性。](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=en)

1. 建立名為 `css.txt` 共用資料夾底下。

   將下列項目填入檔案：

   ```
   #base=css
   
   styles.less
   ```

1. 建立名為 `css` 在下面 `shared` 檔案夾。 新增名為的檔案 `style.less` 在下面 `css` 檔案夾。 用戶端程式庫的結構現在應該如下所示：

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   本教學課程不會直接編寫CSS，而是使用LESS。 [較少](https://lesscss.org/) 是一種熱門的CSS預編譯器，可支援CSS變數、mixin和函式。 AEM用戶端程式庫原本支援LESS編譯。 可以使用Sass或其他預編譯器，但必須在AEM之外進行編譯。

1. 填入 `/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` 並搭配下列項目：

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less
    Poster Component - Shared Style
   */
   
   @import url('https://fonts.googleapis.com/css?family=Fjalla+One|Open+Sans:400i');
   
   @text-light-color: #fff;
   @text-dark-color: #000;
   @title-font-family: 'Fjalla One', sans-serif;
   @description-font-family: 'Open Sans', sans-serif;
   
   .cmp-poster {
   
         &__text {
         position: absolute;
         color: @text-light-color;
         top: 0;
         text-align:center;
         width: 100%;
   
         &--left {
          text-align: left;
                margin-left: 1em;
         }
   
         &--right {
          text-align: right;
                margin-right: 1em;
         }
   
         &--dark {
          color: @text-dark-color;
         }
       }
   
       &__title {
         font-weight: bold;
            font-family: @title-font-family;
            font-size: 1.2em;
       }
   
       &__description {
     font-style: italic;
           font-family: @description-font-family;
    }
   
   }
   ```

   >[!NOTE]
   >
   >GoogleWeb Fonts用於字型系列。 Web Fonts需要網際網路連接，並非所有螢幕實施都能提供可靠的連接。 針對離線模式進行規劃是部署Screens時的重要考量。

1. 複製 `shared` 客戶端庫資料夾。 貼上為同級，然後重新命名為 `production`.

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. 更新 `categories` 要設為的生產clientlibrary的屬性 `cq.screens.components.production.`

   此 `cq.screens.components.production` 類別可確保只有在預覽/生產模式中載入樣式。

   ![/apps/weretail-run/components/content/poster/clientlibs/production的屬性](assets/2018-04-30_at_5_04pm.png)

   /apps/weretail-run/components/content/poster/clientlibs/production的屬性

1. 填入 `/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` 並搭配下列項目：

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less
    Poster Component - Production Style
   */
   
   .cmp-poster {
   
       background-size: cover;
    height: 100%;
    width: 100%;
    position:absolute;
   
        &__text {
   
           top: 2em;
   
           &--left {
               width: 40%;
               top: 5em;
           }
   
           &--right {
               width: 40%;
               right: 1em;
           }
       }
   
       &__title {
     font-size: 5rem;
     font-weight: 900;
     margin: 0.1rem;
    }
   
    &__description {
     font-size: 2rem;
     margin: 0.1rem;
     font-weight: 400;
   
    }
   
       &__logo {
     position: absolute;
     max-width: 200px;
     top: 1em;
     left: 0;
    }
   
   }
   ```

   上述樣式會在畫面上的絕對位置顯示「標題」和「說明」。 標題的顯示大於說明。 元件的BEM記號可讓您輕鬆仔細檢視cmp-poster類別中的樣式。

第三個clientlibrary類別： `cq.screens.components.edit` 可用來僅將特定樣式新增至元件。

| Clientlib類別 | 使用狀況 |
|---|---|
| `cq.screens.components` | 在編輯和生產模式之間共用的樣式和指令碼 |
| `cq.screens.components.edit` | 僅用於編輯模式的樣式和指令碼 |
| `cq.screens.components.production` | 僅用於生產模式的樣式和指令碼 |

## 將海報元件新增至序列管道 {#add-sequence-channel}

海報元件用於序列頻道。 本教學課程的入門套件包含閒置通道。 預先配置空閒通道以允許組的元件 **We.Retail執行 — 內容**. 海報元件的群組設為 `We.Retail Run - Content` 和可供新增至通道。

1. 從We.Retail Run專案開啟「閒置管道」 : **`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. 拖曳+放置 **海報** 元件（從側邊列到頁面）。

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. 編輯海報元件的對話方塊以新增影像、標題、說明。 使用「文字位置」和「文字顏色」選項，確保影像上可讀取「標題/說明」。

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. 重複上述步驟以新增幾個海報元件。 在元件之間新增轉變。

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## 把它們放在一起 {#putting-it-all-together}

以下影片顯示已完成的元件，以及如何將其新增至「序列」管道。 然後，該頻道會新增至「位置」顯示畫面，並最終指派給Screens播放器。

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## 完成的程式碼 {#finished-code}

以下是教學課程中完成的程式碼。 此 **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** 和 **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** 是已編譯的AEM套件。 **SRC-screens-weretail-run-0.0.1.zip **是未編譯的原始碼，可使用Maven部署。

[取得檔案](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[取得檔案](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC最終螢幕We.Retail運行項目

[取得檔案](assets/src-screens-weretail-run-001.zip)

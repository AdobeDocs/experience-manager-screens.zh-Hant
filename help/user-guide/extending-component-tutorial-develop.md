---
title: 擴充AEM Screens元件
seo-title: 擴充AEM Screens元件
description: 以下教學課程將逐步說明如何擴充至現成可用的AEM Screens元件。 影像元件會加以擴充，以新增可授權的文字覆蓋。
seo-description: 以下教學課程將逐步說明如何擴充至現成可用的AEM Screens元件。 影像元件會加以擴充，以新增可授權的文字覆蓋。
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
translation-type: tm+mt
source-git-commit: ec8324ead3789a6cd5dde35a932c89e916709f70

---


# 擴充AEM Screens元件 {#extending-an-aem-screens-component}

以下教學課程將逐步說明如何擴充至現成可用的AEM Screens元件。 影像元件會加以擴充，以新增可授權的文字覆蓋。

## 概覽 {#overview}

本教學課程適用於剛接觸AEM Screens的開發人員。 在本教學課程中，「畫面影像」元件會加以擴充，以建立海報元件。 標題、說明和標誌會覆蓋在影像上，以在序列頻道中建立引人入勝的體驗。

>[!NOTE]
>
>在開始本教學課程之前，建議您先完成教學課程：開 [發AEM畫面的自訂元件](developing-custom-component-tutorial-develop.md)。

![自訂海報元件](assets/2018-05-07_at_4_09pm.png)

自訂海報元件是透過擴充影像元件來建立。

## 必備條件 {#prerequisites}

要完成本教學課程，需要以下內容：

1. [AEM 6.4或](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/release-notes.html)[AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html) + Latest Screens Feature Pack
1. [AEM Screens 播放器](/help/user-guide/aem-screens-introduction.md)
1. 當地開發環境

教學課程步驟和螢幕擷取是使用CRXDE-Lite來執行。 [Eclipse](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/aem-eclipse.html) 或 [IntelliJ](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/ht-intellij.html) IDE也可用來完成教學課程。 有關使用IDE與AEM進行開 [發的詳細資訊，請參閱這裡](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#eclipse-ide)。

## 專案設定 {#project-setup}

畫面專案的原始碼通常會管理為多模組Maven專案。 為加速教學課程，使用 [AEM Project Archetype 13預先產生專案](https://github.com/adobe/aem-project-archetype)。 如需有關使 [用Maven AEM Project Archetype建立專案的詳細資訊，請參閱這裡](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#maven-multimodule)。

1. 使用 **CRX套件管理下載並安裝下列套件**`http://localhost:4502/crx/packmgr/index.jsp)r:`

   [取得檔案](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [取得檔案](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **(可選** )如果使用Eclipse或其他IDE，請下載下列原始碼套件。 使用Maven命令將專案部署至本機AEM例項：

   **`mvn -PautoInstallPackage clean install`**

   SRC Start Screens We.Retail Run Project

   [取得檔案](assets/start-poster-screens-weretail-run.zip)

1. 在 **CRX包管理器中**`http://localhost:4502/crx/packmgr/index.jsp` ，安裝了以下兩個包：

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**
   ![透過CRX Package manager安裝的螢幕We.Retail執行Ui.Apps和Ui.Content套件](assets/crx-packages.png)

   透過CRX Package manager安裝的螢幕We.Retail執行Ui.Apps和Ui.Content套件

## 建立海報元件 {#poster-cmp}

Poster元件可擴充Image元件的方塊外畫面。 Sling的機制 `sling:resourceSuperType`，可用來繼承Image元件的核心功能，而不需複製和貼上。 如需有關 [Sling Request Processing基本概念的詳細資訊，請參閱這裡。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/the-basics.html#SlingRequestProcessing)

海報元件會以全螢幕呈現為預覽／製作模式。 在編輯模式中，請務必以不同的方式呈現元件，以利製作順序頻道。

1. 在下 **方的CRXDE-Lite**`http://localhost:4502/crx/de/index.jsp` （或您選擇的IDE）中， `/apps/weretail-run/components/content`建立新 `cq:Component` 的 `poster`名稱。

   將下列屬性新增至元 `poster` 件：

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

   將屬性設 `sling:resourceSuperType`定為Poster元 `screens/core/components/content/image` 件，可有效繼承Image元件的所有功能。 在元件下方可新增相 `screens/core/components/content/image` 當的節點和檔案， `poster` 以覆寫和擴充功能。

1. 將節點復 `cq:editConfig` 制到「 `/libs/screens/core/components/content/image.`貼上」 `cq:editConfig` 元件下 `/apps/weretail-run/components/content/poster` 方。

   在節點 `cq:editConfig/cq:dropTargets/image/parameters` 上，將屬 `sling:resourceType` 性更新為等於 `weretail-run/components/content/poster`。

   ![edit-config](assets/edit-config.png)

   cq:editConfig的XML表示法如下：

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

1. 將WCM Foundation對 `image` 話框複製為元件使 `poster` 用。

   從現有對話方塊開始進行修改最簡單。

   1. 從以下位置複製對話框： `/libs/wcm/foundation/components/image/cq:dialog`
   1. 將對話方塊貼在下方 `/apps/weretail-run/components/content/poster`
   ![從/libs/wcm/foundation/components/image/cq:dialog複製對話框至/apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   從/libs/wcm/foundation/components/image/cq:dialog複製對話框至/apps/weretail-run/components/content/poster

   Screens元 `image` 件會疊加至WCM Foundation元 `image` 件。 因此，組 `poster` 件繼承了兩者的功能。 海報元件的對話方塊是由「畫面」和「基礎」對話方塊的組合所組成。 **** Sling Resource Merger的功能可用來隱藏不相關的對話欄位和標籤，這些欄位是繼承自超類型元件。

1. 使用XML中表示的下 `/apps/weretail-run/components/content/poster` 列變更，更新cq:dialog:

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

   在節點 `sling:hideChildren`上使用 `"[linkURL,size]`屬性 `items` = **&quot;，以確保在對話方塊中隱藏** linkURL **** 和大小欄位。 僅從海報對話方塊移除這些節點是不夠的。 輔助功 `sling:hideResource="{Boolean}true"` 能標籤上的屬性可用來隱藏整個標籤。

   在對話方塊中新增兩個選取欄位，讓作者控制「標題」和「說明」的文字位置和顏色。

   ![海報——最終對話框結構](assets/2018-05-03_at_4_49pm.png)

   海報——最終對話框結構

   此時，可將元件的例 `poster` 項新增至We.Retail Run專案的 **Idle Channel** （閒置頻道）頁面： `http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`。

   ![海報對話欄位](assets/poster-dialog-full.png)

   海報對話欄位

1. 在名為的下方建立檔 `/apps/weretail-run/components/content/poster` 案 `production.html.`

   在檔案中填入下列項目：

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

   以上是海報元件的生產標籤。 HTL指令碼會覆寫 `screens/core/components/content/image/production.html`。 是 `image.js` 一個伺服器端指令碼，用於建立類似POJO的映像對象。 然後可以呼叫Image物件，以將 `src` 其轉換為內嵌樣式背景影像。

   `The h1` 和h2標籤會根據元件屬性顯示「標題」和「說明」: `${properties.jcr:title}` 和 `${properties.jcr:description}`。

   在和標 `h1` 簽周 `h2` 圍是div包裝函式，包含3個具有&quot; `cmp-poster__text`&quot;變數的CSS類別。 值和屬 `textPosition` 性用 `textColor` 於更改根據作者的對話框選擇呈現的CSS類。 在下一節中，會編寫用戶端程式庫的CSS，以在顯示中啟用這些變更。

   標誌也包含在元件中，當做覆蓋。 在此範例中，We.Retail標誌的路徑是硬式編碼在DAM中。 視使用案例而定，建立新對話欄位，讓標誌路徑成為動態填入的值，可能更有意義。

   另請注意，BEM（塊元素修飾詞）注釋與元件一起使用。 BEM是CSS編碼慣例，可讓您更輕鬆地建立可重複使用的元件。 BEM是 [AEM核心元件使用的符號](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions)。 如需詳細資訊，請參閱： [https://getbem.com/](https://getbem.com/)

1. 在名為的下方建立檔 `/apps/weretail-run/components/content/poster` 案 `edit.html.`

   在檔案中填入下列項目：

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

   以上是海 **報元件** 的編輯標籤。 HTL指令碼會覆寫 `/libs/screens/core/components/content/image/edit.html`。 標籤與標籤類似， `production.html` 並將在影像頂部顯示標題和說明。

   將 `aem-Screens-editWrapper`添加，以便元件不會在編輯器中呈現全屏。 該屬 `data-emptytext` 性可確保在未填入影像或內容時顯示預留位置。

## 建立用戶端程式庫 {#clientlibs}

用戶端程式庫提供組織和管理AEM實作所需CSS和JavaScript檔案的機制。 有關使用用戶 [端程式庫的詳細資訊，請參閱這裡。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html)

AEM Screens元件在「編輯」模式與「預覽／生產」模式的轉譯方式不同。 會建立兩組用戶端程式庫，一組用於編輯模式，另一組用於預覽／生產。

1. 為海報元件的用戶端程式庫建立資料夾。

   在下 `/apps/weretail-run/components/content/poster,`面建立名為的新資料夾 `clientlibs`。

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. 在資料夾 `clientlibs` 下面建立一個名為「類型」的 `shared` 新節點 `cq:ClientLibraryFolder.`

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. 將下列屬性新增至共用用戶端程式庫：

   * `allowProxy` | 布林函數 | `true`
   * `categories` |字串[] | `cq.screens.components`
   ![/apps/weretail-run/components/content/poster/clientlibs/shared的屬性](assets/2018-05-03_at_1026pm-1.png)

   /apps/weretail-run/components/content/poster/clientlibs/shared的屬性

   屬 `categories` 性是識別用戶端程式庫的字串。 類 `cq.screens.components` 別用於編輯和預覽／生產模式。 因此，在clientlib中定義的任何CSS/ `shared` JS都會以所有模式載入。

   絕對不要在生產環境中直接將任何路徑顯示至/app，這是最佳做法。 此屬 `allowProxy` 性可確保用戶端程式庫CSS和JS是透過首碼引用 `/etc.clientlibs`。 如需allowProxy屬性的 [詳細資訊，請參閱這裡。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html#main-pars_title_8ced)

1. 在共用資料夾 `css.txt` 下方建立名稱的檔案。

   在檔案中填入下列項目：

   ```
   #base=css
   
   styles.less
   ```

1. 在資料夾下建立 `css` 一個名為的 `shared` 資料夾。 在資料夾下方新 `style.less` 增名為的 `css` 檔案。 用戶端程式庫的結構現在應如下所示：

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   本教學課程不使用LESS直接編寫CSS。 [LESS](https://lesscss.org/) 是常用的CSS預編譯器，可支援CSS變數、混合和函式。 AEM用戶端程式庫本身支援LESS編譯。 Sass或其他預先編譯器可使用，但需在AEM以外進行編譯。

1. 填 `/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` 入下列：

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
   >Google網頁字型用於字型系列。 網頁字型需要網際網路連線，而並非所有螢幕建置都能提供可靠的連線。 針對離線模式進行規劃是部署螢幕時的重要考量。

1. 複製客 `shared` 戶端程式庫資料夾。 將其貼為同級，然後重新命名為 `production`。

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. 將生產 `categories` 客戶端庫的屬性更新為 `cq.screens.components.production.`

   此類 `cq.screens.components.production` 別可確保只有在預覽／生產模式下才載入樣式。

   ![/apps/weretail-run/components/content/poster/clientlibs/production的屬性](assets/2018-04-30_at_5_04pm.png)

   /apps/weretail-run/components/content/poster/clientlibs/production的屬性

1. 填 `/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` 入下列：

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

   上述樣式會在畫面上的絕對位置顯示「標題」和「說明」。 標題的顯示比說明大很多。 該元件的BEM記號使得在cmp-poster類中仔細調整樣式非常容易。

第三個clientlibrary類別：可 `cq.screens.components.edit` 以用來將「僅編輯」特定樣式添加到元件。

| Clientlib類別 | 使用狀況 |
|---|---|
| `cq.screens.components` | 在編輯和生產模式之間共用的樣式和指令碼 |
| `cq.screens.components.edit` | 僅用於編輯模式的樣式和指令碼 |
| `cq.screens.components.production` | 僅用於生產模式的樣式和指令碼 |

## 將海報元件新增至序列頻道 {#add-sequence-channel}

海報元件可用於序列頻道。 本教學課程的入門套件包含閒置頻道。 閒置頻道已預先設定為允許群組 **We.Retail Run - Content的元件**。 海報元件的群組已設為 `We.Retail Run - Content` 且可供新增至頻道。

1. 從We.Retail Run專案開啟閒置頻道： **`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. 將海報元件的新例項從頁 **面的側列拖放** 。

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. 編輯海報元件的對話方塊，以新增影像、標題、說明。 使用「文字位置」和「文字色彩」選項，確保「標題／說明」在影像上可讀。

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. 重複上述步驟以新增幾個海報元件。 在元件之間新增轉場效果。

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## 整合在一起 {#putting-it-all-together}

以下視訊顯示完成的元件，以及如何將它新增至「序列」頻道。 接著，「頻道」會新增至「位置」顯示畫面，並最終指派給「畫面」播放器。

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## 完成的程式碼 {#finished-code}

以下是教學課程中完成的程式碼。 screens-weretail-run.ui.ap **ps-0.0.1-SNAPSHOT.zip** 和 **** screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip是編譯的AEM套件。 **SRC-screens-weretail-run-0.0.1.zip **是可使用Maven部署的未編譯原始碼。

[取得檔案](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[取得檔案](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC Final Screens We.Retail Run Project

[取得檔案](assets/src-screens-weretail-run-001.zip)

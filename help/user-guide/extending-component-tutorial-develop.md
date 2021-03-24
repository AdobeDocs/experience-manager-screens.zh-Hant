---
title: 擴展AEM Screens元件
seo-title: 擴展AEM Screens元件
description: 以下教學課程將逐步介紹擴充至箱的步驟和最佳範例AEM Screens元件。 影像元件會加以擴充，以新增可授權的文字覆蓋。
seo-description: 以下教學課程將逐步介紹擴充至箱的步驟和最佳範例AEM Screens元件。 影像元件會加以擴充，以新增可授權的文字覆蓋。
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
feature: 開發螢幕
role: 開發人員
level: 中級
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '1856'
ht-degree: 2%

---


# 擴展AEM Screens元件{#extending-an-aem-screens-component}

以下教學課程將逐步介紹擴充至箱的步驟和最佳範例AEM Screens元件。 影像元件會加以擴充，以新增可授權的文字覆蓋。

## 概覽 {#overview}

本教學課程適用於剛接觸AEM Screens的開發人員。 在本教學課程中，「畫面影像」元件會加以擴充，以建立海報元件。 標題、說明和標誌會覆蓋在影像上，以在序列頻道中建立引人入勝的體驗。

>[!NOTE]
>
>在開始本教學課程之前，建議您先完成教學課程：[開發AEM Screens的自訂元件](developing-custom-component-tutorial-develop.md)。

![自訂海報元件](assets/2018-05-07_at_4_09pm.png)

自訂海報元件是透過擴充影像元件來建立。

## 必備條件 {#prerequisites}

要完成本教學課程，需要以下內容：

1. [AEMAEM6.4](https://docs.adobe.com/content/help/zh-Hant/experience-manager-64/release-notes/release-notes.html) 或 [6.3](https://helpx.adobe.com/tw/experience-manager/6-3/release-notes.html) +最新螢幕功能套件
1. [AEM Screens 播放器](/help/user-guide/aem-screens-introduction.md)
1. 本機開發環境

教學課程步驟和螢幕擷取是使用CRXDE-Lite來執行。 [您](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/aem-eclipse.html) 也可 [](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/ht-intellij.html) 以使用ElliJIDE來完成教學課程。有關使用IDE與[開發的詳細資訊，請AEM參閱此處](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#eclipse-ide)。

## 項目設定{#project-setup}

畫面專案的原始碼通常會管理為多模組Maven專案。 為加速教學課程，使用[專案原型13AEM](https://github.com/adobe/aem-project-archetype)預先產生專案。 有關使用Maven項目原型建立項目的詳細AEM資訊，請參閱](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#maven-multimodule)。[

1. 使用&#x200B;**CRX套件manage** `http://localhost:4502/crx/packmgr/index.jsp)r:`下載並安裝下列套件

   [取得檔案](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [取得檔案](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **（可選）** 如果使用Eclipse或其他IDE，請下載下面的源包。使用Maven命令將項目部AEM署到本地實例：

   **`mvn -PautoInstallPackage clean install`**

   SRC Start Screens We.Retail Run Project

   [取得檔案](assets/start-poster-screens-weretail-run.zip)

1. 在&#x200B;**CRX Package Manager** `http://localhost:4502/crx/packmgr/index.jsp`中安裝了以下兩個軟體包：

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![透過CRX Package Manager安裝的螢幕We.Retail執行Ui.Apps和Ui.Content套件](assets/crx-packages.png)

   透過CRX Package Manager安裝的螢幕We.Retail執行Ui.Apps和Ui.Content套件

## 建立海報元件{#poster-cmp}

Poster元件可擴充Image元件的方塊外畫面。 Sling的機制`sling:resourceSuperType`可用來繼承Image元件的核心功能，而不需複製和貼上。 如需[Sling Request Processing的基本資訊，請參閱這裡。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/the-basics.html#SlingRequestProcessing)

海報元件會以全螢幕呈現為預覽／製作模式。 在編輯模式中，請務必以不同的方式呈現元件，以利製作順序頻道。

1. 在&#x200B;**`poster`下方的`/apps/weretail-run/components/content`CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp`（或選擇的IDE）中，建立名為的新`cq:Component`。

   將以下屬性添加到`poster`元件：

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

   通過將`sling:resourceSuperType`屬性設定為`screens/core/components/content/image` ，海報元件有效地繼承了影像元件的所有功能。 在`screens/core/components/content/image`下方找到的對等節點和檔案可以添加到`poster`元件下方，以覆蓋和擴展功能。

1. 複製`/libs/screens/core/components/content/image.`下的`cq:editConfig`節點，將`cq:editConfig`貼上到`/apps/weretail-run/components/content/poster`元件下。

   在`cq:editConfig/cq:dropTargets/image/parameters`節點上，將`sling:resourceType`屬性更新為等於`weretail-run/components/content/poster`。

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

1. 複製WCM Foundation `image`對話框以用於`poster`元件。

   從現有對話方塊開始進行修改最簡單。

   1. 從以下位置複製對話框：`/libs/wcm/foundation/components/image/cq:dialog`
   1. 將對話框貼上到`/apps/weretail-run/components/content/poster`下面

   ![從/libs/wcm/foundation/components/image/cq:dialog複製對話框至/apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   從/libs/wcm/foundation/components/image/cq:dialog複製對話框至/apps/weretail-run/components/content/poster

   螢幕`image`元件被超級類型化到WCM Foundation `image`元件。 因此，`poster`元件繼承了兩者的功能。 海報元件的對話方塊是由「畫面」和「基礎」對話方塊的組合所組成。 **Sling Resource Merger**&#x200B;的功能可用來隱藏從超類型元件繼承的不相關對話欄位和標籤。

1. 使用XML中表示的下列變更，更新`/apps/weretail-run/components/content/poster`下方的cq:dialog::

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

   `sling:hideChildren`= `"[linkURL,size]`&quot;屬性用於`items`節點，以確保&#x200B;**linkURL**&#x200B;和&#x200B;**size**&#x200B;欄位在對話框中隱藏。 僅從海報對話方塊移除這些節點是不夠的。 協助工具標籤上的屬性`sling:hideResource="{Boolean}true"`可用來隱藏整個標籤。

   在對話方塊中新增兩個選取欄位，讓作者控制「標題」和「說明」的文字位置和顏色。

   ![海報——最終對話框結構](assets/2018-05-03_at_4_49pm.png)

   海報——最終對話框結構

   此時，`poster`元件的例項可以添加到We.Retail Run項目的&#x200B;**空閒渠道**&#x200B;頁中：`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`。

   ![海報對話欄位](assets/poster-dialog-full.png)

   海報對話欄位

1. 在`/apps/weretail-run/components/content/poster`下建立名為`production.html.`的檔案

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

   以上是海報元件的生產標籤。 HTL指令碼會覆寫`screens/core/components/content/image/production.html`。 `image.js`是一個伺服器端指令碼，用於建立類似POJO的映像對象。 然後可以調用Image對象，將`src`渲染為內嵌樣式背景影像。

   `The h1` 和h2標籤會根據元件屬性顯示「標題」和「說明」: `${properties.jcr:title}` 和 `${properties.jcr:description}`。

   `h1`和`h2`標籤周圍是div包裝函式，包含3個CSS類別，變化為&quot; `cmp-poster__text`&quot;。 `textPosition`和`textColor`屬性的值用於更改根據作者的對話框選擇呈現的CSS類。 在下一節中，會編寫用戶端程式庫的CSS，以在顯示中啟用這些變更。

   標誌也包含在元件中，當做覆蓋。 在此範例中，We.Retail標誌的路徑是硬式編碼在DAM中。 視使用案例而定，建立新對話欄位，讓標誌路徑成為動態填入的值，可能更有意義。

   另請注意，BEM（塊元素修飾詞）注釋與元件一起使用。 BEM是CSS編碼慣例，可讓您更輕鬆地建立可重複使用的元件。 BEM是[核心元件&lt;a1/AEM>使用的注釋。 ](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions)如需詳細資訊，請參閱：[https://getbem.com/](https://getbem.com/)

1. 在`/apps/weretail-run/components/content/poster`下建立名為`edit.html.`的檔案

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

   以上是海報元件的&#x200B;**edit**&#x200B;標籤。 HTL指令碼會覆寫`/libs/screens/core/components/content/image/edit.html`。 標籤與`production.html`標籤類似，將在影像頂部顯示標題和說明。

   將添加`aem-Screens-editWrapper`，使元件無法在編輯器中呈現全屏。 `data-emptytext`屬性可確保在未填入影像或內容時顯示預留位置。

## 建立客戶端庫{#clientlibs}

用戶端程式庫提供組織和管理實作所需CSS和JavaScript檔案的AEM機制。 有關使用[用戶端程式庫的詳細資訊，請參閱這裡。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html)

AEM Screens元件在編輯模式與預覽／生產模式中的呈現方式不同。 會建立兩組用戶端程式庫，一組用於編輯模式，另一組用於預覽／生產。

1. 為海報元件的用戶端程式庫建立資料夾。

   在`/apps/weretail-run/components/content/poster,`下方建立名為`clientlibs`的新資料夾。

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. 在`clientlibs`資料夾下，建立一個名為`shared`的新節點，該節點類型為`cq:ClientLibraryFolder.`

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. 將下列屬性新增至共用用戶端程式庫：

   * `allowProxy` | 布林函數 | `true`
   * `categories` |字串[] |  `cq.screens.components`

   ![/apps/weretail-run/components/content/poster/clientlibs/shared的屬性](assets/2018-05-03_at_1026pm-1.png)

   /apps/weretail-run/components/content/poster/clientlibs/shared的屬性

   `categories`屬性是識別客戶端庫的字串。 `cq.screens.components`類別在「編輯」和「預覽／生產」模式中都使用。 因此，在`shared` clientlib中定義的任何CSS/JS都會以所有模式載入。

   絕對不要在生產環境中直接將任何路徑顯示至/app，這是最佳做法。 `allowProxy`屬性可確保用戶端程式庫CSS和JS是透過`/etc.clientlibs`的首碼來參考。 有關[allowProxy屬性的更多資訊，請參閱這裡。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html#main-pars_title_8ced)

1. 在共用資料夾下方建立名為`css.txt`的檔案。

   在檔案中填入下列項目：

   ```
   #base=css
   
   styles.less
   ```

1. 在`shared`資料夾下建立名為`css`的資料夾。 在`css`資料夾下添加名為`style.less`的檔案。 用戶端程式庫的結構現在應如下所示：

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   本教學課程不使用LESS直接編寫CSS。 [LESS](https://lesscss.org/) 是常用的CSS預編譯器，可支援CSS變數、混合和函式。用戶AEM端程式庫本身支援LESS編譯。 Sass或其他預編譯器可使用，但需在外部進行編譯AEM。

1. 將`/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less`填入以下內容：

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

1. 複製`shared`客戶端庫資料夾。 將其貼為同級，然後將其重新命名為`production`。

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. 將生產客戶端庫的`categories`屬性更新為`cq.screens.components.production.`

   `cq.screens.components.production`類別可確保只有在「預覽／生產」模式下才載入樣式。

   ![/apps/weretail-run/components/content/poster/clientlibs/production的屬性](assets/2018-04-30_at_5_04pm.png)

   /apps/weretail-run/components/content/poster/clientlibs/production的屬性

1. 將`/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less`填入以下內容：

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

第三個clientlibrary類別：`cq.screens.components.edit`可用於將「僅編輯」特定樣式添加到元件。

| Clientlib類別 | 使用狀況 |
|---|---|
| `cq.screens.components` | 在編輯和生產模式之間共用的樣式和指令碼 |
| `cq.screens.components.edit` | 僅用於編輯模式的樣式和指令碼 |
| `cq.screens.components.production` | 僅用於生產模式的樣式和指令碼 |

## 將海報元件新增至序列頻道{#add-sequence-channel}

海報元件可用於序列頻道。 本教學課程的入門套件包含閒置頻道。 空閒頻道已預先設定為允許群組&#x200B;**We.Retail Run - Content**&#x200B;的元件。 海報元件的群組設為`We.Retail Run - Content`，可供新增至頻道。

1. 從We.Retail Run專案開啟閒置頻道：**`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. 將&#x200B;**Poster**&#x200B;元件的新例項從頁面的側列拖放至頁面。

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. 編輯海報元件的對話方塊，以新增影像、標題、說明。 使用「文字位置」和「文字色彩」選項，確保「標題／說明」在影像上可讀。

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. 重複上述步驟以新增幾個海報元件。 在元件之間新增轉場效果。

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## 將所有內容整合在一起{#putting-it-all-together}

以下視訊顯示完成的元件，以及如何將它新增至「序列」頻道。 接著，「頻道」會新增至「位置」顯示畫面，並最終指派給「畫面」播放器。

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## 完成代碼{#finished-code}

以下是教學課程中完成的程式碼。 **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**&#x200B;和&#x200B;**screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**&#x200B;是編譯的包AEM。 **SRC-screens-weretail-run-0.0.1.zip **是可使用Maven部署的未編譯原始碼。

[取得檔案](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[取得檔案](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC Final Screens We.Retail Run Project

[取得檔案](assets/src-screens-weretail-run-001.zip)

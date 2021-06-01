---
title: 擴充AEM Screens元件
seo-title: 擴充AEM Screens元件
description: 下列教學課程將逐步說明擴充現成可用AEM Screens元件的步驟和最佳作法。 擴充影像元件以新增可授權的文字覆蓋。
seo-description: 下列教學課程將逐步說明擴充現成可用AEM Screens元件的步驟和最佳作法。 擴充影像元件以新增可授權的文字覆蓋。
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
feature: 開發螢幕
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1854'
ht-degree: 2%

---


# 擴充AEM Screens元件{#extending-an-aem-screens-component}

下列教學課程將逐步說明擴充現成可用AEM Screens元件的步驟和最佳作法。 擴充影像元件以新增可授權的文字覆蓋。

## 概覽 {#overview}

本教學課程適用於剛接觸AEM Screens的開發人員。 在本教學課程中，會擴充Screens影像元件，以建立海報元件。 標題、說明和標誌覆蓋在影像上，以在序列頻道中建立引人入勝的體驗。

>[!NOTE]
>
>開始本教學課程之前，建議您先完成本教學課程：[開發AEM Screens的自訂元件](developing-custom-component-tutorial-develop.md)。

![自訂海報元件](assets/2018-05-07_at_4_09pm.png)

自訂海報元件是透過擴充影像元件來建立。

## 必備條件 {#prerequisites}

若要完成本教學課程，需要執行下列操作：

1. [AEM 6.4](https://docs.adobe.com/content/help/zh-Hant/experience-manager-64/release-notes/release-notes.html) 或 [AEM 6.3](https://helpx.adobe.com/tw/experience-manager/6-3/release-notes.html) + Latest Screens Feature Pack
1. [AEM Screens 播放器](/help/user-guide/aem-screens-introduction.md)
1. 本機開發環境

教學課程步驟和螢幕擷取畫面是使用CRXDE-Lite執行。 [](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/aem-eclipse.html) ElliJIDE也 [](https://docs.adobe.com/content/help/en/experience-manager-64/developing/devtools/ht-intellij.html) 可用來完成本教學課程。有關使用IDE來[使用AEM開發的詳細資訊，請參閱此處](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#eclipse-ide)。

## 項目設定{#project-setup}

Screens專案的原始碼通常以多模組Maven專案的形式管理。 為了加速教學課程，已使用[AEM專案原型13](https://github.com/adobe/aem-project-archetype)預先產生專案。 有關使用Maven AEM專案原型建立專案的[詳細資訊，請參閱此處](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/project-setup.html#maven-multimodule)。

1. 使用&#x200B;**CRX套件manage** `http://localhost:4502/crx/packmgr/index.jsp)r:`下載並安裝下列套件

[取得檔案](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [取得檔案](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **（可選）** 如果使用Eclipse或其他IDE，請下載下列來源套件。使用Maven命令將專案部署至本機AEM執行個體：

   **`mvn -PautoInstallPackage clean install`**

   SRC啟動螢幕We.Retail運行項目

[取得檔案](assets/start-poster-screens-weretail-run.zip)

1. 在&#x200B;**CRX Package Manager** `http://localhost:4502/crx/packmgr/index.jsp`中安裝了以下兩個軟體包：

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![透過CRX套件管理器安裝的Screens We.Retail執行Ui.Apps和Ui.Content套件](assets/crx-packages.png)

   透過CRX套件管理器安裝的Screens We.Retail執行Ui.Apps和Ui.Content套件

## 建立海報元件{#poster-cmp}

海報元件會擴展出現的螢幕影像元件。 Sling的機制`sling:resourceSuperType`可繼承影像元件的核心功能，而無須複製並貼上。 如需[Sling請求處理基本資訊，請前往此處。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/the-basics.html#SlingRequestProcessing)

海報元件會以全螢幕預覽/生產模式轉譯。 在編輯模式中，請務必以不同方式轉譯元件，以方便編寫序列管道。

1. 在&#x200B;**CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp`（或選擇的IDE）中，在`/apps/weretail-run/components/content`下建立名為`poster`的新`cq:Component`。

   將以下屬性添加到`poster`元件中：

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

   通過將`sling:resourceSuperType`屬性設定為等於`screens/core/components/content/image` ，海報元件有效地繼承了影像元件的所有功能。 在`screens/core/components/content/image`下可以添加等效節點和檔案到`poster`元件下，以覆蓋和擴展功能。

1. 複製`/libs/screens/core/components/content/image.`下的`cq:editConfig`節點，在`/apps/weretail-run/components/content/poster`元件下貼上`cq:editConfig`。

   在`cq:editConfig/cq:dropTargets/image/parameters`節點上，將`sling:resourceType`屬性更新為等於`weretail-run/components/content/poster`。

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

1. 複製要用於`poster`元件的WCM Foundation `image`對話框。

   最簡單的方式是從現有對話方塊開始，然後進行修改。

   1. 從以下位置複製對話框：`/libs/wcm/foundation/components/image/cq:dialog`
   1. 在`/apps/weretail-run/components/content/poster`下方貼上對話方塊

   ![從/libs/wcm/foundation/components/image/cq:dialog複製到/apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   從/libs/wcm/foundation/components/image/cq:dialog複製到/apps/weretail-run/components/content/poster

   Screens `image`元件被超類為WCM Foundation `image`元件。 因此，`poster`元件會從兩者繼承功能。 海報元件的對話方塊由Screens和Foundation對話方塊的組合組成。 **Sling Resource Merger**&#x200B;的功能可用來隱藏從超類型元件繼承的無關對話欄位和索引標籤。

1. 使用以下XML表示的變更，更新`/apps/weretail-run/components/content/poster`下方的cq:dialog :

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

   `sling:hideChildren`= `"[linkURL,size]`&quot;屬性用於`items`節點，以確保在對話方塊中隱藏&#x200B;**linkURL**&#x200B;和&#x200B;**大小**&#x200B;欄位。 僅從海報對話方塊移除這些節點是不夠的。 輔助工具頁簽上的屬性`sling:hideResource="{Boolean}true"`用於隱藏整個頁簽。

   對話方塊中新增了兩個選取欄位，供作者控制標題和說明的文字位置和顏色。

   ![海報 — 最終對話結構](assets/2018-05-03_at_4_49pm.png)

   海報 — 最終對話結構

   此時，可將`poster`元件的實例添加到We.Retail運行項目的&#x200B;**空閒通道**&#x200B;頁中：`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`。

   ![海報對話欄位](assets/poster-dialog-full.png)

   海報對話欄位

1. 在`/apps/weretail-run/components/content/poster`下建立名為`production.html.`的檔案

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

   以上是海報元件的生產標籤。 HTL指令碼會覆寫`screens/core/components/content/image/production.html`。 `image.js`是伺服器端指令碼，會建立類似POJO的影像物件。 然後，可以調用Image對象，將`src`渲染為內嵌樣式background-image。

   `The h1` 和h2標籤會根據元件屬性顯示「標題」和「說明」： `${properties.jcr:title}` 和 `${properties.jcr:description}`。

   `h1`和`h2`標籤周圍是含有三個CSS類別（變數為「 `cmp-poster__text`」）的div包裝函式。 `textPosition`和`textColor`屬性的值用於根據作者的對話方塊選取來變更呈現的CSS類別。 在下一節中，會寫入用戶端程式庫的CSS，以在顯示中啟用這些變更。

   元件中也包含標誌作為覆蓋。 在此範例中，We.Retail標誌的路徑會在DAM中以硬式編碼撰寫。 視使用案例而定，建立新的對話方塊欄位，將標誌路徑設為動態填入的值，可能更有意義。

   另請注意，BEM（區塊元素修飾元）標籤法會與元件搭配使用。 BEM是CSS編碼慣例，可讓您更輕鬆建立可重複使用的元件。 BEM是[AEM核心元件](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions)使用的記號。 如需詳細資訊，請參閱：[https://getbem.com/](https://getbem.com/)

1. 在`/apps/weretail-run/components/content/poster`下建立名為`edit.html.`的檔案

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

   以上是海報元件的&#x200B;**edit**&#x200B;標籤。 HTL指令碼會覆寫`/libs/screens/core/components/content/image/edit.html`。 標籤類似於`production.html`標籤，並將在影像上方顯示標題和說明。

   已新增`aem-Screens-editWrapper`，讓元件不會在編輯器中呈現全螢幕。 `data-emptytext`屬性可確保在未填入影像或內容時顯示預留位置。

## 建立用戶端程式庫 {#clientlibs}

用戶端資料庫提供組織及管理AEM實作所需CSS和JavaScript檔案的機制。 有關使用[客戶端庫的更多資訊，請參見此處。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html)

AEM Screens元件在編輯模式和預覽/生產模式中呈現的呈現方式不同。 系統會建立兩組用戶端程式庫，一組用於編輯模式，另一組用於預覽/生產。

1. 為海報元件的用戶端程式庫建立資料夾。

   在`/apps/weretail-run/components/content/poster,`下方建立名為`clientlibs`的新資料夾。

   ![2018-05-03_at_1008pm](assets/2018-05-03_at_1008pm.png)

1. 在`clientlibs`資料夾下面建立一個名為`shared`的`cq:ClientLibraryFolder.`類型的新節點

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. 將以下屬性添加到共用客戶端庫：

   * `allowProxy` | 布林函數 | `true`
   * `categories` |字串[] |  `cq.screens.components`

   ![/apps/weretail-run/components/content/poster/clientlibs/shared的屬性](assets/2018-05-03_at_1026pm-1.png)

   /apps/weretail-run/components/content/poster/clientlibs/shared的屬性

   `categories`屬性是標識客戶端庫的字串。 `cq.screens.components`類別在「編輯」和「預覽/生產」模式中均使用。 因此，在`shared` clientlib中定義的任何CSS/JS都會以所有模式載入。

   最佳作法是絕不直接公開任何路徑至生產環境中的/apps。 `allowProxy`屬性可確保透過`/etc.clientlibs`前置詞參考用戶端程式庫CSS和JS。 有關[allowProxy屬性的更多資訊，請參見此處。](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html#main-pars_title_8ced)

1. 在共用資料夾下建立名為`css.txt`的檔案。

   將下列項目填入檔案：

   ```
   #base=css
   
   styles.less
   ```

1. 在`shared`資料夾下方建立名為`css`的資料夾。 在`css`資料夾下方新增名為`style.less`的檔案。 用戶端程式庫的結構現在應該如下所示：

   ![2018-05-03_at_1057pm](assets/2018-05-03_at_1057pm.png)

   本教學課程不會直接編寫CSS，而是使用LESS。 [](https://lesscss.org/) LESS是一種熱門的CSS預編譯器，支援CSS變數、mixin和函式。AEM用戶端程式庫原本支援LESS編譯。 可以使用Sas或其他預編譯器，但需要在AEM之外進行編譯。

1. 將以下內容填入`/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less`:

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
   >Google網頁字型用於字型系列。 Web字型需要網際網路連接，並非所有螢幕實施都能提供可靠的連接。 針對離線模式進行規劃是部署Screens時的重要考量。

1. 複製`shared`客戶端庫資料夾。 貼上為同級，然後將其重新命名為`production`。

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. 將生產clientlibrary的`categories`屬性更新為`cq.screens.components.production.`

   `cq.screens.components.production`類別可確保只有在預覽/生產模式下才載入樣式。

   ![/apps/weretail-run/components/content/poster/clientlibs/production的屬性](assets/2018-04-30_at_5_04pm.png)

   /apps/weretail-run/components/content/poster/clientlibs/production的屬性

1. 將以下內容填入`/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less`:

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

   上述樣式會在畫面上的絕對位置顯示「標題」和「說明」。 標題的顯示會比說明大很多。 元件的BEM記號可讓您輕鬆仔細檢視cmp-poster類別中的樣式。

第三個clientlibrary類別：`cq.screens.components.edit`可用來僅將特定樣式新增至元件。

| Clientlib類別 | 使用狀況 |
|---|---|
| `cq.screens.components` | 在編輯和生產模式之間共用的樣式和指令碼 |
| `cq.screens.components.edit` | 僅用於編輯模式的樣式和指令碼 |
| `cq.screens.components.production` | 僅用於生產模式的樣式和指令碼 |

## 將海報元件添加到序列通道{#add-sequence-channel}

海報元件可用於序列頻道。 本教學課程的入門套件包含閒置通道。 空閒通道已預先配置為允許組&#x200B;**We.Retail運行 — 內容**&#x200B;的元件。 海報元件的群組設為`We.Retail Run - Content`，可新增至通道。

1. 從We.Retail Run專案開啟「閒置管道」 :**`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. 將&#x200B;**Poster**&#x200B;元件的新例項從側欄拖曳至頁面。

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. 編輯海報元件的對話方塊以新增影像、標題、說明。 使用「文字位置」和「文字顏色」選項，確保影像上可讀取「標題/說明」。

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. 重複上述步驟以新增幾個海報元件。 在元件之間新增轉變。

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## 將所有內容放在一起{#putting-it-all-together}

以下影片顯示已完成的元件，以及如何將其新增至「序列」管道。 然後，該頻道會新增至「位置」顯示畫面，並最終指派給Screens播放器。

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## 已完成代碼{#finished-code}

以下是教學課程中完成的程式碼。 **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**&#x200B;和&#x200B;**screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**&#x200B;是已編譯的AEM套件。 **SRC-screens-weretail-run-0.0.1.zip **是未編譯的原始碼，可使用Maven部署。

[取得檔案](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[取得檔案](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC最終螢幕We.Retail運行項目

[取得檔案](assets/src-screens-weretail-run-001.zip)

---
title: 擴展AEM Screens元件
seo-title: Extending an AEM Screens Component
description: 以下教程將介紹擴展開箱後AEM Screens元件的步驟和最佳做法。 擴展「影像」元件以添加可授權的文本覆蓋。
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
source-git-commit: 29116a15d5486b2c446cae0d092c4d4b802fe9e7
workflow-type: tm+mt
source-wordcount: '1771'
ht-degree: 2%

---

# 擴展AEM Screens元件 {#extending-an-aem-screens-component}

以下教程將介紹擴展開箱後AEM Screens元件的步驟和最佳做法。 擴展「影像」元件以添加可授權的文本覆蓋。

## 概觀 {#overview}

本教程適用於對AEM Screens不熟悉的開發人員。 在本教程中，螢幕影像元件將擴展為建立海報元件。 標題、描述和徽標疊加在影像上，以在序列通道中建立引人入勝的體驗。

>[!NOTE]
>
>在啟動本教程之前，建議您完成本教程： [為AEM Screens開發定制元件](developing-custom-component-tutorial-develop.md)。

![自定義海報元件](assets/2018-05-07_at_4_09pm.png)

自定義海報元件是通過擴展影像元件建立的。

## 必備條件 {#prerequisites}

要完成本教程，您需要執行以下操作：

1. AEM 6.5 +最新螢幕功能包
1. [AEM Screens 播放器](/help/user-guide/aem-screens-introduction.md)
1. 本機開發環境

教程步驟和螢幕抓圖是使用CRXDE-Lite執行的。 [日蝕](https://experienceleague.adobe.com/docs/experience-manager-65/developing/devtools/aem-eclipse.html) 或 [智慧J](https://experienceleague.adobe.com/docs/experience-manager-65/developing/devtools/ht-intellij.html) IDE也可用於完成本教程。 有關使用IDE的詳細資訊 [可AEM以找到](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup.html)。

## 專案設定 {#project-setup}

螢幕項目的原始碼通常作為多模組Maven項目進行管理。 為加快教程的完成，預生成的項目 [原型AEM13工程](https://github.com/adobe/aem-project-archetype)。 有關 [在此處可找到使用Maven項AEM目原型建立項目](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup.html)。

1. 使用 **CRX包管理** `http://localhost:4502/crx/packmgr/index.jsp)r:`

[取得檔案](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [取得檔案](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **（可選）** 如果使用Eclipse或其他IDE，請下載以下源包。 使用Maven命令將項AEM目部署到本地實例：

   **`mvn -PautoInstallPackage clean install`**

   SRC啟動螢幕We.Retail運行項目

[取得檔案](assets/start-poster-screens-weretail-run.zip)

1. 在 **CRX包管理器** `http://localhost:4502/crx/packmgr/index.jsp` 安裝了以下兩個軟體包：

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![通過CRX包管理器安裝的We.Retail運行Ui.Apps和Ui.Content包的螢幕](assets/crx-packages.png)

   通過CRX包管理器安裝的We.Retail運行Ui.Apps和Ui.Content包的螢幕

## 建立海報元件 {#poster-cmp}

Poster元件將框外的Image元件延伸。 一種吊具， `sling:resourceSuperType`，用於繼承映像元件的核心功能，而無需複製和貼上。 有關Web服務的基本資訊 [Sling Request Processing可在此處找到。](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/the-basics.html)

海報元件以預覽/生產模式以全屏顯示。 在編輯模式下，為了便於編寫序列通道，必須以不同方式呈現元件。

1. 在 **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` （或選擇的IDE） `/apps/weretail-run/components/content`建立 `cq:Component` 命名 `poster`。

   將以下屬性添加到 `poster` 元件：

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

   通過設定 `sling:resourceSuperType`等於 `screens/core/components/content/image` 海報元件有效地繼承了影像元件的所有功能。 下面找到的對等節點和檔案 `screens/core/components/content/image` 可以添加到 `poster` 以覆蓋和擴展功能。

1. 複製 `cq:editConfig` 節點 `/libs/screens/core/components/content/image.`貼上 `cq:editConfig` 在下面 `/apps/weretail-run/components/content/poster` 元件。

   在 `cq:editConfig/cq:dropTargets/image/parameters` 節點更新 `sling:resourceType` 屬性等於 `weretail-run/components/content/poster`。

   ![編輯 — 配置](assets/edit-config.png)

   cq:editConfig的XML表示形式如下所示：

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

1. 複製WCM基礎 `image` 對話框 `poster` 元件。

   從現有對話框開始，然後進行修改是最容易的。

   1. 從以下位置複製對話框： `/libs/wcm/foundation/components/image/cq:dialog`
   1. 將對話框貼上到下面 `/apps/weretail-run/components/content/poster`

   ![從/libs/wcm/foundation/components/image/cq:dialog複製到/apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   從/libs/wcm/foundation/components/image/cq:dialog複製到/apps/weretail-run/components/content/poster

   螢幕 `image` 元件是超類型到WCM Foundation `image` 元件。 因此 `poster` 元件繼承兩者的功能。 海報元件的對話框由螢幕和基礎對話框的組合組成。 的功能 **Sling資源合併** 用於隱藏從超類型元件繼承的無關對話框欄位和頁籤。

1. 更新下面的cq：對話框 `/apps/weretail-run/components/content/poster` 以下更改在XML中表示：

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

   屬性 `sling:hideChildren`= `"[linkURL,size]`「 」用於 `items` 節點以確保 **連結URL** 和 **大小** 對話框中隱藏了欄位。 僅從海報對話框中刪除這些節點是不夠的。 屬性 `sling:hideResource="{Boolean}true"` 「輔助功能」(accessibility)頁籤上的「隱藏」(inthe)頁籤。

   在對話框中添加兩個選擇欄位，使作者能夠控制「標題」和「說明」的文本位置和顏色。

   ![發信人 — 最終對話框結構](assets/2018-05-03_at_4_49pm.png)

   發信人 — 最終對話框結構

   此時， `poster` 可將元件添加到 **空閒通道** 頁面： `http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`。

   ![海報對話框欄位](assets/poster-dialog-full.png)

   海報對話框欄位

1. 在下面建立檔案 `/apps/weretail-run/components/content/poster` 命名 `production.html.`

   使用以下內容填充檔案：

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

   上面是海報元件的生產標籤。 HTL指令碼將覆蓋 `screens/core/components/content/image/production.html`。 的 `image.js` 是建立類似POJO的映像對象的伺服器端指令碼。 然後，可以調用Image對象來呈現 `src` 作為內嵌樣式背景影像。

   `The h1` 添加h2標籤時，將根據元件屬性顯示「標題」和「說明」： `${properties.jcr:title}` 和 `${properties.jcr:description}`。

   圍繞 `h1` 和 `h2` 標籤是包含三個CSS類的div包裝，變體為「」 `cmp-poster__text`。 的值 `textPosition` 和 `textColor` 屬性用於根據作者的對話框選擇更改呈現的CSS類。 在下一節中，將編寫客戶端庫的CSS，以在顯示中啟用這些更改。

   該元件中還包括標識作為覆蓋。 在本示例中，We.Retail徽標的路徑在DAM中是硬編碼的。 根據使用情形，建立對話框欄位以使徽標路徑成為動態填充值可能更有意義。

   另請注意，BEM（塊元素修飾符）表示法與元件一起使用。 BEM是一種CSS編碼約定，它使建立可重用元件變得更容易。 BEM是由 [核AEM心元件](https://github.com/adobe/aem-core-wcm-components/wiki/CSS-coding-conventions)。 <!-- DEAD LINK More info can be found at: [https://getbem.com/](https://getbem.com/) -->

1. 在下面建立檔案 `/apps/weretail-run/components/content/poster` 命名 `edit.html.`

   使用以下內容填充檔案：

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

   以上是 **編輯** 標籤。 HTL指令碼將覆蓋 `/libs/screens/core/components/content/image/edit.html`。 標籤與 `production.html` 標籤，並在影像頂部顯示標題和說明。

   的 `aem-Screens-editWrapper`添加，以便在編輯器中不呈現全屏。 的 `data-emptytext` 屬性確保在未填充影像或內容時顯示佔位符。

## 建立客戶端庫 {#clientlibs}

客戶端庫提供一種機制，用於組織和管理實現所需的CSS和JavaScriptAEM檔案。 有關使用的詳細資訊 [客戶端庫可在此處找到。](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=en)

AEM Screens元件在「編輯」模式與「預覽/生產」模式下的呈現方式不同。 建立兩組客戶端庫，一組用於「編輯」模式，另一組用於「預覽/生產」。

1. 為Poster元件的客戶端庫建立資料夾。

   在下面 `/apps/weretail-run/components/content/poster,`建立名為 `clientlibs`。

   ![2018-05-03_at_1008下午](assets/2018-05-03_at_1008pm.png)

1. 在 `clientlibs` 資料夾建立名為 `shared` 類型 `cq:ClientLibraryFolder.`

   ![2018-05-03_at_1011pm](assets/2018-05-03_at_1011pm.png)

1. 將以下屬性添加到共用客戶端庫：

   * `allowProxy` | 布林值 | `true`
   * `categories` | 字串[] | `cq.screens.components`

   ![/apps/weretail-run/components/content/poster/clientlibs/shared的屬性](assets/2018-05-03_at_1026pm-1.png)

   /apps/weretail-run/components/content/poster/clientlibs/shared的屬性

   的 `categories` 屬性是標識客戶端庫的字串。 的 `cq.screens.components` 類別在「編輯」和「預覽/生產」模式下使用。 因此，在 `shared` 客戶機庫在所有模式下都載入。

   絕不直接向生產環境中的/app顯示任何路徑是最佳做法。 的 `allowProxy` 屬性確保客戶端庫CSS和JS通過前置詞引用 `/etc.clientlibs`。 有關 [allowProxy屬性可在此處找到。](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=en)

1. 建立名為 `css.txt` 下。

   使用以下內容填充檔案：

   ```
   #base=css
   
   styles.less
   ```

1. 建立名為 `css` 在下面 `shared` 的子菜單。 添加名為 `style.less` 在下面 `css` 的子菜單。 客戶端庫的結構現在應如下所示：

   ![2018-05-03_at_1057下午](assets/2018-05-03_at_1057pm.png)

   本教程不直接編寫CSS，而是使用LESS。 [減](https://lesscss.org/) 是支援CSS變數、混合和函式的常用CSS預編譯器。 客AEM戶端庫本機支援LESS編譯。 可以使用Sass或其他預編譯器，但必須在外部編譯AEM。

1. 填充 `/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` 下面列出：

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
   >GoogleWeb Fonts用於字型系列。 Web Fonts需要網際網路連接，並且並非所有螢幕實現都能可靠連接。 計畫離線模式是螢幕部署的重要考慮因素。

1. 複製 `shared` 客戶端庫資料夾。 將其貼上為同級，然後將其更名為 `production`。

   ![2018-05-03_at_1114pm](assets/2018-05-03_at_1114pm.png)

1. 更新 `categories` 要生產的客戶端庫的屬性 `cq.screens.components.production.`

   的 `cq.screens.components.production` 類別確保只有在「預覽/生產」模式下才載入樣式。

   ![/apps/weretail-run/components/content/poster/clientlibs/production的屬性](assets/2018-04-30_at_5_04pm.png)

   /apps/weretail-run/components/content/poster/clientlibs/production的屬性

1. 填充 `/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` 下面列出：

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

   上述樣式在螢幕上的絕對位置顯示「標題」和「說明」。 標題顯示得比說明大。 該元件的BEM表示法使得可以輕鬆地仔細地確定cmp-poster類中的樣式。

第三個客戶端庫類別： `cq.screens.components.edit` 可用於將「僅編輯」特定樣式添加到元件。

| 客戶端庫類別 | 使用狀況 |
|---|---|
| `cq.screens.components` | 在編輯和生產模式之間共用的樣式和指令碼 |
| `cq.screens.components.edit` | 僅在編輯模式中使用的樣式和指令碼 |
| `cq.screens.components.production` | 僅在生產模式中使用的樣式和指令碼 |

## 將海報元件添加到序列通道 {#add-sequence-channel}

海報元件用於序列通道。 本教程的啟動程式包包括空閒通道。 空閒通道已預配置為允許組的元件 **We.Retail Run — 內容**。 Poster元件的組設定為 `We.Retail Run - Content` 可添加到頻道。

1. 從We.Retail Run項目開啟空閒通道： **`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. 拖動+拖放新實例 **海報** 從側面欄到頁面。

   ![2018-05-07_at_3_23pm](assets/2018-05-07_at_3_23pm.png)

1. 編輯海報元件的對話框以添加影像、標題、說明。 使用「文本位置」和「文本顏色」選項，確保「標題/說明」可通過影像讀取。

   ![2018-05-07_at_3_25pm](assets/2018-05-07_at_3_25pm.png)

1. 重複上述步驟以添加幾個海報元件。 在元件之間添加過渡。

   ![2018-05-07_at_3_28pm](assets/2018-05-07_at_3_28pm.png)

## 把它們放在一起 {#putting-it-all-together}

以下視頻顯示了已完成的元件以及如何將其添加到序列通道。 然後，該頻道被添加到位置顯示器，並最終被分配給螢幕播放器。

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9)

## 已完成代碼 {#finished-code}

下面是本教程的完成代碼。 的 **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** 和 **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** 是已編譯的AEM包。 **SRC-screens-weretail-run-0.0.1.zip **是可使用Maven部署的未編譯的原始碼。

[取得檔案](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[取得檔案](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

SRC最終螢幕我們零售運行項目

[取得檔案](assets/src-screens-weretail-run-001.zip)

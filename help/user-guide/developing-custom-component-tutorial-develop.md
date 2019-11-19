---
title: 開發AEM畫面的自訂元件
seo-title: 開發AEM畫面的自訂元件
description: 下列教學課程將逐步說明為AEM Screens建立自訂元件的步驟。 AEM Screens會重複使用其他AEM產品的許多現有設計樣式和技術。 本教學課程強調針對AEM Screens進行開發時的差異和特殊考量。
seo-description: 為AEM Screens建立簡單「Hello World」元件的入門教學課程。 AEM Screens會重複使用其他AEM產品的許多現有設計樣式和技術。 以下教學課程旨在強調針對AEM Screens進行開發時的特定差異和考量。
uuid: 8ec8be5a-6348-48f2-9cb7-75b2bad555a6
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 24eb937f-ab51-4883-8236-8ebe6243f6e3
targetaudience: target-audience new
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 開發AEM畫面的自訂元件 {#developing-a-custom-component-for-aem-screens}

下列教學課程將逐步說明為AEM Screens建立自訂元件的步驟。 AEM Screens會重複使用其他AEM產品的許多現有設計樣式和技術。 本教學課程強調針對AEM Screens進行開發時的差異和特殊考量。

## 概覽 {#overview}

本教學課程適用於剛接觸AEM Screens的開發人員。 在本教學課程中，AEM Screens中為「序列」頻道建立簡單的「Hello World」元件。 對話方塊可讓作者更新顯示的文字。

![超視低音](assets/overviewhellow.png)

## 必備條件 {#prerequisites}

要完成本教學課程，需要以下內容：

1. [AEM 6.5或](https://helpx.adobe.com/experience-manager/6-4/release-notes.html)[AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html) + Latest Screens Feature Pack

1. [AEM Screens 播放器](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-screens-introduction.html)
1. 當地開發環境

教學課程步驟和螢幕擷取是使 **用CRXDE-Lite來執行**。 IDE也可用於完成教學課程。 有關使用IDE與AEM進行開發的 [詳細資訊，請參閱這裡。](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html#eclipse-ide)


## 專案設定 {#project-setup}

畫面專案的原始碼通常會管理為多模組Maven專案。 為加速教學課程，使用 [AEM Project Archetype 13預先產生專案](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)。 如需有關使 [用Maven AEM Project Archetype建立專案的詳細資訊，請參閱這裡](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html#maven-multimodule)。

1. 使用 [CRX套件管理器下載並安裝下列套件](http://localhost:4502/crx/packmgr/index.jsp):

   [取得檔案](assets/base-screens-weretail-runuiapps-001-snapshot.zip)

   [取得檔案](assets/base-screens-weretail-runuicontent-001-snapshot.zip)
   **(可選** )如果使用Eclipse或其他IDE，請下載以下源包。 使用Maven命令將專案部署至本機AEM例項：

   **`mvn -PautoInstallPackage clean install`**

   開始HelloWorld SRC螢幕We.Retail運行項目

   [取得檔案](assets/src-screens-weretail-run.zip)

1. 在 [CRX包管理器中](http://localhost:4502/crx/packmgr/index.jsp) ，驗證是否安裝了以下兩個包：

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**
   ![透過CRX Package manager安裝的螢幕We.Retail執行Ui.Apps和Ui.Content套件](assets/crx-packages.png)

   透過CRX Package manager安裝的螢幕We.Retail執行Ui.Apps和Ui.Content套件

1. screens-weretail-run.ui.apps **套件** ，會在下方安裝程式碼 `/apps/weretail-run`。

   此套件包含負責為專案產生自訂元件的程式碼。 此套件包含元件程式碼和所需的任何JavaScript或CSS。 此套件也 **內嵌screens-weretail-run.core-0.0.1-SNAPSHOT.jar** ，其中包含專案所需的任何Java程式碼。

   >[!NOTE]
   >
   >在本教學課程中，不編寫Java程式碼。 如果需要更複雜的商業邏輯，可使用核心Java套件來建立和部署後端Java。

   ![在CRXDE Lite中呈現ui.apps程式碼](assets/uipps-contents.png)

   在CRXDE Lite中呈現ui.apps程式碼

   helloworld **元件** 目前只是預留位置。 在本教學課程中，將會新增功能，讓作者更新元件顯示的訊息。

1. screens-weretail-run.ui.content **套件** ，會在下列位置安裝程式碼：

   * `/conf/we-retail-run`
   * `/content/dam/we-retail-run`
   * `/content/screens/we-retail-run`
   此套件包含專案所需的開始內容和設定結構。 **`/conf/we-retail-run`** 包含We.Retail Run專案的所有設定。 **`/content/dam/we-retail-run`** 包括啟動專案的數位資產。 **`/content/screens/we-retail-run`** 包含「畫面」內容結構。 這些路徑下方的內容主要會在AEM中更新。 為了提高環境（本地、開發、舞台、prod）之間的一致性，通常在原始碼控制中保存基本內容結構。

1. **導覽至「AEM畫面&gt; We.Retail Run」專案：**

   從「AEM開始功能表&gt;按一下畫面圖示」。 驗證是否可以看到We.Retail Run Project。

   ![我們的"入門"](assets/we-retaiul-run-starter.png)

## 建立Hello world元件 {#hello-world-cmp}

Hello world元件是一個簡單元件，允許用戶輸入要顯示在螢幕上的消息。 此元件以 [AEM Screens元件範本為基礎：https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template).

AEM Screens有一些有趣的限制條件，這對於傳統的WCM Sites元件不一定適用。

* 大部分的「螢幕」元件需要在目標數位標牌裝置上以全螢幕執行
* 大部分的「畫面」元件必須可內嵌在序列頻道中，才能產生投影片
* 撰寫應允許編輯序列頻道中的個別元件，因此不需要全螢幕呈現

1. 在 **CRXDE-Lite**`http://localhost:4502/crx/de/index.jsp` （或您選擇的IDE）中，導覽至 `/apps/weretail-run/components/content/helloworld.`

   將下列屬性新增至元 `helloworld` 件：

   ```
       jcr:title="Hello World"
       sling:resourceSuperType="foundation/components/parbase"
       componentGroup="We.Retail Run - Content"
   ```

   ![/apps/weretail-run/components/content/helloworld的屬性](assets/2018-04-28_at_4_23pm.png)

   /apps/weretail-run/components/content/helloworld的屬性

   該 **Helloworld** 元件延伸 **該基礎／元件/parbase** 元件，使其能夠在序列通道內正確使用。

1. 在名為的下方建立檔 `/apps/weretail-run/components/content/helloworld` 案 `helloworld.html.`

   在檔案中填入下列項目：

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/helloworld.html
   
   */-->
   
   <!--/* production: preview authoring mode + unspecified mode (i.e. on publish) */-->
   <sly data-sly-test.production="${wcmmode.preview || wcmmode.disabled}" data-sly-include="production.html" />
   
   <!--/* edit: any other authoring mode, i.e. edit, design, scaffolding, etc. */-->
   <sly data-sly-test="${!production}" data-sly-include="edit.html" />
   ```

   畫面元件需要兩種不同的轉譯，視使 [用的製作模式](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/author-environment-tools.html#PageModes) 而定：

   1. **生產**:預覽或發佈模式(wcmmode=disabled)
   1. **編輯**:用於所有其他製作模式，例如編輯、設計、腳手架、開發人員……
   `helloworld.html`當做交換機，檢查哪個編寫模式目前處於活動狀態並重新導向至另一個HTL指令碼。 畫面元件使用的常見慣例是使用「編輯」 `edit.html` 模式的指令碼和「生 `production.html` 產」模式的指令碼。

1. 在名為的下方建立檔 `/apps/weretail-run/components/content/helloworld` 案 `production.html.`

   在檔案中填入下列項目：

   ```xml
   <!--/*
    /apps/weretail-run/components/content/helloworld/production.html
   
   */-->
   
   <div data-duration="${properties.duration}" class="cmp-hello-world">
    <h1 class="cmp-hello-world__message">${properties.message}</h1>
   </div>
   ```

   以上是Hello world元件的生產標籤。 由 `data-duration` 於元件用於序列頻道，因此包含屬性。 序 `data-duration` 列渠道使用屬性來瞭解序列項目的顯示時間。

   元件會轉譯 `div` 和標 `h1` 記含文字。 `${properties.message}` 是HTL指令碼的一部分，將輸出名為的JCR屬性的內容 `message`。 稍後將建立一個對話框，允許用戶為屬性文本輸 `message` 入值。

   另請注意，BEM（塊元素修飾詞）注釋與元件一起使用。 BEM是CSS編碼慣例，可讓您更輕鬆地建立可重複使用的元件。 BEM是 [AEM核心元件使用的符號](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions)。 如需詳細資訊，請參閱： [https://getbem.com/](https://getbem.com/)

1. 在名為的下方建立檔 `/apps/weretail-run/components/content/helloworld` 案 `edit.html.`

   在檔案中填入下列項目：

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/edit.html
   
   */-->
   
   <!--/* if message populated */-->
   <div
    data-sly-test.message="${properties.message}"
    class="aem-Screens-editWrapper cmp-hello-world">
    <p class="cmp-hello-world__message">${message}</p>
   </div>
   
   <!--/* empty place holder */-->
   <div data-sly-test="${!message}"
        class="aem-Screens-editWrapper cq-placeholder cmp-hello-world"
        data-emptytext="${'Hello World' @ i18n, locale=request.locale}">
   </div>
   ```

   以上是Hello world元件的編輯標籤。 如果已填入對話訊息，第一個區塊會顯示元件的編輯版本。

   如果未輸入對話消息，則呈現第二塊。 在此 `cq-placeholder` 情 `data-emptytext` 況下，標籤 ***Hello World*** 會呈現為預留位置。 標籤的字串可以使用i18n進行國際化，以支援在多個地區設定中編寫。

1. **Copy Screens Image Dialog to be used for the Hello World component.**

   從現有對話方塊開始進行修改最簡單。

   1. 從以下位置複製對話框： `/libs/screens/core/components/content/image/cq:dialog`
   1. 將對話方塊貼在下方 `/apps/weretail-run/components/content/helloworld`
   ![copy-image-dialog](assets/copy-image-dialog.gif)

1. **更新「Hello World」對話框以包含消息的頁籤。**

   更新對話方塊，使其符合下列項目。 XML中顯示最終對話框的JCR節點結構如下：

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Hello World"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/coral/foundation/tabs"
           size="L">
           <items jcr:primaryType="nt:unstructured">
               <message
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Message"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <message
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/textfield"
                                   fieldDescription="Message for component to display"
                                   fieldLabel="Message"
                                   name="./message"/>
                           </items>
                       </column>
                   </items>
               </message>
               <sequence
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Sequence"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <duration
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/numberfield"
                                   defaultValue=""
                                   fieldDescription="Amount of time the image will be shown in the sequence, in milliseconds"
                                   fieldLabel="Duration (ms)"
                                   min="0"
                                   name="./duration"/>
                           </items>
                       </column>
                   </items>
               </sequence>
           </items>
       </content>
   </jcr:root>
   ```

   消息的文本欄位將保存到名為的屬性， `message` 並且持續時間的編號欄位將保存到名為的屬性 `duration`。 HTL中參照這兩個 `/apps/weretail-run/components/content/helloworld/production.html` 屬性 `${properties.message}` 為和 `${properties.duration}`。

   ![Hello World —— 已完成對話方塊](assets/2018-04-29_at_5_21pm.png)

   Hello World —— 已完成對話方塊

## 建立用戶端程式庫 {#clientlibs}

用戶端程式庫提供組織和管理AEM實作所需CSS和JavaScript檔案的機制。

AEM Screens元件在「編輯」模式與「預覽／生產」模式的轉譯方式不同。 將會建立兩個用戶端程式庫，一個用於編輯模式，另一個用於預覽／生產。

1. 為Hello world元件的客戶端庫建立資料夾。

   在下 `/apps/weretail-run/components/content/helloworld`面建立名為的新資料夾 `clientlibs`。

   ![2018-04-30_at_1046am](assets/2018-04-30_at_1046am.png)

1. 在資料夾 `clientlibs` 下面建立一個名為「類型」的 `shared` 新節點 `cq:ClientLibraryFolder.`

   ![2018-04-30_at_1115am](assets/2018-04-30_at_1115am.png)

1. 將下列屬性新增至共用用戶端程式庫：

   * `allowProxy` | 布林函數 | `true`

   * `categories`|字串[] | `cq.screens.components`
   ![/apps/weretail-run/components/content/helloworld/clientlibs/shared的屬性](assets/2018-05-03_at_1026pm.png)

   /apps/weretail-run/components/content/helloworld/clientlibs/shared的屬性

   類別屬性是識別用戶端程式庫的字串。 cq.screens.components類別可在「編輯」和「預覽／生產」模式中使用。 因此，在sharedclientlib中定義的任何CSS/JS都會以所有模式載入。

   絕對不要在生產環境中直接將任何路徑顯示至/app，這是最佳做法。 allowProxy屬性可確保用戶端程式庫CSS和JS是透過首碼of/etc.clientlibs來參考。

1. 在共用資料夾 `css.txt` 下方建立名稱的檔案。

   在檔案中填入下列項目：

   ```
   #base=css
   
   styles.less
   ```

1. 在資料夾下建立 `css` 一個名為的 `shared` 資料夾。 在資料夾下方新 `style.less` 增名為的 `css` 檔案。 用戶端程式庫的結構現在應如下所示：

   ![2018-04-30_at_3_11pm](assets/2018-04-30_at_3_11pm.png)

   本教學課程不使用LESS直接編寫CSS。 [LESS](https://lesscss.org/) 是常用的CSS預編譯器，可支援CSS變數、混合和函式。 AEM用戶端程式庫本身支援LESS編譯。 Sass或其他預先編譯器可使用，但需在AEM以外進行編譯。

1. 填 `/apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less` 入下列：

   ```css
   /**
       Shared Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less
   
   **/
   
   .cmp-hello-world {
       background-color: #fff;
   
    &__message {
     color: #000;
     font-family: Helvetica;
     text-align:center;
    }
   }
   ```

1. 複製並貼上用戶 `shared` 端程式庫資料夾，以建立名為的新用戶端程式庫 `production`。

   ![複製共用用戶端程式庫以建立新的生產用戶端程式庫](assets/copy-clientlib.gif)

   複製共用用戶端程式庫以建立新的生產用戶端程式庫

1. 將生產 `categories` 客戶端庫的屬性更新為 `cq.screens.components.production.`

   這可確保只有在「預覽／生產」模式下才載入樣式。

   ![/apps/weretail-run/components/content/helloworld/clientlibs/production的屬性](assets/2018-04-30_at_5_04pm.png)

   /apps/weretail-run/components/content/helloworld/clientlibs/production的屬性

1. 填 `/apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less` 入下列：

   ```css
   /**
       Production Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less
   
   **/
   .cmp-hello-world {
   
       height: 100%;
       width: 100%;
       position: fixed;
   
    &__message {
   
     position: relative;
     font-size: 5rem;
     top:25%;
    }
   }
   ```

   上述樣式會將訊息置於畫面中央，但只會顯示在生產模式中。

第三個clientlibrary類別：可用 `cq.screens.components.edit` 於將僅編輯的特定樣式添加到元件中。

| Clientlib類別 | 使用狀況 |
|---|---|
| `cq.screens.components` | 在編輯和生產模式之間共用的樣式和指令碼 |
| `cq.screens.components.edit` | 僅用於編輯模式的樣式和指令碼 |
| `cq.screens.components.production` | 僅用於生產模式的樣式和指令碼 |

## 建立設計頁面 {#design-page}

AEM Screens使用靜 [態頁面範本](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/page-templates-static.html)[和設計組態](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/default-components-designmode.html) ，進行全域變更。 設計配置常用於為通道上的Parsys配置允許的元件。 最佳實務是以應用程式特定的方式儲存這些設定。

在「We.Retail Run Design」（We.Retail Run設計）頁面下建立，該頁面將儲存We.Retail Run項目的所有特定配置。

1. 在 **CRXDE-Lite中** ，導 `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs` 覽至 `/apps/settings/wcm/designs`
1. 在設計資料夾下方建立新節點， `we-retail-run` 以類型命名 `cq:Page`。
1. 在頁面 `we-retail-run` 下，添加另一個名為類 `jcr:content` 型的節點 `nt:unstructured`。 將以下屬性添加到節 `jcr:content` 點：

   | 名稱 | 類型 | 值 |
   |---|---|---|
   | jcr:title | 字串 | We.Retail Run |
   | sling:resourceType | 字串 | wcm/core/components/designer |
   | cq:doctype | 字串 | html_5 |

   ![設計頁面，網址為：/apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1219pm.png)

   設計頁面，網址為：/apps/settings/wcm/designs/we-retail-run

## 建立序列渠道 {#create-sequence-channel}

Hello World元件用於序列通道。 若要測試元件，會建立新的「序列頻道」。

1. 從「AEM開始」功能表導覽至「畫面 **&gt;** We.Retail **Run &gt;」，然後選取「**&#x200B;頻道 ****」。

1. 按一下「 **建立** 」按鈕

   1. 選擇 **建立實體**
   ![2018-04-30_at_5_18pm](assets/2018-04-30_at_5_18pm.png)

1. 在建立嚮導中：

1. 範本步驟——選擇**序列頻道**

   1. 屬性步驟
   * 「基本標籤&gt;標題=空 **閒頻道」**
   * 渠道標籤&gt;勾選 **線上渠道**
   ![空閒通道](assets/idle-channel.gif)

1. 開啟閒置頻道的頁面屬性。 更新「設計」欄位，以指 `/apps/settings/wcm/designs/we-retail-run,`向在上一節中建立的設計頁面。

   ![設計設定/apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1240pm.png)

   指向/apps/settings/wcm/designs/we-retail-run的設計組態

1. 編輯新建立的閒置頻道以開啟它。

1. 將頁面模式切換為 **設計模式**

   1. 按一下 **Parsys中的** 「扳手圖示」，以設定允許的元件

   1. 選取「 **畫面** 」群組和「 **We.Retail Run —— 內容」群組** 。
   ![2018-04-30_at_5_43pm](assets/2018-04-30_at_5_43pm.png)

1. 將頁面模式切換為「 **編輯」**。 Hello World元件現在可以新增至頁面，並與其他序列頻道元件結合。

   ![2018-04-30_at_5_53pm](assets/2018-04-30_at_5_53pm.png)

1. 在 **CRXDE-Lite中** ，導 `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs/we-retail-run/jcr%3Acontent/sequencechannel/par` 覽至 `/apps/settings/wcm/designs/we-retail-run/jcr:content/sequencechannel/par`。 請注意， `components` 屬性現在包 `group:Screens`含 `group:We.Retail Run - Content`。

   ![在/apps/settings/wcm/designs/we-retail-run下進行設計設定](assets/2018-05-07_at_1_14pm.png)

   在/apps/settings/wcm/designs/we-retail-run下進行設計設定

## 整合在一起 {#putting-it-all-together}

以下視訊顯示完成的元件，以及如何將它新增至「序列」頻道。 接著，「頻道」會新增至「位置」顯示畫面，並最終指派給「畫面」播放器。

>[!VIDEO](https://video.tv.adobe.com/v/22385?quaity=9&captions=chi_hant)

## 完成的程式碼 {#finished-code}

以下是教學課程中完成的程式碼。 screens-weretail-run.ui.ap **ps-0.0.1-SNAPSHOT.zip** 和 **** screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip是編譯的AEM套件。 **SRC-screens-weretail-run-0.0.1.zip **是可使用Maven部署的未編譯原始碼。

[取得檔案](assets/screens-weretail-runuiapps-001-snapshot.zip)

[取得檔案](assets/screens-weretail-runuicontent-001-snapshot.zip)

[取得檔案](assets/screens-weretail-run.zip)

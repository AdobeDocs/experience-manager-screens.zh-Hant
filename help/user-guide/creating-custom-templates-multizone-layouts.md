---
title: 在多區域版面中建立自訂範本
seo-title: 在多區域版面中建立自訂範本
description: 請依照本頁來瞭解如何在MultiZone版面中建立自訂範本。
seo-description: 請依照本頁來瞭解如何在MultiZone版面中建立自訂範本。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 6a0967580d06e749db878d74aad2ffb1fec82f43

---


# 在多區域版面中建立自訂範本 {#creating-custom-templates-multizone}

本頁面展示如何在多區域版面中建立自訂範本。

## 命名慣例 {#name-terms}

在您瞭解如何建立自訂多區域範本以用於AEM Screens專案之前，建議您先瞭解您要建立的範本版本。

| **版面名稱** | **說明** |
|---|---|
| Left20-LandscapeHD3Zone | 指3區橫向版面配置，可讓您建立3個區域，其中區域1為左側水準和垂直螢幕的20%、區域2為水準螢幕的80%、右側垂直螢幕的20%、區域3為水準螢幕的100%，垂直螢幕的80%，寬高比為16:9 |
| Upper20-PortraitHD2Zone | 指從上方覆蓋20%螢幕的2區縱向範本，長寬比為16:9 |
| Right20-LandscapeSD3Zone | 指從右側涵蓋20%螢幕的3區範本，長寬比為4:3 |

## 範例使用案例 {#example-use-cases}

## Left20-LandscapeHD3Zone版面 {#custom-template-one}

請依照下節，使用下列組態建立自 *訂範本Left20-LandscapeHD3Zone* :

* **Left20** 是指左側最上方的區域，涵蓋20%的水準和垂直螢幕大小。
* **橫向** ：指螢幕方向
* **HD** 將寬高比指定為16:9
* **3 Zone** (3 Zone)指顯示器的三個區域

## 多區域佈局的可視化表示 {#multi-layout-visual-one}

Left20-LandscapeHD3Zone Layout可讓您在專案中建立下列多區域版面：

![影像](/help/user-guide/assets/custom-multizone/custom-multizone1.png)

## 建立Left20-LandscapeHD3Zone版面 {#landscape-layout-one}

請依照下列步驟，為AEM Screens專案建立Left20-LandscapeHD3Zone Layout:

1. 建立標題為「自訂範本」的AEM **畫面專案**。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. 從您的 **AEM例項** —>工具—> **CRXDE Lite導覽至CRXDE Lite**。

1. 在名為「自訂範本」的 **應用程式** 下建立 **資料夾**。 同樣地，在customtemplate下建立另一 **個名為****模板的資料夾**，如下圖所示。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   > [!NOTE]
   > 建議您每次建立、編輯或複製內容至任何節點時，從CRXDE Lite的動作列按一下「全部儲存 **** 」，否則將無法提交更新。

1. 將左側長條範本從複製 `/libs/screens/core/templates/splitscreenchannel/lbar-left` 到 `/apps/customtemplate/template`。

1. 將複製 **的左側列** (`/apps/customtemplate/template`)重新命 **名為my-custom-layout**。

1. 導覽並 `/apps/customtemplate/template/my-custom-layout` 更新屬性 **jcr:description** 至Left20-LandscapeHD3Zone的「 *Template」（範本）和* jcr:title ******&#x200B;至Left20-LandscapeHD3Zone的「Template」（模板）。

1. 從導覽至 **offline-config** 節點， `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` 並將 **jcr:title** 更新 *為Left20-LandscapeHD3Zone*。

1. 從導覽至 *my custom-template* 的jcr:content **屬性，並將** cq:cssClass `/apps/customtemplate/template/my-custom-layout/jcr:content`********&#x200B;屬性更新至Aem-My custom-layout的Layout。

1. 參考步驟(4)，在步驟中，您複製左側的範本，您將在下方檢視3個回應式格線 `my-custom-layout/jcr:content`。 在 *cq:cssClass* 屬性中，將自訂css類別新增至每個互動式格線，例如 *my-custom-layout -top-left*, *my-custom-layout -top-right*, ** my-custom-layout -bottomCassing。

   >[!NOTE]
   >這些自訂類別將用於css中，以設定這些互動式格點的寬度／高度。

   >[!NOTE]
   > 您可以根據所需的網格總數來添加或刪除自適應網格。 在此範例中，我們展示第一列的2個格點和第二列的1個格點，因此共有3個回應式格點(r1c1、r1c2、r2c1)。

1. 複製 `/libs/settings/wcm/designs/screens` 至 `/apps/settings/wcm/designs/` 自訂範本 **設計並重新命名**

1. 導覽至 `/apps/settings/wcm/designs/custom-template-designs` custom-template-designs的屬 *性jcr:title* ，並將其更新 **為customtemplate-design****的屬性**。

1. 更新內 `/apps/settings/wcm/designs/<project>-designs/static.css` 容以符合下列

## 使用特定配置建立自定義模板 {#basic-flow-setting}

![影像](assets/custom-template1.png)

請依照下列步驟建立自訂範本。

1. 在 `/apps/<project>/templates/my-custom-layout`

   ```shell
    <?xml version="1.0" encoding="UTF-8"?>
    <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
    jcr:description="My Custom 3-zones layout "
    jcr:primaryType="cq:Template"
    jcr:title="3-zones layout"
    allowedParents="[/libs/screens/core/templates/channelfolder]"
    allowedPaths="[/content/screens(/.*)?]"
    ranking="{Long}20000">
    <jcr:content
        cq:cssClass="aem-Layout aem-Layout--3x1 my-CustomLayout"
        cq:designPath="/apps/settings/wcm/designs/<project>"
        cq:deviceGroups="[mobile/groups/responsive]"
        jcr:primaryType="cq:PageContent"
        sling:resourceSuperType="screens/core/components/channel"
        sling:resourceType="screens/core/components/multiscreenchannel">
        <r1c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-top"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r2c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-middle"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r3c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-bottom"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <cq:responsive jcr:primaryType="nt:unstructured">
            <breakpoints jcr:primaryType="nt:unstructured"/>
        </cq:responsive>
        <offline-config/>
    </jcr:content>
   </jcr:root>
   ```

1. 在中建立頁面設計 `/apps/settings/wcm/designs/<project>`。

   >[!NOTE]
   >
   >請確定上 `cq:designPath` 述路徑相符。

1. 更新 **離線設定節點** ，讓設計指向新路徑

1. 在資料 **夾中新增static.css**`/apps/settings/wcm/designs/<project>` 檔案，並將其內容設定為

   ```shell
   .cq-Screens-channel--multizone.my-CustomLayout {}
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-top { height: 150px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-middle { height: 1470px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-bottom { height: 300px; }
   ```

## 將影像插入背景圖層 {#inserting-image}

您可以將影像設定為版面的背景圖層：

您可以調整CSS規則，使用稱為「data-uri」的項目，並直接將影像（Base64編碼）內嵌在CSS檔案中。

這如下所述：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您可以遵循下列步驟：

1. 請確定影像是否包含在頻道的離線設定中
1. 使用上述CSS中影像的直接連結，而非「data-uri」變體


## 更新背景顏色 {#updating-color}

若要變更背景顏色，請將下列程式碼新增至xml檔案：

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`




---
title: 在多區域版面中建立自訂範本
seo-title: 在多區域版面中建立自訂範本
description: 請依照本頁來瞭解如何在MultiZone版面中建立自訂範本。
seo-description: 請依照本頁來瞭解如何在MultiZone版面中建立自訂範本。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 23208ed9e4e293cfcec65305918f35573c20cc02

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
   ![影像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. 導覽並 `/apps/customtemplate/template/my-custom-layout` 更新屬性 **jcr:description** 至Left20-LandscapeHD3Zone的「 *Template」（範本）和* jcr:title ******&#x200B;至Left20-LandscapeHD3Zone的「Template」（模板）。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. 從導覽至 **offline-config** 節點， `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` 並將 **jcr:title** 更新 *為Left20-LandscapeHD3Zone*。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. 從導覽至 *my custom-template* 的jcr:content **屬性，並將** cq:cssClass `/apps/customtemplate/template/my-custom-layout/jcr:content`********&#x200B;屬性更新至Aem-My custom-layout的Layout。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 參考步驟(4)，在步驟中，您複製左側的範本，您將在下方檢視3個回應式格線 `my-custom-layout/jcr:content`。 在 *cq:cssClass* 屬性中，將自訂css類別新增至每個回應式格線，例如， *my-custom-layout -* r1c1節點的左上角(top-left ** )。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同樣地， *為r1c2添加* my-custom-layout —— 右上角 ** r1c2 *,* my-custom-layout - bottom *for* r2c1 node。

   >[!NOTE]
   >這些自訂類別將用於css中，以設定這些互動式格點的寬度／高度。

   >[!NOTE]
   > 您可以根據所需的網格總數來添加或刪除自適應網格。 在此範例中，我們展示第一列的2個格點和第二列的1個格點，因此共有3個回應式格點(r1c1、r1c2、r2c1)。

1. 復 `/libs/settings/wcm/designs/screens` 制復 `/apps/settings/wcm/designs/` 制並將複製的設計重 **新命名為自訂範本設計**。

1. 導覽至 `/apps/settings/wcm/designs/custom-template-designs` custom-template-designs的屬 *性jcr:title* ，並將其更新 **為customtemplate-design****的屬性**。

1. 導覽至 `/apps/settings/wcm/designs/custom-template-designs` 並建立檔案static.css。

1. 將內容複製至static.css檔案：

   ```shell
       /*my-custom-layout styles*/
      .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-left {
       width:20%;
       height: 36%;
      float: left !important;
      }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-right {
      width:80%;
      height: 36%;
     float: left !important;
     }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--bottom {
     width:100%;
     height: 64%;
     }
   ```

   >[!NOTE]
   > 您可以更新百分比以符合自訂範本的需求。

1. 導覽至 `/apps/<project>/templates/my-custom-layout/jcr:content` 並更新屬 *性cq:designPath* ，以載 `/apps/settings/wcm/designs/customtemplate-designs` 入static.css中設定的樣式

   >[!NOTE]
   > 建議您輸入所有樣式，而非複製或貼上，這會造成空格造成css樣式問題。

## 查看結果 {#viewing-result}

請依照下列步驟，在您的AEM Screens專案中使用上述自訂範本：

1. 導覽至您在步驟(1)中建立的畫面專案，並選取「頻道」 **檔案夾** 。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 從動 **作列按一下「建立** 」，並從「建立」精靈中選取範本 **Left20-LandscapeHD3Zone****** 。

1. 使用自訂範本建立渠道後，您就可以從編輯器將資產新增至渠道。

## 將影像插入背景圖層 {#inserting-image}

您可以將影像插入版面中做為背景圖層：

您可以調整CSS規則，使用稱為「data-uri」的項目，並直接將影像（Base64編碼）內嵌在CSS檔案中。

這如下所述：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您可以遵循下列步驟：

1. 請確定影像是否包含在頻道的離線設定中
1. 使用上述CSS中影像的直接連結，而非「data-uri」變體


## 更新背景顏色 {#updating-color}

若要變更背景顏色，請將下列程式碼新增至xml檔案：

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`




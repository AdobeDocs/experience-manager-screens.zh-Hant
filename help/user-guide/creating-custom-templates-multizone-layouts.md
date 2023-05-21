---
title: 在多區域佈局中建立自定義模板
seo-title: Creating Custom Templates in MultiZone Layouts
description: 按照本頁瞭解如何在MultiZone佈局中建立自定義模板。
seo-description: Follow this page to learn about creating custom templates in MultiZone layouts.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 1%

---

# 為多區域佈局建立自定義模板 {#creating-custom-templates-multizone}

此頁顯示如何為多區域佈局建立自定義模板。

## 重要考量 {#considerations}

在多區域佈局中建立自定義模板之前，必須注意以下兩個重要注意事項：

1. **固定像素大小或百分比**:

   您必須決定是否為自定義佈局的不同區域使用固定像素大小，或者是否要使用百分比建立自定義佈局。

   >[!NOTE]
   >使用百分比為自定義佈局設定區域的好處是，您可以在各種螢幕大小上重複使用模板。

1. **命名約定**:

   在瞭解如何建立要在AEM Screens項目中使用的自定義多區域模板之前，建議您先瞭解要建立的模板的版本。

   | **佈局名稱** | **說明** |
   |---|---|
   | Left20-LandscapeHD3Zone | 指3區橫向佈局，它允許您建立3個區域，區域1為左側水準和垂直螢幕的20%，區域2為水準螢幕的80%，右側垂直螢幕的20%對齊，區域3為水準螢幕的100%，縱向螢幕的80%，縱橫比為16:9 |
   | Upper20-PortraitHD2Zone | 指從頂部覆蓋20%螢幕的2區縱向模板，縱橫比為16:9 |
   | Right20-LandscapeSD3區 | 指從右側覆蓋20%螢幕的3區模板，長寬比為4:3 |

   >[!IMPORTANT]
   >在自定義佈局中定義的區域可能與整個佈局的整體縱橫比不匹配。 本文檔中遵循的命名約定將自定義佈局的縱橫比指定為整體。

## 示例用例Left20-LandscapeHD3Zone佈局 {#custom-template-one}

按照下面的部分建立自定義模板 *Left20-LandscapeHD3Zone* 配置：

* **左20** 指左側的頂部區域，覆蓋20%的水準和垂直螢幕大小。
* **橫向** 指螢幕方向
* **高清** 將寬高比表示為16:9
* **3區** 指顯示器的三個區域

## 多區域佈局的可視化表示 {#multi-layout-visual-one}

Left20-LandscapeHD3Zone佈局允許您在項目中建立以下多區域佈局：

![影像](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## 建立Left20-LandscapeHD3Zone佈局 {#landscape-layout-one}

按照以下步驟為AEM Screens項目建立Left20-LandscapeHD3Zone佈局：

1. 建立標題為的AEM Screens項目 **customtemplate（自定義模板）**。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. 導航到 **CRXDE Lite** 從實AEM例 — >工具 — > **CRXDE Lite**。

1. 建立資料夾 **應用** 標題 **customtemplate（自定義模板）**。 同樣，建立另一個名為 **模板** 在 **customtemplate（自定義模板）**，如下圖所示。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >建議您按一下 **全部保存** 每次建立、編輯內容或將內容複製到任何節點時，都會從CRXDE Lite中的操作欄中，否則將無法提交更新。

1. 複製左欄模板 `/libs/screens/core/templates/splitscreenchannel/lbar-left` 至 `/apps/customtemplate/template`。

1. 更名複製的 **左欄** (`/apps/customtemplate/template`) **自定義佈局**。
   ![影像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. 導航到 `/apps/customtemplate/template/my-custom-layout` 並更新屬性 **jcr：說明** 至 *Left20-LandscapeHD3Zone模板* 和 **jcr：標題** 至 *Left20-LandscapeHD3Zone*。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. 導航到 **離線配置** 節點 `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` 並更新 **jcr：標題** 至 *Left20-LandscapeHD3Zone*。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. 導航到 *jcr：內容* 物業 **我的自定義模板** 從 `/apps/customtemplate/template/my-custom-layout/jcr:content` 並更新 **cq:css類** 屬性 **aem-layout my-custom-layout**。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 參考步驟(4)，在步驟中，您複製了左欄模板，您將在下面查看3個響應網格 `my-custom-layout/jcr:content`。 將自定義css類添加到 *cq:css類* 屬性，例如 *my-custom-layout — 左上* 為 *r1c* 的下界。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同樣，添加 *my-custom-layout — 右上* 為 *r1c2*  和 *my-custom-layout — 底部* 為 *r2c1* 的下界。

   >[!NOTE]
   >這些自定義類將用於css中，以設定這些響應網格的寬度/高度。

   >[!NOTE]
   >您可以根據所需的總網格數來添加或刪除響應網格。 在本示例中，我們在第一行中顯示2個網格，在第二行中顯示1個網格，因此總共有3個響應網格(r1c1、r1c2、r2c1)。

1. 複製 `/libs/settings/wcm/designs/screens` 至 `/apps/settings/wcm/designs/` 並將複製的設計更名為 **自定義模板設計**。

1. 導航到 `/apps/settings/wcm/designs/custom-template-designs` 並更新屬性 *jcr：標題* 共 **自定義模板設計** 至 **定制模板設計**。

1. 導航到 `/apps/settings/wcm/designs/custom-template-designs` 建立一個static.css檔案。

1. 將內容複製到 `static.css` 檔案：

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
   >您可以更新百分比以符合自定義模板的要求。

1. 導航到 `/apps/<project>/templates/my-custom-layout/jcr:content` 並更新屬性 *cq:designPath* 至 `/apps/settings/wcm/designs/customtemplate-designs` 載入在static.css中配置的樣式

   >[!NOTE]
   >建議鍵入所有樣式，而不是複製或貼上，這會導致空格導致css樣式問題。

## 查看結果 {#viewing-result}

按照以下步驟在您的AEM Screens項目中使用上述自定義模板：

1. 導航到您在步驟(1)中建立的螢幕項目，然後選擇 **頻道** 的子菜單。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 按一下 **建立** 從操作欄中選擇模板 **Left20-LandscapeHD3Zone** 從 **建立** 的子菜單。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 使用自定義模板建立頻道後，可以從編輯器將資產添加到頻道。 以下預覽顯示自定義模板中的影像。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 將影像插入為背景層  {#inserting-image}

可以將影像作為背景圖層插入佈局：

您可以調整CSS規則，使用在（步驟13）中建立的CSS檔案中稱為「data-uri」的內聯影像（Base64編碼）, *static.css*。

具體操作如下：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您可以執行以下步驟：

1. 確保映像以某種方式包含在通道的離線配置中
1. 使用上面CSS中影像的直接連結，而不是「data-uri」變體


## 更新背景顏色 {#updating-color}

要更改背景顏色，請將以下代碼添加到xml檔案（步驟13）, *static.css*。

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`

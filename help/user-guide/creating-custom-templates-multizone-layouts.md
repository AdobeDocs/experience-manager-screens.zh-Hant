---
title: 在多區域版面中建立自訂範本
seo-title: 在多區域版面中建立自訂範本
description: 請依照本頁來瞭解如何在MultiZone版面中建立自訂範本。
seo-description: 請依照本頁來瞭解如何在MultiZone版面中建立自訂範本。
contentOwner: Jyotika Syal
feature: 開發螢幕
role: 開發人員
level: 中級
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 1%

---


# 建立多區域版面的自訂範本{#creating-custom-templates-multizone}

本頁面展示如何建立多區域版面的自訂範本。

## 重要注意事項{#considerations}

在多區域版面中建立自訂範本之前，您必須注意兩個重要考量：

1. **固定像素大小或百分比**:

   您必須決定是否針對自訂版面的不同區域使用固定像素大小，或是您想要使用百分比建立自訂版面。

   >[!NOTE]
   >使用百分比來設定自訂版面的區域的好處，可讓您在各種螢幕大小上重複使用範本。

1. **命名慣例**:

   在瞭解如何建立自訂多區域範本以用於AEM Screens專案之前，建議您先瞭解您要建立之範本的版本。

   | **版面名稱** | **說明** |
   |---|---|
   | Left20-LandscapeHD3Zone | 指3區橫向版面配置，可讓您建立3個區域，其中區域1為左側水準和垂直螢幕的20%、區域2為水準螢幕的80%、右側垂直螢幕的20%、區域3為水準螢幕的100%，垂直螢幕的80%，寬高比為16:9 |
   | Upper20-PortraitHD2Zone | 指從上方覆蓋20%螢幕的2區縱向範本，長寬比為16:9 |
   | Right20-LandscapeSD3Zone | 指從右側涵蓋20%螢幕的3區範本，長寬比為4:3 |

   >[!IMPORTANT]
   >在自訂版面中定義的區域可能不符合整個版面的整體外觀比例。 本檔案中遵循的命名慣例會指定自訂版面的整體外觀比例。

## 範例使用案例Left20-LandscapeHD3Zone Layout {#custom-template-one}

請依照下節，建立具有下列組態的自訂範本&#x200B;*Left20-LandscapeHD3Zone*:

* **Left20** 是指左側最上方的區域，涵蓋20%的水準和垂直螢幕大小。
* **版** 面設計指螢幕方向
* **** HD將寬高比指定為16:9
* **3** Zonerears the 3個顯示區

## 多區域佈局的可視表示{#multi-layout-visual-one}

Left20-LandscapeHD3Zone Layout可讓您在專案中建立下列多區域版面：

![影像](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## 建立Left20-LandscapeHD3Zone版面{#landscape-layout-one}

請依照下列步驟，為AEM Screens專案建立Left20-LanscapeHD3Zone版面：

1. 建立名為&#x200B;**customtemplate**&#x200B;的AEM Screens項目。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. 從實例—>工具—> **CRXDE LiteAEM**&#x200B;瀏覽至&#x200B;**CRXDE Lite**。

1. 在&#x200B;**apps**&#x200B;下建立名為&#x200B;**customtemplate**&#x200B;的資料夾。 同樣地，在&#x200B;**customtemplate**&#x200B;下建立名為&#x200B;**template**&#x200B;的另一個資料夾，如下圖所示。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >建議您每次建立、編輯或將內容複製到任何節點時，從CRXDE Lite中的操作欄按一下&#x200B;**保存所有**，否則將無法提交更新。

1. 將左欄範本從`/libs/screens/core/templates/splitscreenchannel/lbar-left`複製至`/apps/customtemplate/template`。

1. 將複製的&#x200B;**lbar-left**(`/apps/customtemplate/template`)重新命名為&#x200B;**my-custom-layout**。
   ![影像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. 導覽至`/apps/customtemplate/template/my-custom-layout`並將屬性&#x200B;**jcr:description**&#x200B;更新為&#x200B;*Template for Left20-LandscapeHD3Zone*&#x200B;和&#x200B;**jcr:title**&#x200B;更新為&#x200B;*Left20-LandscapeHD3Zone*。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. 從`/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config`導覽至&#x200B;**offline-config**&#x200B;節點，並將&#x200B;**jcr:title**&#x200B;更新為&#x200B;*Left20-LandscapeHD3Zone*。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. 從`/apps/customtemplate/template/my-custom-layout/jcr:content`導覽至&#x200B;*jcr:content*&#x200B;屬性的&#x200B;**my-custom-template**，並將&#x200B;**cq:cssClass**&#x200B;屬性更新為&#x200B;**aem-Layout my-custom-layout**。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 參考步驟(4)，在步驟中，您複製了左側的模板，您將在`my-custom-layout/jcr:content`下查看3個自適應網格。 在&#x200B;*cq:cssClass*&#x200B;屬性中，將自訂css類別新增至每個回應式格線，例如&#x200B;*my-custom-layout— top-left* for *r1c1*&#x200B;節點。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同樣地，為&#x200B;*r1c2*&#x200B;新增&#x200B;*my-custom-layout—top-right*，為&#x200B;*r2c1*&#x200B;節點新增&#x200B;*my-custom-layout—bottom*。

   >[!NOTE]
   >這些自訂類別將用於css中，以設定這些互動式格點的寬度／高度。

   >[!NOTE]
   >您可以根據所需的網格總數來添加或刪除自適應網格。 在此範例中，我們展示第一列的2個格點和第二列的1個格點，因此共有3個回應式格點(r1c1、r1c2、r2c1)。

1. 將`/libs/settings/wcm/designs/screens`複製至`/apps/settings/wcm/designs/`，並將複製的設計重新命名為&#x200B;**custom-template-designs**。

1. 導覽至`/apps/settings/wcm/designs/custom-template-designs`並將&#x200B;**custom-template-designs**&#x200B;的屬性&#x200B;*jcr:title*&#x200B;更新為&#x200B;**customtemplate-design**。

1. 導覽至`/apps/settings/wcm/designs/custom-template-designs`並建立檔案static.css。

1. 將內容複製到`static.css`檔案：

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
   >您可以更新百分比以符合自訂範本的需求。

1. 導覽至`/apps/<project>/templates/my-custom-layout/jcr:content`並將屬性&#x200B;*cq:designPath*&#x200B;更新至`/apps/settings/wcm/designs/customtemplate-designs`，以載入static.css中設定的樣式

   >[!NOTE]
   >建議您輸入所有樣式，而非複製或貼上，這會造成空格造成css樣式問題。

## 查看結果{#viewing-result}

請依照下列步驟，在您的AEM Screens專案中使用上述自訂範本：

1. 導覽至您在步驟(1)中建立的畫面專案，並選取&#x200B;**Channels**&#x200B;資料夾。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 從動作列按一下「建立」**「建立」**，並從&#x200B;**「建立」精靈中選取範本** Left20-LandscapeHD3Zone **。**

   ![影像](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 使用自訂範本建立渠道後，您就可以從編輯器將資產新增至渠道。 下列預覽顯示自訂範本中的影像。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 將影像插入為背景圖層{#inserting-image}

您可以將影像插入版面中做為背景圖層：

您可以調整CSS規則，使用稱為&quot;data-uri&quot;的項目，並直接將您在（步驟13）*static.css*&#x200B;中建立的影像（Base64編碼）內嵌在CSS檔案中。

這如下所述：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您可以遵循下列步驟：

1. 請確定影像是否包含在頻道的離線設定中
1. 使用上述CSS中影像的直接連結，而非「data-uri」變體


## 更新背景顏色{#updating-color}

若要變更背景顏色，請將下列程式碼新增至xml檔案（步驟13）*static.css*。

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`




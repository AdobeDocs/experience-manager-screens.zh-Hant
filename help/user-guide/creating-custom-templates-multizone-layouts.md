---
title: 以多區域佈局建立自定義模板
seo-title: 以多區域佈局建立自定義模板
description: 請參照本頁了解如何在多區域佈局中建立自定義模板。
seo-description: 請參照本頁了解如何在多區域佈局中建立自定義模板。
contentOwner: Jyotika Syal
feature: 開發螢幕
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 1%

---


# 為多區域佈局建立自定義模板{#creating-custom-templates-multizone}

此頁面將展示如何為多區域版面建立自訂範本。

## 重要考量 {#considerations}

在以多區域佈局建立自定義模板之前，必須注意以下兩點：

1. **固定像素大小或百分比**:

   您必須決定要針對不同區域使用固定像素大小來進行自訂配置，還是要使用百分比建立自訂配置。

   >[!NOTE]
   >使用百分比為自訂版面設定區域的好處是，您可以在各種螢幕大小上重複使用範本。

1. **命名慣例**:

   在了解如何建立要在AEM Screens專案中使用的自訂多區域範本之前，建議您先了解您要建立的範本的概念。

   | **版面名稱** | **說明** |
   |---|---|
   | Left20-LandscapeHD3Zone | 指的是3區橫向佈局，可讓您建立3個區域，其中區域1為左側水準和垂直螢幕的20%，區域2為水準螢幕的80%，垂直螢幕的右側對齊為20%，區域3為水準螢幕的100%，垂直螢幕的80%，長寬比為16:9 |
   | Upper20-PorraitHD2Zone | 是指從上方覆蓋20%螢幕的2區縱向範本，長寬比為16:9 |
   | Right20-LandscapeSD3Zone | 是指從右側覆蓋20%螢幕的3區範本，長寬比為4:3 |

   >[!IMPORTANT]
   >在自訂配置中定義的區域可能與整個佈局的整體外觀比例不匹配。 本檔案中遵循的命名慣例會將自訂版面的外觀比例指定為整體。

## 示例使用案例Left20-LandscapeHD3Zone佈局{#custom-template-one}

請依照下節，使用下列設定建立自訂範本&#x200B;*Left20-LandscapeHD3Zone*:

* **Left20** 是指位於左側的頂部區域，覆蓋了20%的水準和垂直螢幕大小。
* **** 直向是指螢幕方向
* **** HD將外觀比率表示為16:9
* **3** 區域是指顯示器的三個區域

## 多區域佈局的可視表示{#multi-layout-visual-one}

Left20-LandscapeHD3Zone Layout允許您在項目中建立以下多區域佈局：

![影像](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## 建立Left20-LandscapeHD3Zone佈局{#landscape-layout-one}

請依照下列步驟，為AEM Screens專案建立Left20-LandscapeHD3Zone版面：

1. 建立標題為&#x200B;**customtemplate**&#x200B;的AEM Screens項目。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. 從您的AEM例項 — >工具 — > **CRXDE Lite**&#x200B;導覽至&#x200B;**CRXDE Lite**。

1. 在&#x200B;**apps**&#x200B;下建立標題為&#x200B;**customtemplate**&#x200B;的資料夾。 同樣地，在&#x200B;**customtemplate**&#x200B;下建立另一個名為&#x200B;**template**&#x200B;的資料夾，如下圖所示。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >建議您每次建立、編輯內容或將內容複製到任何節點時，都要按一下CRXDE Lite中動作列的&#x200B;**「儲存全部」**，否則將無法提交更新。

1. 將左欄範本從`/libs/screens/core/templates/splitscreenchannel/lbar-left`複製到`/apps/customtemplate/template`。

1. 將複製的&#x200B;**lbar-left**(`/apps/customtemplate/template`)重新命名為&#x200B;**my-custom-layout**。
   ![影像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. 導覽至`/apps/customtemplate/template/my-custom-layout`並將屬性&#x200B;**jcr:description**&#x200B;更新至&#x200B;*Left20-LandcaseHD3Zone*&#x200B;的範本，以及將&#x200B;**jcr:title**&#x200B;更新至&#x200B;*Left20-LandcaseHD3Zone*。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. 從`/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config`導覽至&#x200B;**offline-config**&#x200B;節點，並將&#x200B;**jcr:title**&#x200B;更新至&#x200B;*Left20-LandcaseHD3Zone*。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. 從`/apps/customtemplate/template/my-custom-layout/jcr:content`導覽至&#x200B;*jcr:content*&#x200B;屬性&#x200B;**my-custom-template**，並將&#x200B;**cq:cssClass**&#x200B;屬性更新為&#x200B;**aem-Layout my-custom-layout**。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 參考步驟(4)，在步驟中，您複製了左側範本，將在`my-custom-layout/jcr:content`下檢視3個回應式格線。 在&#x200B;*cq:cssClass*&#x200B;屬性中的每個回應式格線中新增自訂CSS類別，例如&#x200B;*my-custom-layout—* r1c1 *節點的左上角*。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同樣地，為&#x200B;*r1c2*&#x200B;添加&#x200B;*my-custom-layout—top-right*，為&#x200B;*r2c1*&#x200B;節點添加&#x200B;*my-custom-layout—bottom*。

   >[!NOTE]
   >這些自訂類別將用於css中，以設定這些回應式格線的寬度/高度。

   >[!NOTE]
   >您可以根據所需的總格數新增或移除回應式格線。 在此示例中，我們展示了第一行中的2個網格和第二行中的1個網格，因此總共有3個響應網格(r1c1、r1c2、r2c1)。

1. 將`/libs/settings/wcm/designs/screens`複製到`/apps/settings/wcm/designs/`，並將複製的設計重新命名為&#x200B;**custom-template-designs**。

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

1. 導覽至`/apps/<project>/templates/my-custom-layout/jcr:content`並將屬性&#x200B;*cq:designPath*&#x200B;更新至`/apps/settings/wcm/designs/customtemplate-designs`以載入static.css中設定的樣式

   >[!NOTE]
   >建議您輸入所有樣式，而非複製或貼上，這可能會導致空格導致CSS樣式問題。

## 查看結果{#viewing-result}

請依照下列步驟，在您的AEM Screens專案中使用上述自訂範本：

1. 導覽至您在步驟(1)中建立的Screens專案，並選取&#x200B;**Channels**&#x200B;資料夾。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 按一下動作列中的&#x200B;**建立**，然後從&#x200B;**建立**&#x200B;精靈中選取範本&#x200B;**Left20-LandscapeHD3Zone**。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 使用自訂範本建立管道後，您就可以從編輯器將資產新增至管道。 下列預覽會顯示自訂範本中的影像。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 將影像插入為背景層{#inserting-image}

您可以將影像插入版面中作為背景圖層：

您可以調整CSS規則，使用所謂的「data-uri」，並直接在CSS檔案中內嵌影像（Base64編碼），您是在（步驟13）*static.css*&#x200B;中建立。

此作法如下：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您可以依照下列步驟操作：

1. 確認影像不知何故包含在通道的離線設定中
1. 使用上述CSS中影像的直接連結，而非「data-uri」變體


## 更新背景顏色{#updating-color}

若要變更背景顏色，請將下列程式碼新增至xml檔案（步驟13）, *static.css*。

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`




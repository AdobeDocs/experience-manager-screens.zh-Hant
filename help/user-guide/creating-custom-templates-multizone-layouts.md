---
title: 在多區域版面配置中建立自訂範本
description: 瞭解如何在MultiZone配置中為AEM Screens建立自訂範本。
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '862'
ht-degree: 1%

---

# 建立MultiZone配置圖的自訂範本 {#creating-custom-templates-multizone}

此頁面說明如何建立多區域版面的自訂範本。

## 重要考量 {#considerations}

以多區域版面配置建立自訂範本之前，您必須注意兩個重要事項：

1. **固定畫素大小或百分比**：

   決定是否要針對自訂配置的不同區域使用固定畫素大小，或是要使用百分比建立自訂配置。

   >[!NOTE]
   >使用百分比來設定自訂配置區域的好處，可讓您在各種熒幕大小上重複使用範本。

1. **命名慣例**：

   它有助於瞭解如何建立自訂多區域範本，以便在AEM Screens專案中使用。 但首先，您必須瞭解要建立的範本的措辭。

   | **配置名稱** | **說明** |
   |---|---|
   | `Left20-LandscapeHD3Zone` | 三區域橫向配置可讓您建立三個區域： <br>*區域1是水準熒幕與垂直熒幕的20%，從左側<br>*區域2是水準熒幕的80%，垂直熒幕的20%是向右對齊<br>*區域3是水準熒幕的100%與垂直熒幕的80%。 外觀比例為16:9 |
   | `Upper20-PortraitHD2Zone` | 雙區直向範本從上到下佔熒幕的20%，外觀比例為16:9 |
   | `Right20-LandscapeSD3Zone` | 三區範本從右側涵蓋熒幕的20%，外觀比例為4:3 |

   >[!IMPORTANT]
   >自訂配置中定義的區域可能與整個配置的整體外觀比例不符。 本檔案遵循的命名慣例會指定自訂配置整體之外觀比例。

## 使用案例`Left20-LandscapeHD3Zone`配置範例 {#custom-template-one}

請依照下列章節內容，使用下列設定來建立自訂範本&#x200B;*`Left20-LandscapeHD3Zone`*：

* **`Left20`** — 左側的頂部區域涵蓋水平與垂直熒幕大小的20%。
* **`Landscape`** — 熒幕方向。
* **`HD`** — 外觀比例為16:9。
* **`3Zone`** — 三個顯示區域。

## 多區域配置的視覺化表示法 {#multi-layout-visual-one}

`Left20-LandscapeHD3Zone`配置可讓您在專案中建立下列多區域配置：

![影像](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## 建立`Left20-LandscapeHD3Zone`配置 {#landscape-layout-one}

請依照下列步驟，為AEM Screens專案建立`Left20-LandscapeHD3Zone`配置。

1. 建立標題為&#x200B;**`customtemplate`**&#x200B;的AEM Screens專案。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. 從您的AEM執行個體> 「工具」 > **CRXDE Lite**&#x200B;瀏覽至&#x200B;**CRXDE Lite**。

1. 在&#x200B;**應用程式**&#x200B;下建立標題為&#x200B;**`customtemplate`**&#x200B;的資料夾。 同樣地，在「**`customtemplate`**」下建立另一個標題為「**範本**」的資料夾，如下圖所示。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >每次建立、編輯內容或將內容複製到任何節點時，按一下CRXDE Lite中動作列的「儲存全部&#x200B;**&#x200B;**」。 否則，您無法認可更新。

1. 將lbar-left範本從`/libs/screens/core/templates/splitscreenchannel/lbar-left`複製到`/apps/customtemplate/template`。

1. 將複製的&#x200B;**lbar-left** (`/apps/customtemplate/template`)重新命名為&#x200B;**my-custom-layout**。
   ![影像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. 瀏覽至`/apps/customtemplate/template/my-custom-layout`並將屬性&#x200B;**`jcr:description`**&#x200B;更新為&#x200B;`Left20-LandscapeHD3Zone`*的*&#x200B;範本及&#x200B;**`jcr:title`**&#x200B;的&#x200B;*`Left20-LandscapeHD3Zone`*。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. 從`/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config`導覽至&#x200B;**`offline-config`**&#x200B;節點，並將&#x200B;**`jcr:title`**&#x200B;更新為&#x200B;*`Left20-LandscapeHD3Zone`*。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. 從`/apps/customtemplate/template/my-custom-layout/jcr:content`瀏覽至&#x200B;**my-custom-template**&#x200B;的&#x200B;*`jcr:content`*&#x200B;屬性，並更新&#x200B;**`cq:cssClass`**&#x200B;屬性，以便您可以使用&#x200B;**aem-Layout my-custom-layout**。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 參考您複製lbar左側範本的步驟(4)，您可以在`my-custom-layout/jcr:content`下檢視三個回應式格線。 在&#x200B;*`cq:cssClass`*&#x200B;屬性中的每個回應式格線中新增自訂css類別，例如&#x200B;*r1c1*&#x200B;節點的&#x200B;*my-custom-layout-top-left*。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同樣地，為&#x200B;*r1c2*&#x200B;新增&#x200B;*my-custom-layout-top-right*，並為&#x200B;*r2c1*&#x200B;節點新增&#x200B;*my-custom-layout-bottom*。

   >[!NOTE]
   >這些自訂類別用於css，以設定這些回應式格點的寬度/高度。

   >[!NOTE]
   >您可以根據所要的格點總數來新增或移除回應式格點。 在此範例中，第一列中有兩個網格，第二列有一個網格，因此總共有三個回應式網格(r1c1、r1c2、r2c1)。

1. 將`/libs/settings/wcm/designs/screens`複製到`/apps/settings/wcm/designs/`，並將複製的設計重新命名為&#x200B;**custom-template-designs**。

1. 瀏覽至`/apps/settings/wcm/designs/custom-template-designs`並將&#x200B;**custom-template-designs**&#x200B;的屬性&#x200B;*`jcr:title`*&#x200B;更新為&#x200B;**customtemplate-design**。

1. 瀏覽至`/apps/settings/wcm/designs/custom-template-designs`並建立檔案static.css。

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
   >您可以更新百分比以符合自訂範本的要求。

1. 導覽至`/apps/<project>/templates/my-custom-layout/jcr:content`並將屬性&#x200B;*`cq:designPath`*&#x200B;更新為`/apps/settings/wcm/designs/customtemplate-designs`，以便載入在static.css中設定的樣式。

   >[!NOTE]
   >輸入所有樣式，而非複製或貼上，因為這樣可能會導致空白字元導致css樣式問題。

## 檢視結果 {#viewing-result}

請依照下列步驟，在您的AEM Screens專案中使用上述自訂範本：

1. 導覽至您在步驟(1)中建立的Screens專案，然後按一下「**管道**」資料夾。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 從動作列按一下&#x200B;**建立**，然後從&#x200B;**建立**&#x200B;精靈按一下範本&#x200B;**`Left20-LandscapeHD3Zone`**。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 使用自訂範本建立管道後，您可以從編輯器將資產新增至管道。 下列預覽會顯示自訂範本中的影像。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 插入影像做為背景圖層 {#inserting-image}

您可以將影像作為背景圖層插入版面：

您可以調整CSS規則以使用&quot;data-uri&quot;，並直接內嵌您於（步驟13） *static.css*&#x200B;中建立之CSS檔案中的影像（`Base64`編碼）。

此安排如下：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您可以遵循下列步驟：

1. 請確定影像以某種方式包含在頻道的離線設定中。
1. 使用上述CSS中影像的直接連結，而非「data-uri」變體。


## 更新背景顏色 {#updating-color}

若要變更背景顏色，請將下列程式碼新增至xml檔案（步驟13），*static.css*。

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`

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
   | `Left20-LandscapeHD3Zone` | 三區域橫向配置可讓您建立三個區域：<br>*區域1是水平與垂直畫面的20% （從左側算起）<br>*區域2為水準熒幕的80%與垂直熒幕的20%向右對齊<br>*區域3是水準熒幕的100%和垂直熒幕的80%。 外觀比例為16:9 |
   | `Upper20-PortraitHD2Zone` | 雙區直向範本從上到下佔熒幕的20%，外觀比例為16:9 |
   | `Right20-LandscapeSD3Zone` | 三區範本從右側涵蓋熒幕的20%，外觀比例為4:3 |

   >[!IMPORTANT]
   >自訂配置中定義的區域可能與整個配置的整體外觀比例不符。 本檔案遵循的命名慣例會指定自訂配置整體之外觀比例。

## 範例使用案例 `Left20-LandscapeHD3Zone` 版面 {#custom-template-one}

請依照以下章節建立自訂範本 *`Left20-LandscapeHD3Zone`* 設定下：

* **`Left20`**  — 左側的頂部區域涵蓋水平與垂直熒幕大小的20%。
* **`Landscape`**  — 熒幕方向。
* **`HD`**  — 外觀比例為16:9。
* **`3Zone`**  — 三個顯示區域。

## 多區域配置的視覺化表示法 {#multi-layout-visual-one}

此 `Left20-LandscapeHD3Zone` 「配置」可讓您在專案中建立下列多區域配置：

![影像](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## 建立 `Left20-LandscapeHD3Zone` 版面 {#landscape-layout-one}

請依照下列步驟建立 `Left20-LandscapeHD3Zone` AEM Screens專案的配置。

1. 建立標題為的AEM Screens專案 **`customtemplate`**.

   ![影像](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. 瀏覽至 **CRXDE Lite** 從您的AEM執行個體>工具> **CRXDE Lite**.

1. 在下建立資料夾 **應用程式** 標題為 **`customtemplate`**. 同樣地，建立另一個名為 **範本** 在 **`customtemplate`**，如下圖所示。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >按一下 **全部儲存** 每次建立、編輯內容或將內容複製到任何節點時，都會從CRXDE Lite中的動作列複製內容。 否則，您無法認可更新。

1. 複製左方欄範本來源 `/libs/screens/core/templates/splitscreenchannel/lbar-left` 至 `/apps/customtemplate/template`.

1. 重新命名複製的 **左欄** (`/apps/customtemplate/template`)至 **my-custom-layout**.
   ![影像](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. 瀏覽至 `/apps/customtemplate/template/my-custom-layout` 並更新屬性 **`jcr:description`** 至 *範本`Left20-LandscapeHD3Zone`* 和 **`jcr:title`** 至 *`Left20-LandscapeHD3Zone`*.

   ![影像](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. 導覽至 **`offline-config`** 節點來源 `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` 並更新 **`jcr:title`** 至 *`Left20-LandscapeHD3Zone`*.

   ![影像](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. 導覽至 *`jcr:content`* 屬性 **my-custom-template** 從 `/apps/customtemplate/template/my-custom-layout/jcr:content` 並更新 **`cq:cssClass`** 屬性，方便您使用 **aem-Layout my-custom-layout**.

   ![影像](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. 參照您複製lbar左側範本的步驟(4)，您可以檢視下方的三個回應式格點 `my-custom-layout/jcr:content`. 將自訂css類別新增至 *`cq:cssClass`* 屬性，例如， *my-custom-layout-top-left* 的 *r1c1* 節點。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template7.png)

   同樣地，新增 *my-custom-layout-top-right* 的 *r1c2* 和 *my-custom-layout-bottom* 的 *r2c1* 節點。

   >[!NOTE]
   >這些自訂類別用於css，以設定這些回應式格點的寬度/高度。

   >[!NOTE]
   >您可以根據所要的格點總數來新增或移除回應式格點。 在此範例中，第一列中有兩個網格，第二列有一個網格，因此總共有三個回應式網格(r1c1、r1c2、r2c1)。

1. 複製 `/libs/settings/wcm/designs/screens` 至 `/apps/settings/wcm/designs/` 並將複製的設計重新命名為 **custom-template-designs**.

1. 瀏覽至 `/apps/settings/wcm/designs/custom-template-designs` 並更新屬性 *`jcr:title`* 之 **custom-template-designs** 至 **customtemplate-design**.

1. 瀏覽至 `/apps/settings/wcm/designs/custom-template-designs` 並建立static.css檔案。

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
   >您可以更新百分比以符合自訂範本的要求。

1. 瀏覽至 `/apps/<project>/templates/my-custom-layout/jcr:content` 並更新屬性 *`cq:designPath`* 至 `/apps/settings/wcm/designs/customtemplate-designs` 以便載入在static.css中設定的樣式。

   >[!NOTE]
   >輸入所有樣式，而非複製或貼上，因為這樣可能會導致空白字元導致css樣式問題。

## 檢視結果 {#viewing-result}

請依照下列步驟，在您的AEM Screens專案中使用上述自訂範本：

1. 導覽至您在步驟(1)中建立的Screens專案，然後按一下 **頻道** 資料夾。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. 按一下 **建立** 然後按一下範本 **`Left20-LandscapeHD3Zone`** 從 **建立** 精靈。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. 使用自訂範本建立管道後，您可以從編輯器將資產新增至管道。 下列預覽會顯示自訂範本中的影像。

   ![影像](/help/user-guide/assets/custom-multizone/custom-template10.png)

## 插入影像做為背景圖層 {#inserting-image}

您可以將影像作為背景圖層插入版面：

您可以調整CSS規則以使用「data-uri」並直接內嵌影像(`Base64` (encoded)，位於您於中建立的CSS檔案中（步驟13）， *static.css*.

此安排如下：
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

或者，您可以遵循下列步驟：

1. 請確定影像以某種方式包含在頻道的離線設定中。
1. 使用上述CSS中影像的直接連結，而非「data-uri」變體。


## 更新背景顏色 {#updating-color}

若要變更背景顏色，請將下列程式碼新增至xml檔案（步驟13）， *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`

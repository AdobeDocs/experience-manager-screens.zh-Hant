---
title: 套用文字覆蓋圖的自訂品牌和樣式
description: 瞭解如何在AEM Screens頻道中套用文字覆蓋圖的自訂品牌和樣式。
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 1%

---

# 文字覆蓋圖的自訂品牌和樣式 {#creating-custom-branding-styling}

瞭解如何在AEM Screens頻道中，將文字覆蓋圖套用的自訂品牌和樣式套用至您的資產。

## 建立文字覆蓋圖的自訂品牌和樣式 {#steps-custom-branding}

請依照下列步驟，建立文字覆蓋的自訂品牌和樣式：

1. 建立AEM Screens專案。 此範例透過建立名為的專案來展示功能 **`customstyle`** 和標題為的頻道 **DemoBrand** ，如下圖所示。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 從編輯器中，拖放影像並將文字覆蓋新增至資產。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >若要瞭解如何在管道編輯器中將文字覆蓋新增至您的資產，請參閱 [文字覆蓋](/help/user-guide/text-overlay.md).

1. 從您的AEM執行個體>工具>導覽至CRXDE Lite **CRXDE Lite**.

1. 在中建立自訂設計 `/apps/settings/wcm/designs/<your-project>/`例如，在此案例中，導覽至 `/apps/settings/wcm/designs/customstyle/`

   ![影像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. 建立 *static.css* 並設定下列css規則。 亦顯示為css規則下圖的範例。

   ```shell
    //global styles
    cq-Screens-textOverlay {
    padding: 1em;
    font-size: 3rem;
    line-height: 1em;
     }
    //authoring overrides
   .aem-AuthorLayer-Edit .cq-Screens-textOverlay {
    display: none;
    padding: 0;
    font-size: 1rem;
    }
     // light text variant
    .cq-Screens-textOverlay-color--light {
     background-color: rgba(0, 0, 0, .6);
     }
     // dark text variant
     .cq-Screens-textOverlay-color--dark {
      background-color: rgba(255, 255, 255, .6);
    }
   ```

   ![影像](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. 複製專案的路徑，在此案例中，路徑為 `/apps/settings/wcm/designs/customstyle`.

1. 瀏覽到標題為 **DemoBrand** (在步驟(1)中建立)並選取 **屬性** 從動作列選取頻道後。

1. 導覽至 **進階** 標籤並核取 **設計** 欄位。
   ![影像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >根據預設， **設計** 欄位會顯示指向libs資料夾中設計的路徑。

1. 更新 **設計** 包含專案資料夾路徑的欄位。 在此案例中，它是 `/apps/settings/wcm/designs/customstyle`.

   ![影像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 選取 **儲存並關閉** 以更新設計路徑。

   >[!IMPORTANT]
   >您可以選擇覆蓋現有的Screens範本，依預設插入您自己的設計或完全建立您自己的範本。 如需詳細資訊，請參閱下列步驟。

1. 若要依預設覆蓋現有的Screens範本以插入您自己的設計：

   1. 覆蓋 `/libs/screens/core/templates/sequencechannel` 在 `/apps/screens/core/templates/sequencechannel`.
   1. 修改 *`cq:designPath`* 中的屬性 `/apps/screens/core/templates/sequencechannel/jcr:content` 因此它指向新的設計。

1. 完全建立您自己的範本：
   1. 複製 `/libs/screens/core/templates/sequencechannel` 至 `/apps/customstyle/templates/styled-sequencechannel`.
   1. 修改 *`cq:designPath`* 中的屬性 `/apps/customstyle/templates/styled-sequencechannel/jcr:content` 因此它指向新的設計。


### 更新ACL {#updating-acls}

更新這些設計的ACL，讓播放器可以下載它們。

1. 導覽至使用者管理員，然後選擇 `screens-<project>-devices group` 並賦予其自訂設計路徑的讀取許可權。

1. 提供 `screens-<project>-administrators` 群組讀取及修改此路徑的許可權。

## 檢視結果 {#viewing-the-result}

完成上述步驟後，您可以更新 *statis.css* 檔案來源 **CRXDE Lite** 因此，檢視已新增至資產的文字覆蓋更新。

請依照下列步驟，檢視文字覆蓋的更新設計：

1. 導覽至您的AEM Screens專案，標題為 **`customstyle`** > **頻道** > **DemoBrand**. 選取管道並選取 **編輯** 從動作列移除。

1. 由於您現在已將設計新增至 **設計** 欄位，如上所述，選取 **預覽** 在含有文字覆蓋的影像上檢視目前的樣式。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. 導覽至 *static.css* CRXDE Lite檔案，並新增字型，例如， `font-family: "Lucida Console", Courier, monospace;` 至此檔案，如下所示。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 儲存變更並重新載入預覽時，您會看到文字覆蓋字型的更新，如下圖所示。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 您也可以從移除程式碼的最後兩個區塊 *static.css* 檔案移除文字覆蓋周圍的盒裝樣式。

![影像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 在影像中新增文字覆蓋的預覽中檢視更新的變更。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand11.png)

   現在您已準備好更新您的品牌和新增至資產的文字覆蓋的自訂樣式。

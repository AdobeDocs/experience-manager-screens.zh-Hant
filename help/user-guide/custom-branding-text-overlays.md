---
title: 套用文字覆蓋圖的自訂品牌和樣式
description: 瞭解如何在AEM Screens管道中，為套用至資產的文字覆蓋圖套用自訂品牌和樣式。
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 1%

---

# 文字覆蓋圖的自訂品牌和樣式 {#creating-custom-branding-styling}

瞭解如何在AEM Screens頻道中，針對套用至資產的文字覆蓋圖套用自訂品牌和樣式。

## 建立文字覆蓋圖的自訂品牌和樣式 {#steps-custom-branding}

請依照下列步驟，建立文字覆蓋的自訂品牌和樣式：

1. 建立AEM Screens專案。 此範例透過建立名為&#x200B;**`customstyle`**&#x200B;的專案和標題為&#x200B;**DemoBrand**&#x200B;的頻道來展示功能，如下圖所示。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 從編輯器中，拖放影像並將文字覆蓋新增至資產。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >若要瞭解如何在管道編輯器中將文字覆蓋新增至您的資產，請參閱[文字覆蓋](/help/user-guide/text-overlay.md)。

1. 從您的AEM執行個體>工具> **CRXDE Lite**&#x200B;導覽至CRXDE Lite。

1. 在`/apps/settings/wcm/designs/<your-project>/`中建立自訂設計，例如，在此案例中，瀏覽至`/apps/settings/wcm/designs/customstyle/`

   ![影像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. 建立&#x200B;*static.css*&#x200B;檔案並設定下列css規則。 亦顯示為css規則下圖的範例。

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

1. 複製專案的路徑，在此案例中，路徑為`/apps/settings/wcm/designs/customstyle`。

1. 導覽至標題為&#x200B;**DemoBrand** (在步驟(1)中建立)的頻道，然後在選取頻道後，從動作列按一下&#x200B;**內容**。

1. 導覽至&#x200B;**進階**&#x200B;標籤，並檢查&#x200B;**設計**&#x200B;欄位。
   ![影像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >根據預設，**設計**&#x200B;欄位會顯示指向libs資料夾中設計的路徑。

1. 以您的專案資料夾的路徑更新&#x200B;**設計**&#x200B;欄位。 在此案例中，它是`/apps/settings/wcm/designs/customstyle`。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 按一下&#x200B;**儲存並關閉**&#x200B;以更新設計路徑。

   >[!IMPORTANT]
   >您可以選擇覆蓋現有的Screens範本，依預設來插入您自己的設計或完全建立您自己的範本。 如需詳細資訊，請參閱下列步驟。

1. 若要依預設覆蓋現有的Screens範本以插入您自己的設計：

   1. 覆蓋`/apps/screens/core/templates/sequencechannel`中的`/libs/screens/core/templates/sequencechannel`。
   1. 修改`/apps/screens/core/templates/sequencechannel/jcr:content`中的&#x200B;*`cq:designPath`*&#x200B;屬性，使其指向新的設計。

1. 完全建立您自己的範本：
   1. 將`/libs/screens/core/templates/sequencechannel`複製到`/apps/customstyle/templates/styled-sequencechannel`。
   1. 修改`/apps/customstyle/templates/styled-sequencechannel/jcr:content`中的&#x200B;*`cq:designPath`*&#x200B;屬性，使其指向新的設計。


### 更新ACL {#updating-acls}

更新這些設計的ACL，讓播放器可以下載。

1. 導覽至使用者管理員，並選擇`screens-<project>-devices group`並授予其自訂設計路徑的讀取許可權。

1. 提供`screens-<project>-administrators`群組對此路徑的讀取和修改許可權。

## 檢視結果 {#viewing-the-result}

完成上述步驟後，您可以從&#x200B;**CRXDE Lite**&#x200B;更新&#x200B;*statis.css*&#x200B;檔案，檢視已新增至資產的文字覆蓋更新。

請依照下列步驟，檢視文字覆蓋的更新設計：

1. 導覽至您標題為「**`customstyle`** > **管道** > **示範品牌**」的AEM Screens專案。 按一下頻道，然後從動作列按一下&#x200B;**編輯**。

1. 由於您現在已將設計新增至您的&#x200B;**設計**&#x200B;欄位，如上所述，請按一下&#x200B;**預覽**&#x200B;以檢視含文字覆蓋的影像上的目前樣式。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. 導覽至您在CRXDE Lite中的&#x200B;*static.css*&#x200B;檔案，然後將`font-family: "Lucida Console", Courier, monospace;`等字型新增至此檔案，如下所示。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 儲存變更並重新載入預覽時，您會看到文字覆蓋字型的更新，如下圖所示。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 您也可以從&#x200B;*static.css*&#x200B;檔案中移除最後兩個程式碼區塊，以移除文字覆蓋周圍的盒裝樣式。

![影像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 在影像中新增文字覆蓋的預覽中檢視更新的變更。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand11.png)

   現在，您已準備好更新您的品牌和新增至資產的文字覆蓋的自訂樣式。

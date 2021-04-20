---
title: 為文字覆蓋套用自訂品牌和樣式
seo-title: 為文字覆蓋套用自訂品牌和樣式
description: 請依照本頁進行，瞭解如何針對「文字覆蓋」套用自訂品牌和樣式。
seo-description: 請依照本頁進行，瞭解如何針對「文字覆蓋」套用自訂品牌和樣式。
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 1%

---


# 文字覆蓋的自訂品牌與樣式{#creating-custom-branding-styling}

請依照本頁進行，瞭解如何針對套用至AEM Screens頻道資產的文字覆蓋套用自訂品牌和樣式。

## 建立文字覆蓋的自訂品牌與樣式{#steps-custom-branding}

請依照下列步驟，為文字覆蓋建立自訂品牌和樣式：

1. 建立AEM Screens專案。 此範例會建立名為&#x200B;**customstyle**&#x200B;的專案和名為&#x200B;**DemoBrand**&#x200B;的頻道，以展示其功能，如下圖所示。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 從編輯器拖放影像，並新增文字覆蓋至資產。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >若要瞭解如何在頻道編輯器中將文字覆蓋新增至資產，請參閱[文字覆蓋](/help/user-guide/text-overlay.md)。

1. 從實例AEM—>工具—> **CRXDE Lite**&#x200B;導航到CRXDE Lite。

1. 您必須在`/apps/settings/wcm/designs/<your-project>/`中建立自訂設計，例如，在此例中，導覽至`/apps/settings/wcm/designs/customstyle/`

   ![影像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. 建立&#x200B;*static.css*&#x200B;檔案並設定下列css規則。 另外，在css規則下方的圖中也顯示為範例。

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

1. 複製專案的路徑，在本例中，路徑為`/apps/settings/wcm/designs/customstyle`。

1. 導覽至標題為&#x200B;**DemoBrand**&#x200B;的頻道(在步驟(1)中建立)，並在選取頻道後，從動作列按一下&#x200B;**屬性**。

1. 導覽至「**進階**」標籤，並勾選「**設計**」欄位。
   ![影像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >若為預設值，**Design**&#x200B;欄位會顯示指向libs資料夾中設計的路徑。

1. 使用專案資料夾的路徑更新&#x200B;**Design**&#x200B;欄位。 在這種情況下，它將是`/apps/settings/wcm/designs/customstyle`。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 按一下「儲存並關閉」以更新設計路徑。****

   >[!IMPORTANT]
   >您可以選擇覆蓋現有的「畫面」範本，依預設插入您自己的設計，或完全建立您自己的範本。 請參閱以下步驟以取得詳細資訊。

1. 若要覆蓋現有的「畫面」範本，以依預設插入您自己的設計：

   1. 覆蓋`/apps/screens/core/templates/sequencechannel`中的`/libs/screens/core/templates/sequencechannel`。
   1. 修改`/apps/screens/core/templates/sequencechannel/jcr:content`中的&#x200B;*cq:designPath*&#x200B;屬性，以指向新設計。

1. 要完全建立您自己的模板，請執行以下操作：
   1. 將`/libs/screens/core/templates/sequencechannel`複製到`/apps/customstyle/templates/styled-sequencechannel`。
   1. 修改`/apps/customstyle/templates/styled-sequencechannel/jcr:content`中的&#x200B;*cq:designPath*&#x200B;屬性，以指向新設計。


### 更新ACL {#updating-acls}

您必須更新這些設計的ACL，以便播放器下載。

1. 導覽至使用者管理員並選擇`screens-<project>-devices group`，並授予其自訂設計路徑的讀取權限。

1. 提供`screens-<project>-administrators`群組讀取和修改此路徑的權限。

## 查看結果{#viewing-the-result}

完成上述步驟後，您就可以從&#x200B;**CRXDE Lite**&#x200B;更新&#x200B;*statis.css*&#x200B;檔案，然後檢視已新增至資產的文字覆蓋的更新。

請依照下列步驟，檢視文字覆蓋的更新設計：

1. 導覽至您的AEM Screens專案，標題為&#x200B;**customstyle** —> **Channels** —> **DemoBrand**。 選擇該通道，然後按一下操作欄中的&#x200B;**編輯**&#x200B;以開啟編輯器。

1. 由於您現在已將設計新增至&#x200B;**Designs**&#x200B;欄位，如上所述，請按一下&#x200B;**Preview**&#x200B;以檢視包含文字覆蓋的影像上的目前樣式。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. 導覽至CRXDE Lite中的&#x200B;*static.css*&#x200B;檔案，並將字型（例如`font-family: "Lucida Console", Courier, monospace;`）新增至此檔案，如下所示。
   ![影像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 儲存變更並重新載入預覽後，您會看到文字覆蓋字型的更新，如下圖所示。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 此外，您也可以從&#x200B;*static.css*檔案移除最後兩個程式碼區塊，以移除文字覆蓋周圍的盒裝樣式。
   ![影像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 您將在預覽中檢視更新的變更，將文字覆蓋新增至影像。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand11.png)

   現在，您已準備好更新您的品牌及自訂樣式，以便將文字覆蓋新增至資產。










---
title: 為文字覆蓋套用自訂品牌和樣式
seo-title: 為文字覆蓋套用自訂品牌和樣式
description: 請依照本頁進行，瞭解如何針對「文字覆蓋」套用自訂品牌和樣式。
seo-description: 請依照本頁進行，瞭解如何針對「文字覆蓋」套用自訂品牌和樣式。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 835e801909d8d126042acd713fc68075ff598712

---


# 文字覆蓋的自訂品牌與樣式 {#creating-custom-branding-styling}

請依照本頁進行，瞭解如何針對套用至「畫面」頻道中資產的「文字覆蓋」套用自訂品牌和樣式。

## 建立文字覆蓋的自訂品牌與樣式 {#steps-custom-branding}

請依照下列步驟，為文字覆蓋建立自訂品牌和樣式：

1. 建立標題為自訂樣式的AEM Screens專 **案** ，以及標題為 **** DemoBrand的頻道，如下圖所示。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 從編輯器拖放影像，並新增文字覆蓋至資產。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >若要瞭解如何在頻道編輯器中將文字覆蓋新增至資產，請參閱「文 [字覆蓋」](/help/user-guide/text-overlay.md)。

1. 從您的AEM例項—>工具—> **CRXDE Lite導覽至CRXDE Lite**。

1. 您必須建立自訂設 `/apps/settings/wcm/designs/<your-project>/`計，例如，在本例中，導覽至 `/apps/settings/wcm/designs/customstyle/`

   ![影像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. 導覽至 *static.css檔案* ，並設定下列css規則。 另外，在css規則下方的圖中也顯示為範例。

   ```shell
    //global styles
    .cq-Screens-textOverlay
    { … }
    //authoring overrides
    .aem-AuthorLayer-Edit .cq-Screens-textOverlay { … }
    // light text variant
    .cq-Screens-textOverlay-color--light
    { … }
     // dark text variant
    .cq-Screens-textOverlay-color--dark { … }
   ```
   ![影像](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. 將路徑複製到您的專案中，此時路徑為 `/apps/settings/wcm/designs/customstyle`。

1. 導覽至標題為 **DemoBrand** (在步驟(1)中建立)的頻道，並在選取頻道後，從動作列按一下「 **Properties** 」（屬性）。

1. 導覽至「進 **階** 」索引標籤，並勾 **選「設計** 」欄位。
   ![影像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >若為預設值， **「設計** 」欄位會顯示指向libs資料夾中設計的路徑。

1. 使用專案 **資料夾的路徑** ，更新「設計」欄位。 在這種情況下，會是， `/apps/settings/wcm/designs/customstyle`。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 按一 **下「儲存並關閉** 」以更新設計路徑。


## 查看結果 {#viewing-the-result}

完成上述步驟後，您就可以從 *CRXDE Lite***** ，更新statis.css檔案，然後檢視已新增至資產的文字覆蓋更新。

請依照下列步驟，檢視文字覆蓋的更新設計：

1. 導覽至您的AEM Screens專案，標題為 **customstyle** —> **Channels** —> **DemoBrand**。 選取渠道，然後從動 **作列按一下** 「編輯」以開啟編輯器。

1. 由於您現在已將設計新增至「設計」欄 **位** （如上所述），請按一下「 **Preview** 」（預覽），以檢視包含文字覆蓋的影像上目前的樣式。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. 導覽至CRXDE *Lite中的static.css* 檔案，並將字型（例如）新增至 `font-family: "Lucida Console", Courier, monospace;` 此檔案，如下所示。
   ![影像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 儲存變更並重新載入預覽後，您會看到文字覆蓋字型的更新，如下圖所示。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 此外，您也可以從 *static.css檔案移除最後兩個程式碼區塊* ，以移除文字覆蓋周圍的盒裝樣式。
   ![影像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 您將在預覽中檢視更新的變更，將文字覆蓋新增至影像。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand11.png)

參照教學課程，您現在可以更新您的品牌和自訂樣式，以便將文字覆蓋新增至資產。










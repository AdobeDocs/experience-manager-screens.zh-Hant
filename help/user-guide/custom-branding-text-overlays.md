---
title: 為文本覆蓋應用自定義品牌和樣式
seo-title: Applying Custom Branding and Styling for Text Overlays
description: 按照本頁瞭解如何為文本覆蓋應用自定義品牌和樣式。
seo-description: Follow this page to learn how to apply custom branding and styling for Text Overlays.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 1%

---

# 文本疊加的自定義品牌和樣式 {#creating-custom-branding-styling}

請按照本頁瞭解如何將自定義品牌和樣式應用於AEM Screens渠道中的資產的文本覆蓋。

## 為文本疊加建立自定義品牌和樣式 {#steps-custom-branding}

按照以下步驟為文本疊加建立自定義品牌和樣式：

1. 建立AEM Screens項目。 此示例通過建立名為 **自定義樣式** 以及一個 **演示品牌** ，如下圖所示。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. 在編輯器中拖放影像，並將文本覆蓋添加到資源。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >要瞭解如何在渠道編輯器中將文本覆蓋添加到資產中，請參閱 [文本覆蓋](/help/user-guide/text-overlay.md)。

1. 從實例導航到AEMCRXDE Lite—>工具 — > **CRXDE Lite**。

1. 您必須在 `/apps/settings/wcm/designs/<your-project>/`例如，在本例中，導航到 `/apps/settings/wcm/designs/customstyle/`

   ![影像](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. 建立 *static.css* 並設定以下css規則。 另示為css規則下圖的示例。

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

1. 將路徑複製到項目，在這種情況下，路徑將 `/apps/settings/wcm/designs/customstyle`。

1. 導航到標題為 **演示品牌** (在步驟(1)中建立)，然後按一下 **屬性** 的下界。

1. 導航到 **高級** 的子菜單。 **設計** 的子菜單。
   ![影像](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >如果為預設， **設計** 欄位顯示指向libs資料夾中設計的路徑。

1. 更新 **設計** 的子菜單。 在這種情況下， `/apps/settings/wcm/designs/customstyle`。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. 按一下 **保存並關閉** 更新設計路徑。

   >[!IMPORTANT]
   >您可以選擇覆蓋現有的螢幕模板，以在預設情況下注入您自己的設計或完全建立您自己的模板。 有關詳細資訊，請參閱以下步驟。

1. 要覆蓋現有螢幕模板以在預設情況下注入您自己的設計：

   1. 覆蓋 `/libs/screens/core/templates/sequencechannel` 在 `/apps/screens/core/templates/sequencechannel`。
   1. 修改 *cq:designPath* 物業 `/apps/screens/core/templates/sequencechannel/jcr:content` 指向新設計。

1. 要完全建立您自己的模板，請執行以下操作：
   1. 複製 `/libs/screens/core/templates/sequencechannel` 至 `/apps/customstyle/templates/styled-sequencechannel`。
   1. 修改 *cq:designPath* 物業 `/apps/customstyle/templates/styled-sequencechannel/jcr:content` 指向新設計。


### 更新ACL {#updating-acls}

您必須更新這些設計的ACL，以便播放器可以下載它們。

1. 導航到用戶管理員並選擇 `screens-<project>-devices group` 並賦予它對自定義設計路徑的讀取權限。

1. 提供 `screens-<project>-administrators` 對此路徑進行組讀取和修改權限。

## 查看結果 {#viewing-the-result}

完成上述步驟後，您可以更新 *statis.css* 檔案 **CRXDE Lite** 然後查看已添加到資產的文本覆蓋的更新。

按照以下步驟查看更新後的設計以覆蓋文本：

1. 導航到您的AEM Screens項目，標題為 **自定義樣式** —> **頻道** —> **演示品牌**。 選擇頻道並按一下 **編輯** 的子菜單。

1. 因為您現在已將設計添加到 **設計** 欄位，按一下 **預覽** 查看影像上具有文本覆蓋的當前樣式。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. 導航到 *static.css* 檔案，並添加字型，如 `font-family: "Lucida Console", Courier, monospace;` 檔案，如下所示。
   ![影像](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. 保存更改並重新載入預覽後，將看到對文本覆蓋字型的更新，如下圖所示。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. 另外，您可以從 *static.css* 檔案，以刪除文本覆蓋周圍的盒裝樣式。
   ![影像](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. 您將在預覽中查看將文本覆蓋添加到影像的更新更改。

   ![影像](/help/user-guide/assets/custom-brand/custom-brand11.png)

   現在，您已準備好更新您的品牌和自定義樣式，以便將文本疊加添加到資產中。

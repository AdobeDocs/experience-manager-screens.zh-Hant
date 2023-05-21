---
title: 在AEM Screens配置ContextHub
seo-title: Configuring ContextHub in AEM Screens
description: 按照此頁瞭解目標引擎中的ContextHub，以定義資料儲存以用於資料觸發內容更改。
seo-description: Follow this page to learn about ContextHub in the targeting engine to define data store for the purpose of data trigger content change.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 1%

---

# 在AEM Screens配置ContextHub {#configuring-contexthub-in-aem-screens}

本節著重介紹使用資料儲存建立和管理資料驅動的資產更改。

## 關鍵術語 {#key-terms}

在我們瞭解在您的AEM Screens項目中建立和管理庫存驅動渠道的詳細資訊之前，您必須瞭解與不同方案相關的重要關鍵術語。

**品牌** 參考您的高級項目描述。

**區域** 指您的AEM Screens項目名稱，如數字廣告標牌

**活動** 定義規則類別，如庫存驅動、天氣驅動、部門可用性驅動等。

**觀眾** 定義規則。

**段** 指為給定規則播放的資產版本，例如，如果溫度低於華氏50度，則螢幕將顯示熱咖啡的影像，否則顯示冷飲。

下圖提供了ContextHub配置如何與「活動」、「受眾」和「渠道」重合的可視表示。

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 先決條件 {#preconditions}

在開始為AEM Screens項目配置上下文中心配置之前，必須設定Google工作表（用於演示目的）。

>[!IMPORTANT]
>
>Google工作表在以下示例中用作獲取值的示例資料庫系統，並僅用於教育目的。 Adobe不贊成將Google產品介紹用於生產環境。
>
>有關詳細資訊，請參閱 [獲取API密鑰](https://developers.google.com/maps/documentation/javascript/get-api-key) 在Google檔案中。

## 步驟1:設定資料儲存 {#step-setting-up-a-data-store}

可以將資料儲存設定為本地I/O事件或本地資料庫事件。

以下資產級資料觸發器示例展示了本地資料庫事件，該事件設定資料儲存，如Excel工作表，允許您使用ContextHub配置和段到AEM Screens通道的路徑。

一旦正確設定了google工作表，如下所示：

![影像](/help/user-guide/assets/context-hub/context-hub1.png)

以下驗證是通過輸入兩個值檢查連接時將查看的內容。 *谷歌表ID* 和 *API密鑰* 的下界：

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![影像](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>下面的具體示例將google工作表顯示為資料儲存，如果值高於100或小於50，則會觸發資產更改。

## 步驟2:設定儲存配置 {#step-setting-store-configurations}

1. **導航到ContextHub**

   導航到實AEM例，然後從左側提要欄按一下工具表徵圖。 按一下 **站點** —> **上下文中心**，如下圖所示。

   ![影像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **建立新的ContextHub儲存配置**

   1. 導航到標題為「」的配置容器 **螢幕**。

   1. 按一下 **建立** > **建立配置容器** 並輸入標題為 **上下文集演示**。

      ![影像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **導航** 至 **上下文集演示** > **建立** **ContentHub配置** 按一下 **保存**。

      >[!NOTE]
      > 按一下後 **保存** 你會在 **ContextHub配置** 的上界。

   1. 從 **ContextHub配置** 螢幕，按一下 **建立** > **ContentHub儲存配置……**

      ![影像](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >
      >作為6AEM.5功能包4或6.4功AEM能包8的一部分，客戶應更新 `/conf/screens/settings/cloudsettings` 至 `sling:Folder`。
      >
      >請遵循下列步驟：
      >
      >1. 導航到CRXDE Lite，然後導航到 `/conf/screens/settings/cloudsettings`。
      >1. 檢查 `cloudsettings jcr:primaryType` 在 `sling:Folder`。 如果 `jcr:primaryType` 不在 `sling:folder`，繼續執行後續步驟。
      >1. 按一下右鍵 `/conf/screens/settings` 建立新節點 *名稱*  如 **雲設定1** 和 *類型* 如 **sling：資料夾** 並保存更改。
      >1. 將所有節點 `/conf/screens/settings/cloudsettings` 至 `cloudsettings1`。
      >1. 刪除 `cloudsettings` 然後保存。
      >1. 更名 `cloudsettings1` 至 `cloudsettings` 然後保存。
      >1. 您現在應該注意/conf/screens/settings/cloudsettings `jcr:primaryType` 如 `sling:Folder`。

      >
      >您應在升級之前或之後執行這些步驟並發佈。

   1. 輸入 **標題** 如 **Google·謝特**。 **儲存名稱** 如 **谷歌表**, **儲存類型** 如 **contexthub.generic.jsonp** 按一下 **下一個**。

      >[!CAUTION]
      >如果您使用Adobe Experience Manager(AEM)6.4，請輸入 **配置標題** 如 **谷歌表** 和 **儲存類型** 如 **contexthub.generic.jsonp**。

      ![影像](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 輸入您的特定json配置。 例如，您可以使用以下json進行演示，然後按一下 **保存** 您將看到名為 **Google·謝特** 中。

      >[!IMPORTANT]
      >確保將代碼替換為 *&lt;sheet id=&quot;&quot;>* 和 *&lt;api key=&quot;&quot;>*&#x200B;你在設定Google床單時取的。

      ```
       {
        "service": {
        "host": "sheets.googleapis.com",
        "port": 80,
        "path": "/v4/spreadsheets/<your google sheets id>/values/Sheet1",
        "jsonp": false,
        "secure": true,
        "params": {
        "key": "<your Google API key>"
       }
      },
      "pollInterval": 10000
      }
      ```

      >[!NOTE]
      在上面的示例代碼中， **輪詢間隔** 定義刷新值的頻率（毫秒）。
      將代碼替換為 *&lt;sheet id=&quot;&quot;>* 和 *&lt;api key=&quot;&quot;>*&#x200B;你在設定Google床單時取的。

      >[!CAUTION]
      如果您在全局資料夾之外建立了「Google工作表」儲存配置（例如在您自己的項目資料夾中），則目標將不會在開箱後生效。

1. **設定儲存分段**

   1. 導航到 **ContentHub儲存配置……** 並在螢幕配置容器中建立另一個儲存配置，並設定 **標題** 如 **分段上下文**。 **儲存名稱** 如 **分割** 和 **儲存類型** 如 **aem分割**。

      ![影像](/help/user-guide/assets/context-hub/context-hub7.png)

   1. 按一下 **下一個** 然後 **保存**。

      >[!NOTE]
您必須跳過定義json的過程，將其留空。


## 第3步：在受眾中設定段 {#setting-up-audience}

1. **在受眾中建立段**

   1. 從實例導AEM航到 **個性化** > **觀眾** > **螢幕**。

   1. 按一下 **建立** > **建立上下文中心段。** 的 **新建ContextHub段** 對話框。

   1. 輸入 **標題** 如 **50以上** 按一下 **建立**。 同樣，建立另一個標題為 **低於50**。

      ![影像](/help/user-guide/assets/context-hub/context-hub11.png)

   1. 選擇段 **50以上** 按一下 **屬性** 按鈕。
      ![影像](/help/user-guide/assets/context-hub/context-hub12.png)

   1. 選擇 **個性化** 的 **段屬性**。 設定 **上下文中心路徑** 至 `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` 和 **段路徑** 至 `/conf/screens/settings/wcm/segments` 按一下 **保存**，如下圖所示。

      ![影像](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 同樣，設定 **上下文中心路徑** 和 **段路徑** 為 **低於50** 段。

## 第4步：設定品牌和區域 {#setting-brand-area}

按照以下步驟在您的活動和品牌下建立品牌：

1. **在活動中建立品牌**

   1. 從實例導AEM航到 **個性化** > **活動**。

   1. 按一下 **建立** > **建立品牌**。

   1. 選擇 **品牌** 從 **建立頁** 嚮導 **下一個**。

   1. 輸入 **標題** 如 **螢幕品牌** 按一下 **建立**。 您的品牌現已建立，如下所示。

      ![影像](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      已知問題：要添加區域，請從URL中刪除主節點，如
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`。

1. **在品牌中建立區域**

   按照以下步驟在品牌中建立區域：

   1. 按一下 **建立** 然後 **建立區域**。

      ![影像](/help/user-guide/assets/context-hub/context-hub9.png)

   1. 選擇 **區域** 從 **建立頁** 嚮導 **下一個**。

   1. 輸入 **標題** 如 **螢幕值** 按一下 **建立**。
將在您的品牌中建立區域。

## 第5步：在活動中建立段 {#step-setting-up-audience-segmentation}

設定資料儲存並定義活動（品牌和區域）後，請按照以下步驟在活動中建立段。

1. **在活動中建立段**

   1. 從實例導AEM航到 **個性化** > **活動** > **螢幕品牌** >**螢幕值**。

   1. 按一下 **建立** > **建立活動。** 的 **配置活動嚮導** 的上界。

   1. 輸入 **標題** 如 **值檢查50** 和 **名稱** 如 **值檢查50**。 選擇 **目標引擎** 如 **上下文集AEM()** 下拉框中，按一下 **下一個**。

      ![影像](/help/user-guide/assets/context-hub/context-hub14.png)

   1. 按一下 **添加體驗** 從 **配置活動嚮導**。

   1. 從 **觀眾**，選擇 **50以上** 按一下 **添加體驗** 輸入 **標題** 如 **高於50** **名稱** 如 **高於50**。 按一下 **確定**。

   1. 從 **觀眾**，選擇 **低於50** 按一下 **添加體驗** 輸入 **標題** 如 **低於50** **名稱** 如 **低於50**。 按一下 **確定**。

      ![影像](/help/user-guide/assets/context-hub/context-hub15.png)

   1. 按一下 **下一個** 然後 **保存**。 **值檢查50** 活動現在已建立和配置。

      ![影像](/help/user-guide/assets/context-hub/context-hub16.png)

## 第5步：編輯受眾中的段{#editing-audience-segmentation}

1. **編輯段**

   1. 從實例導AEM航到 **個性化** > **觀眾** > **螢幕**。

   1. 選擇段 **50以上**，然後按一下 **編輯** 按鈕。

   1. 拖放 **比較：屬性 — 值** 元件。

   1. 按一下扳手錶徵圖以開啟 **將屬性與值進行比較** 對話框。

   1. 選擇 **谷歌表/值/1/0** 從 **屬性名稱**。

      >[!NOTE]
的 **谷歌表/值/1/0** 指下圖中google工作表中填寫的行2和列：

      ![影像](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 選擇 **運算子** 如 **大於** 的下界。

   1. 輸入 **值** 如 **70**。

      >[!NOTE]
      通過AEM將段顯示為綠色來驗證來自Google工作表的資料。

      ![影像](/help/user-guide/assets/context-hub/context-hub18.png)
   同樣，編輯屬性值以 **低於50**。

   1. 拖放 **比較：屬性 — 值** 元件。

   1. 按一下扳手錶徵圖以開啟 **將屬性與值進行比較** 對話框。

   1. 選擇 **谷歌表/值/1/0** 從 **屬性名稱**。

   1. 選擇 **運算子** 如 **小於** 的下界。

   1. 輸入 **值** 如 **50**。



## 在渠道中啟用目標 {#step-enabling-targeting-in-channels}

按照以下步驟在您的渠道中啟用目標。

1. 導航到其中一個AEM Screens頻道。 以下步驟演示如何使用 **資料驅動通道** 在AEM Screens頻道創作。

1. 選擇頻道 **目標通道** 按一下 **屬性** 按鈕。

   ![影像](/help/user-guide/assets/context-hub/context-hub19.png)

1. 選擇 **個性化** 頁籤。

   1. 設定 **上下文中心路徑** 至 `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` 和 **段路徑** 至 `/conf/screens/settings/wcm/segments` 按一下 **保存**。

   1. 按一下&#x200B;**「儲存並關閉」**。

      >[!NOTE]
      使用ContextHub和Segments路徑，在其中您最初保存了上下文中心配置和段。

      ![影像](/help/user-guide/assets/context-hub/context-hub20.png)

   1. 導航並選擇 **目標通道** 按一下 **編輯** 按鈕。

      >[!NOTE]
      如果您已正確設定所有內容，您將看到 **目標** 的子菜單。

      ![影像](/help/user-guide/assets/context-hub/context-hub21.png)

## 瞭解詳情：示例使用案例 {#learn-more-example-use-cases}

在為AEM Screens項目配置ContextHub後，您可以按照不同的使用案例來瞭解資料觸發的資產如何在不同的行業中扮演關鍵角色：

1. **[零售庫存目標激活](retail-inventory-activation.md)**
1. **[旅行中心溫度激活](local-temperature-activation.md)**
1. **[酒店預訂激活](hospitality-reservation-activation.md)**

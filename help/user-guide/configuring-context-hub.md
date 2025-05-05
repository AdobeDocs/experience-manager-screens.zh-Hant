---
title: 在AEM Screens中設定ContextHub
description: 瞭解定位引擎中的ContextHub，讓您能夠為資料觸發內容變更定義資料存放區。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '1450'
ht-degree: 1%

---

# 在AEM Screens中設定ContextHub {#configuring-contexthub-in-aem-screens}

本節著重於使用資料存放區建立和管理資料導向資產變更。

## 主要條款 {#key-terms}

在您開始瞭解在AEM Screens專案中建立和管理庫存導向管道的詳細資訊之前，請先瞭解不同情境的一些關鍵術語。

**品牌** — 您的高階專案說明。

**區域** — 您的AEM Screens專案名稱，例如數位廣告招牌

**活動** — 定義類別規則，例如庫存導向、天氣導向或部門可用性導向。

**對象** — 定義規則。

**區段** — 要針對指定規則播放的資產版本。 例如，如果溫度低於華氏50度，則熒幕會顯示熱飲的影像，否則會顯示冷飲。

下圖以視覺化方式呈現ContextHub設定與「活動」、「對象」和「管道」的對應情形。

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 先決條件 {#preconditions}

開始為AEM Screens專案設定ContextHub設定前，請先設定Google Sheets （以供示範之用）。

>[!IMPORTANT]
>
>在下列範例中，Google Sheets是作為範例資料庫系統使用，其值會從中擷取，且僅供教育用途。 Adobe不認可將Google Sheets用於生產環境。
>
>如需詳細資訊，請參閱Google檔案中的[取得API金鑰](https://developers.google.com/maps/documentation/javascript/get-api-key)。

## 步驟1：設定資料存放區 {#step-setting-up-a-data-store}

您可以將資料存放區設定為本機I/O事件或本機資料庫事件。

下列資產層級資料觸發器範例會示範本機資料庫事件。 事件會設定資料存放區（例如Excel工作表），供您使用ContextHub設定和AEM Screens通道的區段路徑。

正確設定`google`工作表之後，如下列範例所示：

![影像](/help/user-guide/assets/context-hub/context-hub1.png)

以下為檢查連線時所檢視的驗證內容，方法是以下列格式輸入兩個值： `*google sheet ID*`和`*API key*`：

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![影像](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>以下特定範例將Google工作表示範為當值高於100或低於50時觸發資產變更的資料存放區。

## 步驟2：設定存放區設定 {#step-setting-store-configurations}

1. **瀏覽至ContextHub**

   導覽至您的AEM執行個體，然後按一下左側邊欄中的工具圖示。 按一下「**網站**」>「**ContextHub**」，如下圖所示。

   ![影像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **正在建立ContextHub存放區組態**

   1. 導覽至標題為&#x200B;**熒幕**&#x200B;的設定容器。

   1. 按一下「**建立**」>「**建立設定容器**」，然後輸入標題為&#x200B;**ContextHubDemo**。

      ![影像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **瀏覽**&#x200B;至&#x200B;**ContextHubDemo** > **建立** **ContentHub設定**，然後按一下&#x200B;**儲存**。

      >[!NOTE]
      > 按一下&#x200B;**儲存**&#x200B;之後，您就會進入&#x200B;**ContextHub組態**&#x200B;畫面。

   1. 在&#x200B;**ContextHub設定**&#x200B;畫面中，按一下&#x200B;**建立** > **ContentHub存放區設定**

   ![影像](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >在AEM 6.5 Feature Pack 4或AEM 6.4 Feature Pack 8中，客戶應將`/conf/screens/settings/cloudsettings`更新為`sling:Folder`。
   >
   >請遵循下列步驟：
   >
   >1. 導覽至CRXDE Lite，然後導覽至`/conf/screens/settings/cloudsettings`。
   >1. 檢查`cloudsettings jcr:primaryType`是否在`sling:Folder`中。 如果`jcr:primaryType`不在`sling:folder`中，請繼續後續步驟。
   >1. 用滑鼠右鍵按一下`/conf/screens/settings`並建立具有&#x200B;*名稱*&#x200B;的節點做為&#x200B;**`cloudsettings1`**，*型別*&#x200B;做為&#x200B;**`sling:Folder`**，並儲存變更。
   >1. 將`/conf/screens/settings/cloudsettings`下的所有節點移至`cloudsettings1`。
   >1. 刪除`cloudsettings`並儲存。
   >1. 將`cloudsettings1`重新命名為`cloudsettings`並儲存。
   >1. 請注意，`/conf/screens/settings/cloudsettings`有`jcr:primaryType`做為`sling:Folder`。
   >
   >在升級之前或之後，請依照作者和Publish中的這些步驟操作。

   1. 輸入&#x200B;**標題**&#x200B;作為&#x200B;**Google工作表**，**儲存名稱**&#x200B;作為&#x200B;**`googlesheets`**，且&#x200B;**儲存型別**&#x200B;作為&#x200B;**c`ontexthub.generic-jsonp`**，然後按一下&#x200B;**下一步**。

      >[!CAUTION]
      >如果您使用Adobe Experience Manager (AEM) 6.4，請輸入&#x200B;**設定標題**&#x200B;作為&#x200B;**`googlesheets`**，並輸入&#x200B;**存放區型別**&#x200B;作為&#x200B;**c`ontexthub.generic-jsonp`**。

      ![影像](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 輸入您專屬的json設定。 例如，您可以使用以下json進行示範，然後按一下&#x200B;**儲存**。 您會在ContextHub設定中看到標題為&#x200B;**Google工作表**&#x200B;的存放區設定。

      >[!IMPORTANT]
      >請務必以您在設定Google工作表時擷取的`*<Sheet ID>*`和`*<API Key>*`取代代碼。

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
      >
      >在上述範常式式碼中，**pollInterval**&#x200B;定義重新整理值的頻率（毫秒）。
      >
      >將程式碼取代為您在設定Google工作表時擷取的`*<Sheet ID>*`和`*<API Key>*`。

      >[!CAUTION]
      >
      >如果您建立Google工作表來將設定儲存於全域資料夾之外（例如，在您自己的專案資料夾中），則定位無法立即運作。

1. **設定商店分段**

   1. 導覽至&#x200B;**ContentHub存放區組態**，並在AEM Screens組態容器中建立另一個存放區組態，並將&#x200B;**Title**&#x200B;設定為&#x200B;**segmentation-contexthub**，**存放區名稱**&#x200B;設定為&#x200B;**segmentation**，並將&#x200B;**存放區型別**&#x200B;設定為&#x200B;**aem.segmentation**。

      ![影像](/help/user-guide/assets/context-hub/context-hub7.png)

   1. 按一下[下一步]&#x200B;**&#x200B;**，然後按一下[儲存]&#x200B;**&#x200B;**。

      >[!NOTE]
      >跳過定義json的程式，並保留為空白。


## 步驟3：在對象中設定區段 {#setting-up-audience}

1. **在對象中建立區段**

   1. 從您的AEM執行個體瀏覽至&#x200B;**Personalization** > **對象** > **畫面**。

   1. 按一下「**建立** > **建立ContextHub區段」。** **新ContextHub區段**&#x200B;對話方塊開啟。

   1. 輸入&#x200B;**標題**&#x200B;作為`**Higherthan50**`，然後按一下&#x200B;**建立**。 同樣地，建立另一個標題為`**Lowerthan50**`的區段。

      ![影像](/help/user-guide/assets/context-hub/context-hub11.png)

   1. 按一下區段`**Higherthan50**`，然後按一下動作列中的&#x200B;**屬性**。

      ![影像](/help/user-guide/assets/context-hub/context-hub12.png)

   1. 從&#x200B;**區段屬性**&#x200B;按一下&#x200B;**Personalization**&#x200B;索引標籤。 將&#x200B;**ContextHub路徑**&#x200B;設為`/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations`，將&#x200B;**區段路徑**&#x200B;設為`/conf/screens/settings/wcm/segments`，然後按一下&#x200B;**儲存**，如下圖所示。

   ![影像](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 同樣地，也為`**Lowerthan50**`區段設定&#x200B;**ContextHub路徑**&#x200B;和&#x200B;**區段路徑**。

## 步驟4：設定品牌和區域 {#setting-brand-area}

請依照下列步驟，在品牌下的活動與區域中建立品牌：

1. **在活動中建立品牌**

   1. 從您的AEM執行個體瀏覽至&#x200B;**Personalization** > **活動**。

   1. 按一下&#x200B;**建立** > **建立品牌**。

   1. 從&#x200B;**建立頁面**&#x200B;精靈按一下&#x200B;**品牌**，然後按一下&#x200B;**下一步**。

   1. 輸入&#x200B;**Title**&#x200B;作為&#x200B;**ScreensBrand**，然後按一下&#x200B;**建立**。 您的品牌現在已建立，如下所示。

      ![影像](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >已知問題：
      >若要新增區域，請從URL移除主要網址，例如
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`。

1. **在您的品牌中建立區域**

   請依照下列步驟，在品牌中建立區域：

   1. 按一下&#x200B;**建立**，然後按&#x200B;**建立區域**。

      ![影像](/help/user-guide/assets/context-hub/context-hub9.png)

   1. 從&#x200B;**建立頁面**&#x200B;精靈按一下&#x200B;**區域**，然後按一下&#x200B;**下一步**。

   1. 輸入&#x200B;**Title**&#x200B;作為&#x200B;**ScreensValue**，然後按一下&#x200B;**建立**。
會在您的品牌中建立一個區域。

## 步驟5：在活動中建立區段 {#step-setting-up-audience-segmentation}

在您設定資料存放區並定義活動（品牌和區域）後，請依照下列步驟在活動中建立區段。

1. **在活動中建立區段**

   1. 從您的AEM執行個體瀏覽至&#x200B;**Personalization** > **活動** > **ScreensBrand** >**ScreensValue**。

   1. 按一下&#x200B;**建立** > **建立活動。** **設定活動精靈**&#x200B;開啟。

   1. 輸入&#x200B;**Title**&#x200B;作為&#x200B;**ValueCheck50**，並輸入&#x200B;**Name**&#x200B;作為&#x200B;**valuecheck50**。 從下拉式清單中按一下&#x200B;**目標定位引擎**&#x200B;做為&#x200B;**ContextHub (AEM)**，然後按一下&#x200B;**下一步**。

      ![影像](/help/user-guide/assets/context-hub/context-hub14.png)

   1. 從`**Configure Activity**`精靈按一下&#x200B;**新增體驗**。

   1. 從&#x200B;**對象**，按一下`**Higherthan50**`並按一下&#x200B;**新增體驗**，然後輸入&#x200B;**標題**&#x200B;作為`**higherthan50**` **名稱**&#x200B;作為`**higherthan50**`。 按一下&#x200B;**確定**。

   1. 從&#x200B;**對象**，按一下`**Lowerthan50**`並按一下&#x200B;**新增體驗**，然後輸入&#x200B;**標題**&#x200B;作為`**lowerthan50**` **名稱**&#x200B;作為`**lowerthan50**`。 按一下&#x200B;**確定**。

   ![影像](/help/user-guide/assets/context-hub/context-hub15.png)

   1. 按一下[下一步]&#x200B;**&#x200B;**，然後按一下[儲存]&#x200B;**&#x200B;**。 `**ValueCheck50**`活動現在已建立並設定。

      ![影像](/help/user-guide/assets/context-hub/context-hub16.png)

## 步驟5：編輯受眾中的區段{#editing-audience-segmentation}

1. **編輯區段**

   1. 從您的AEM執行個體瀏覽至&#x200B;**Personalization** > **對象** > **畫面**。

   1. 按一下區段`**Higherthan50**`，然後按一下動作列中的&#x200B;**編輯**。

   1. 將&#x200B;**Comparison： Property - Value**&#x200B;元件拖放到編輯器中。

   1. 按一下扳手圖示，即可開啟&#x200B;**比較屬性與值**&#x200B;對話方塊。

   1. 從&#x200B;**屬性名稱**&#x200B;的下拉式清單中按一下&#x200B;**google工作表/value/1/0**。

      >[!NOTE]
      > **Googlesheets/value/1/0**&#x200B;參考到下圖中填入`google`工作表的列2和欄：

      ![影像](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 從下拉式功能表中按一下&#x200B;**運運算元**&#x200B;做為&#x200B;**大於**。

   1. 輸入&#x200B;**值**&#x200B;作為&#x200B;**70**。

      >[!NOTE]
      >
      >AEM會將您的區段顯示為綠色，以驗證Google工作表中的資料。

      ![影像](/help/user-guide/assets/context-hub/context-hub18.png)

   同樣地，將屬性值編輯為`**Lowerthan50**`。

   1. 將&#x200B;**Comparison： Property - Value**&#x200B;元件拖放到編輯器中。

   1. 按一下扳手圖示。

   1. 在&#x200B;**比較屬性與值**&#x200B;對話方塊中，從&#x200B;**屬性名稱**&#x200B;的下拉式清單中按一下&#x200B;**Googlesheets/value/1/0**。

   1. 從下拉式功能表中按一下&#x200B;**運運算元**&#x200B;做為&#x200B;**小於**。

   1. 輸入&#x200B;**值**&#x200B;做為&#x200B;**50**。


## 在頻道中啟用鎖定目標 {#step-enabling-targeting-in-channels}

請依照下列步驟，在您的管道中啟用目標定位。

1. 導覽至其中一個AEM Screens管道。 下列步驟示範如何使用在AEM Screens頻道中建立的&#x200B;**DataDrivenChannel**&#x200B;來啟用鎖定目標。

1. 按一下頻道&#x200B;**TargetChannel**，然後從動作列按一下&#x200B;**內容**。

   ![影像](/help/user-guide/assets/context-hub/context-hub19.png)

1. 按一下&#x200B;**Personalization**&#x200B;標籤，以便您可以設定ContextHub設定。

   1. 將&#x200B;**ContextHub路徑**&#x200B;設定為`/conf/screens/settings/wcm/segments`並將&#x200B;**區段路徑**&#x200B;設定為`/conf/screens/settings/wcm/segments`。
   1. 從下拉式清單中將品牌設定為&#x200B;**ScreensBrand**，並將&#x200B;**區域參考**&#x200B;設定為&#x200B;**ScreensValue**。

   1. 按一下&#x200B;**「儲存並關閉」**。

      >[!NOTE]
      >
      >使用ContextHub和區段路徑，您最初儲存您的ContextHub設定和區段時可使用此路徑。

      ![影像](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. 瀏覽並按一下&#x200B;**TargetChannel**&#x200B;頻道，然後從動作列按一下&#x200B;**編輯**。

      >[!NOTE]
      >
      >如果您已正確設定所有專案，您會在編輯器的下拉式清單中看到&#x200B;**鎖定目標**&#x200B;選項，如下圖所示。

      ![影像](/help/user-guide/assets/context-hub/context-hub21.png)

## 瞭解更多：範例使用案例 {#learn-more-example-use-cases}

為您的AEM Screens專案設定ContextHub後，您可以依照不同的使用案例來瞭解資料觸發的資產如何在不同產業中扮演重要角色：

1. **[零售庫存目標啟動](retail-inventory-activation.md)**
1. **[旅行中心溫度啟用](local-temperature-activation.md)**
1. **[旅館預訂啟用](hospitality-reservation-activation.md)**

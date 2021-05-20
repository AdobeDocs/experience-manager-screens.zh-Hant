---
title: 在AEM Screens中設定ContextHub
seo-title: 在AEM Screens中設定ContextHub
description: 請依照本頁面了解定位引擎中的ContextHub，以定義資料存放區，以便資料觸發內容變更。
seo-description: 請依照本頁面了解定位引擎中的ContextHub，以定義資料存放區，以便資料觸發內容變更。
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
feature: 開發螢幕
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '1533'
ht-degree: 1%

---

# 在AEM Screens {#configuring-contexthub-in-aem-screens}中設定ContextHub

本節重點說明如何使用資料存放區建立及管理資料導向的資產變更。

## 關鍵術語{#key-terms}

在我們了解在您的AEM Screens專案中建立和管理庫存導向管道的詳細資訊之前，您必須先了解與不同案例重要且相關的幾個關鍵術語。

**** 品牌：指您的高階專案說明。

**** 區域：指您的AEM Screens專案名稱，例如數位廣告標牌

**** 活動定義規則類別，例如庫存驅動、天氣驅動、部門可用性驅動等。

**** Audience定義規則。

**** 區段指依照指定規則播放的資產版本，例如，如果溫度低於華氏50度，則螢幕會顯示熱咖啡的影像，否則會顯示冷飲。

下圖以視覺化方式呈現ContextHub設定如何與活動、對象和管道保持一致。

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 先決條件 {#preconditions}

開始為AEM Screens專案設定「內容中心設定」之前，您必須先設定Google工作表（以供示範之用）。

>[!IMPORTANT]
>
>在以下範例中，Google Sheets會作為範例資料庫系統使用，其中會擷取值，且僅供教育之用。 Adobe不認可將Google工作表用於生產環境。
>
>如需詳細資訊，請參閱Google檔案中的[取得API金鑰](https://developers.google.com/maps/documentation/javascript/get-api-key)。

## 步驟1:設定資料儲存{#step-setting-up-a-data-store}

您可以將資料儲存設定為本機I/O事件或本機資料庫事件。

下列資產層級資料觸發器範例將展示本機資料庫事件，此事件會設定資料存放區，例如excel工作表，供您使用ContextHub設定和區段至AEM Screens通道的路徑。

例如，在您正確設定google工作表後，如下所示：

![影像](/help/user-guide/assets/context-hub/context-hub1.png)

以下驗證是您在檢查連線時所要檢視的，方法是輸入以下格式的兩個值&#x200B;*google工作表ID*&#x200B;和&#x200B;*API金鑰*:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![影像](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>以下特定範例以資料存放區的形式展示Google工作表，當值大於100或小於50時，便會觸發資產變更。

## 步驟2:設定儲存配置{#step-setting-store-configurations}

1. **導覽至ContextHub**

   導覽至您的AEM例項，然後按一下左側邊欄中的工具圖示。 按一下&#x200B;**Sites** —> **ContextHub**，如下圖所示。

   ![影像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **建立新的ContextHub存放區設定**

   1. 導覽至標題為&#x200B;**screens**&#x200B;的設定容器。

   1. 按一下「**建立** > **建立配置容器**」，然後輸入標題作為&#x200B;**ContextHubDemo**。

      ![影像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **** 導覽至 **ContextHubDemo**  >  **** **CreateContentHub設定，然** 後按一下 **儲存**。

      >[!NOTE]
      > 按一下&#x200B;**Save**&#x200B;後，您將位於&#x200B;**ContextHub Configuration**&#x200B;畫面中。

   1. 在&#x200B;**ContextHub配置**&#x200B;螢幕中，按一下&#x200B;**建立** > **ContentHub儲存配置……**

      ![影像](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >
      >作為AEM 6.5 Feature Pack 4或AEM 6.4 Feature Pack 8的一部分，客戶應將`/conf/screens/settings/cloudsettings`更新為`sling:Folder`。
      >
      >請遵循下列步驟：
      >
      >1. 導覽至CRXDE Lite，然後導覽至`/conf/screens/settings/cloudsettings`。
      >1. 檢查`cloudsettings jcr:primaryType`是否在`sling:Folder`中。 如果`jcr:primaryType`不在`sling:folder`中，請繼續執行後續步驟。
      >1. 按一下右鍵`/conf/screens/settings`，並建立一個新節點，其&#x200B;*name*&#x200B;為&#x200B;**cloudsettings1**&#x200B;和&#x200B;*Type*&#x200B;為&#x200B;**sling:Folder**，並保存更改。
      >1. 將`/conf/screens/settings/cloudsettings`下的所有節點移至`cloudsettings1`。
      >1. 刪除`cloudsettings`並保存。
      >1. 將`cloudsettings1`重新命名為`cloudsettings`並儲存。
      >1. 您現在應該注意， /conf/screens/settings/cloudsettings的`jcr:primaryType`為`sling:Folder`。

      >
      >您應在製作中遵循這些步驟，並在升級前或升級後發佈。

   1. 將&#x200B;**Title**&#x200B;輸入為&#x200B;**Google工作表**，將名稱&#x200B;**儲存為** Googlesheets **，將類型**&#x200B;儲存為&#x200B;**contexthub.generic-jsonp**，然後按一下&#x200B;**Next a13/>。******

      >[!CAUTION]
      >如果您使用Adobe Experience Manager(AEM)6.4，請輸入&#x200B;**Configuration Title**&#x200B;作為&#x200B;**Googlesheets**，以及&#x200B;**Store Type**&#x200B;作為&#x200B;**contexthub.generic-jsonp**。

      ![影像](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 輸入您的特定json設定。 例如，您可以將下列json用於示範用途，然後按一下&#x200B;**Save**，在ContextHub設定中就會看到標題為&#x200B;**Google工作表**&#x200B;的商店設定。

      >[!IMPORTANT]
      >請務必將程式碼取代為您在設定Google工作表時擷取的&#x200B;*&lt;Sheet ID>*&#x200B;和&#x200B;*&lt;API金鑰>*。

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
      在上述范常式式碼中，**pollInterval**&#x200B;定義值重新整理的頻率（以毫秒為單位）。
      將程式碼取代為您在設定Google工作表時擷取的&#x200B;*&lt;Sheet ID>*&#x200B;和&#x200B;*&lt;API金鑰>*。

      >[!CAUTION]
      如果您在全域資料夾之外（例如在您自己的專案資料夾中）建立Google工作表存放設定，則鎖定目標將無法立即運作。


1. **設定商店細分**

   1. 導覽至&#x200B;**ContentHub存放區設定。** 並在「螢幕設定」容器中建立其他存放區設 **** 定，並設 **定「標題」區段 — contexthub**、「 **** 存放名稱 **** 」區段 **和「存放** 類型」 **aem.segmentation**。

      ![影像](/help/user-guide/assets/context-hub/context-hub7.png)

   1. 按一下&#x200B;**Next**，然後按一下&#x200B;**Save**。

      >[!NOTE]
您必須略過定義json的程式，並將其保留為空白。


## 步驟3:在對象{#setting-up-audience}中設定區段

1. **在受眾中建立區段**

   1. 從您的AEM例項導覽至&#x200B;**個人化** > **對象** > **螢幕**。

   1. 按一下「**建立** > **建立內容中樞區段」。** 「新 **建ContextHub區** 段」對話方塊隨即開啟。

   1. 輸入&#x200B;**Title**&#x200B;作為&#x200B;**Higherthan50**，然後按一下&#x200B;**Create**。 同樣地，請建立另一個名為&#x200B;**Lowerthan50**&#x200B;的區段。

      ![影像](/help/user-guide/assets/context-hub/context-hub11.png)

   1. 選取區段&#x200B;**高度50**，然後從動作列按一下&#x200B;**屬性**。
      ![影像](/help/user-guide/assets/context-hub/context-hub12.png)

   1. 從&#x200B;**區段屬性**&#x200B;中選取&#x200B;**個人化**&#x200B;標籤。 將&#x200B;**ContextHub路徑**&#x200B;設定為`/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations`，將&#x200B;**區段路徑**&#x200B;設定為`/conf/screens/settings/wcm/segments`，然後按一下&#x200B;**儲存**，如下圖所示。

      ![影像](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 同樣地，也為&#x200B;**Lowerthan50**&#x200B;區段設定&#x200B;**ContextHub路徑**&#x200B;和&#x200B;**區段路徑**。

## 步驟4:設定品牌和區域{#setting-brand-area}

請依照下列步驟，在您的活動中和品牌下方的區域建立品牌：

1. **在活動中建立品牌**

   1. 從您的AEM例項導覽至&#x200B;**Personalization** > **Activities**。

   1. 按一下「**建立** > **建立品牌**」。

   1. 從&#x200B;**建立頁面**&#x200B;精靈中選擇&#x200B;**品牌** ，然後按一下&#x200B;**下一步**。

   1. 將&#x200B;**Title**&#x200B;輸入為&#x200B;**ScreensBrand**，然後按一下&#x200B;**Create**。 您的品牌現在已建立，如下所示。

      ![影像](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      已知問題：
若要新增區域，請從URL中移除主版，例如
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`。

1. **在您的品牌中建立區域**

   請依照下列步驟，在品牌中建立區域：

   1. 按一下「**建立**」，然後按一下「建立區域&#x200B;**」。**

      ![影像](/help/user-guide/assets/context-hub/context-hub9.png)

   1. 從&#x200B;**建立頁面**&#x200B;嚮導中選擇&#x200B;**區域**，然後按一下&#x200B;**下一步**。

   1. 將&#x200B;**Title**&#x200B;輸入為&#x200B;**ScreensValue**，然後按一下&#x200B;**Create**。
系統會在您的品牌中建立區域。

## 步驟5:在活動{#step-setting-up-audience-segmentation}中建立區段

設定資料存放區並定義活動（品牌和區域）後，請依照下列步驟在活動中建立區段。

1. **在活動中建立區段**

   1. 從您的AEM例項導覽至&#x200B;**Personalization** > **Activities** > **ScreensBrand** >**ScreensValue**。

   1. 按一下「**建立** > **建立活動」。** 設定 **活動精** 靈。

   1. 將&#x200B;**Title**&#x200B;輸入為&#x200B;**ValueCheck50**，將&#x200B;**Name**&#x200B;輸入為&#x200B;**valuecheck50**。 從下拉式清單中選取&#x200B;**目標引擎**&#x200B;作為&#x200B;**ContextHub(AEM)**，然後按一下&#x200B;**Next**。

      ![影像](/help/user-guide/assets/context-hub/context-hub14.png)

   1. 從&#x200B;**設定活動精靈**&#x200B;按一下「新增體驗&#x200B;**」 。**

   1. 從&#x200B;**對象**&#x200B;中，選擇&#x200B;**高於50**，然後按一下&#x200B;**新增體驗**，並將&#x200B;**標題**&#x200B;輸入為&#x200B;**高於50** **名稱**&#x200B;為&#x200B;**高於50**。 按一下&#x200B;**確定**。

   1. 從&#x200B;**對象**&#x200B;中，選擇&#x200B;**小寫&lt;a50**，然後按一下&#x200B;**新增體驗**，然後輸入&#x200B;**標題**&#x200B;小寫&#x200B;**小寫**&#x200B;名稱&#x200B;**作為**&#x200B;小寫&#x200B;**。**&#x200B;按一下&#x200B;**確定**。

      ![影像](/help/user-guide/assets/context-hub/context-hub15.png)

   1. 按一下&#x200B;**Next**，然後按一下&#x200B;**Save**。 **現在已建立並設定ValueCheck50** 活動。

      ![影像](/help/user-guide/assets/context-hub/context-hub16.png)

## 步驟5:編輯對象中的區段{#editing-audience-segmentation}

1. **編輯區段**

   1. 從您的AEM例項導覽至&#x200B;**個人化** > **對象** > **螢幕**。

   1. 選取區段&#x200B;**高於50**，然後從動作列按一下&#x200B;**編輯**。

   1. 拖放&#x200B;**比較：屬性 — 對編輯器的值**&#x200B;元件。

   1. 按一下扳手圖示以開啟「將屬性與值&#x200B;**比較」對話方塊。**

   1. 從&#x200B;**屬性名稱**&#x200B;中的下拉式清單中選擇&#x200B;**googlesheets/value/1/0**。

      >[!NOTE]
googlesheets/value/1/ **0** 會參照下圖中Google工作表中填入的第2列和欄：

      ![影像](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 從下拉式選單中選取&#x200B;**Operator**&#x200B;作為&#x200B;**greater-than**。

   1. 將&#x200B;**值**&#x200B;輸入為&#x200B;**70**。

      >[!NOTE]
      AEM會將您的區段顯示為綠色，以驗證Google工作表中的資料。

      ![影像](/help/user-guide/assets/context-hub/context-hub18.png)
   同樣地，將屬性值編輯為&#x200B;**Lowerthan50**。

   1. 拖放&#x200B;**比較：屬性 — 對編輯器的值**&#x200B;元件。

   1. 按一下扳手圖示以開啟「將屬性與值&#x200B;**比較」對話方塊。**

   1. 從&#x200B;**屬性名稱**&#x200B;中的下拉式清單中選擇&#x200B;**googlesheets/value/1/0**。

   1. 從下拉式選單中選取&#x200B;**Operator**&#x200B;作為&#x200B;**小於**。

   1. 將&#x200B;**值**&#x200B;輸入為&#x200B;**50**。



## 在通道中啟用定位{#step-enabling-targeting-in-channels}

請依照下列步驟，在您的管道中啟用鎖定目標。

1. 導覽至其中一個AEM Screens管道。 下列步驟示範如何使用在AEM Screens頻道中建立的&#x200B;**DataDrivenChannel**&#x200B;來啟用定位。

1. 選取通道&#x200B;**TargetChannel**，然後從動作列按一下&#x200B;**屬性**。

   ![影像](/help/user-guide/assets/context-hub/context-hub19.png)

1. 選取&#x200B;**Personalization**&#x200B;標籤以設定ContextHub設定。

   1. 將&#x200B;**ContextHub路徑**&#x200B;設定為`/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations`，將&#x200B;**區段路徑**&#x200B;設定為`/conf/screens/settings/wcm/segments`，然後按一下&#x200B;**儲存**。

   1. 按一下&#x200B;**「儲存並關閉」**。

      >[!NOTE]
      使用ContextHub和區段路徑，您最初會在此儲存內容中樞設定和區段。

      ![影像](/help/user-guide/assets/context-hub/context-hub20.png)

   1. 導覽並選取&#x200B;**TargetChannel**&#x200B;頻道，然後按一下動作列中的&#x200B;**Edit**。

      >[!NOTE]
      如果您已正確設定所有項目，您會在編輯器的下拉式清單中看到「**目標定位**」選項，如下圖所示。

      ![影像](/help/user-guide/assets/context-hub/context-hub21.png)

## 更多詳情：使用案例範例{#learn-more-example-use-cases}

為AEM Screens專案設定ContextHub後，您可以遵循不同的使用案例來了解資料觸發資產在不同產業中扮演重要角色的方式：

1. **[零售庫存目標激活](retail-inventory-activation.md)**
1. **[旅行中心溫度激活](local-temperature-activation.md)**
1. **[酒店預訂激活](hospitality-reservation-activation.md)**

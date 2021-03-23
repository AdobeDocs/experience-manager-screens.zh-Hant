---
title: 在AEM Screens配置ContextHub
seo-title: 在AEM Screens配置ContextHub
description: 請依照本頁瞭解定位引擎中的ContextHub，以定義資料儲存區，以利資料觸發內容變更。
seo-description: 請依照本頁瞭解定位引擎中的ContextHub，以定義資料儲存區，以利資料觸發內容變更。
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
feature: 開發螢幕
role: 開發人員
level: 中級
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1535'
ht-degree: 1%

---


# 在AEM Screens配置ContextHub {#configuring-contexthub-in-aem-screens}

本節著重說明如何使用資料存放區來建立和管理資料導向的資產變更。

## 關鍵詞{#key-terms}

在我們瞭解在您的AEM Screens專案中建立和管理庫存導向渠道的詳細資訊之前，您必須先瞭解一些重要且與不同藍本相關的關鍵術語。

**品** 牌是指您的高階專案說明。

**區** 域是指您的AEM Screens專案名稱，例如數位廣告標牌

**活** 動定義規則類別，例如庫存驅動、天氣驅動、部門可用性驅動等。

**對** 像定義規則。

**區** 段：指要依特定規則播放的資產版本，例如當溫度低於華氏50度時，螢幕會顯示熱咖啡的影像，否則會顯示冷飲。

下圖以視覺化方式呈現ContextHub組態與「活動」、「對象」和「頻道」的一致性。

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 先決條件{#preconditions}

在開始為AEM Screens項目配置上下文中心配置之前，您必須設定Google工作表（用於演示）。

>[!IMPORTANT]
>
>Google Sheets在下列範例中用作擷取值的範例資料庫系統，僅供教育用途。 Adobe不會為生產環境使用Google工作表背書。
>
>如需詳細資訊，請參閱Google檔案中的[取得API金鑰](https://developers.google.com/maps/documentation/javascript/get-api-key)。

## 步驟1:設定資料儲存{#step-setting-up-a-data-store}

您可以將資料儲存設定為本地I/O事件或本地資料庫事件。

下列資產層級資料觸發器範例展示本機資料庫事件，此事件可設定資料儲存區，例如Excel表單，讓您使用ContextHub組態和區段至AEM Screens頻道的路徑。

在您正確設定Google工作表後，例如，如下所示：

![影像](/help/user-guide/assets/context-hub/context-hub1.png)

在檢查連線時，您會輸入以下格式的&#x200B;*google工作表ID*&#x200B;和&#x200B;*API金鑰*&#x200B;這兩個值，以檢視下列驗證：

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![影像](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>下列特定範例會將Google工作表顯示為資料存放區，當值高於100或小於50時，會觸發資產變更。

## 步驟2:設定儲存配置{#step-setting-store-configurations}

1. **導覽至ContextHub**

   導覽至您的AEM例項，然後從左側邊欄按一下工具圖示。 按一下&#x200B;**Sites** —> **ContextHub** ，如下圖所示。

   ![影像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **建立新的ContextHub商店設定**

   1. 導覽至名為&#x200B;**screens**&#x200B;的設定容器。

   1. 按一下「建立&#x200B;**** > **建立組態容器**」，然後輸入標題為&#x200B;**ContextHubDemo**。

      ![影像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **導** 覽至 **ContextHubDemo** >  **** **CreateContentHub設定，** 然後按一下 **儲存**。

      >[!NOTE]
      > 按一下&#x200B;**Save**&#x200B;後，將顯示在&#x200B;**ContextHub Configuration**&#x200B;螢幕中。

   1. 在&#x200B;**ContextHub Configuration**&#x200B;畫面中，按一下「建立&#x200B;**>** ContentHub Store Configuration...**」**

      ![影像](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >
      >作為6.AEM5 Feature Pack 4或AEM6.4 Feature Pack 8的一部分，客戶應將`/conf/screens/settings/cloudsettings`更新為`sling:Folder`。
      >
      >請遵循下列步驟：
      >
      >1. 導覽至CRXDE Lite，然後導覽至`/conf/screens/settings/cloudsettings`。
      >1. 檢查`cloudsettings jcr:primaryType`是否在`sling:Folder`中。 如果`jcr:primaryType`不在`sling:folder`中，請繼續下一步。
      >1. 在`/conf/screens/settings`上按一下滑鼠右鍵，並建立新節點，其名稱&#x200B;*name*&#x200B;為&#x200B;**cloudsettings1**，而&#x200B;*Type*&#x200B;為&#x200B;**sling:Folder**，並儲存變更。
      >1. 將`/conf/screens/settings/cloudsettings`下的所有節點移動到`cloudsettings1`。
      >1. 刪除`cloudsettings`並保存。
      >1. 將`cloudsettings1`重新命名為`cloudsettings`並儲存。
      >1. 您現在應該注意到/conf/screens/settings/cloudsettings的`jcr:primaryType`為`sling:Folder`。

      >
      >您應依照作者的這些步驟進行，並在升級前後發佈。

   1. 將&#x200B;**Title**&#x200B;輸入為&#x200B;**Google Sheets**、**Store Name**&#x200B;輸入為&#x200B;**Googlessheet**&#x200B;和&#x200B;**Store Type**&#x200B;輸入為&#x200B;**conthub.generic-jsonp**，然後按一下「下一步」**。**

      >[!CAUTION]
      >如果您使用Adobe Experience Manager(AEM)6.4，請將&#x200B;**配置標題**&#x200B;輸入為&#x200B;**googlesheets**，將&#x200B;**商店類型**&#x200B;輸入為&#x200B;**contexthub.generic-jsonp**。

      ![影像](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 輸入您的特定json設定。 例如，您可以使用下列json進行示範，然後按一下&#x200B;**Save**，您就會在ContextHub設定中看到名為&#x200B;**Google Sheets**&#x200B;的商店設定。

      >[!IMPORTANT]
      >請務必將程式碼取代為您在設定Google Sheets時擷取的&#x200B;*&lt;Sheet ID>*&#x200B;和&#x200B;*&lt;API金鑰>*。

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
      如果您建立Google Sheets會將設定儲存在全域資料夾以外（例如在您自己的專案資料夾中），則定位將無法立即使用。


1. **設定商店區段**

   1. 導覽至&#x200B;**ContentHub商店設定。** 然後在螢幕配置容器中建立另一個儲存配置，並設定 ****  **Leas**&#x200B;分段-conthub **、** Store  **** Nameas segment **和** Store  **** Typenames分段tatem和as aa.segmentation textem。

      ![影像](/help/user-guide/assets/context-hub/context-hub7.png)

   1. 按一下&#x200B;**Next**，然後按一下&#x200B;**Save**。

      >[!NOTE]
您必須略過定義json的程式，並將其保留為空白。


## 步驟3:在對象{#setting-up-audience}中設定區段

1. **在觀眾中建立區段**

   1. 從您AEM的例項導覽至&#x200B;**個人化** > **觀眾** > **畫面**。

   1. 按一下「建立&#x200B;**** > **建立內容中樞區段」。** 「新建 **ContextHub區** 段」(New ContextHub Segments)對話框開啟。

   1. 將&#x200B;**Title**&#x200B;輸入為&#x200B;**Higherthan50**，然後按一下&#x200B;**Create**。 同樣地，請建立另一個名為&#x200B;**Lowerthan50**&#x200B;的區段。

      ![影像](/help/user-guide/assets/context-hub/context-hub11.png)

   1. 選擇&#x200B;**Higherthan 50**&#x200B;區段，然後從操作欄中按一下&#x200B;**屬性**。
      ![影像](/help/user-guide/assets/context-hub/context-hub12.png)

   1. 從&#x200B;**區段屬性**&#x200B;中選擇&#x200B;**個人化**&#x200B;標籤。 將&#x200B;**ContextHub路徑**&#x200B;設為`/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations`和&#x200B;**區段路徑**&#x200B;設為`/conf/screens/settings/wcm/segments`，然後按一下&#x200B;**儲存**，如下圖所示。

      ![影像](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 同樣地，也請為&#x200B;**Loberthan50**&#x200B;區段設定&#x200B;**ContextHub路徑**&#x200B;和&#x200B;**區段路徑**。

## 步驟4:設定品牌和區域{#setting-brand-area}

請依照下列步驟，在您的活動和品牌下方建立品牌：

1. **在活動中建立品牌**

   1. 從您AEM的例項導覽至&#x200B;**個人化** > **活動**。

   1. 按一下「建立&#x200B;**** > **建立品牌**」。

   1. 從&#x200B;**「建立頁面」嚮導中選擇** Brand **，然後按一下** Next **。**

   1. 將&#x200B;**Title**&#x200B;輸入為&#x200B;**ScreensBrand**，然後按一下&#x200B;**Create**。 您的品牌現在已建立，如下所示。

      ![影像](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      已知問題：
若要新增區域，請從URL移除主版，例如
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`。

1. **在品牌中建立區域**

   請依照下列步驟，在品牌中建立區域：

   1. 按一下&#x200B;**建立**，然後按一下&#x200B;**建立區域**。

      ![影像](/help/user-guide/assets/context-hub/context-hub9.png)

   1. 從&#x200B;**「建立頁面」嚮導中選擇**&#x200B;區域&#x200B;**，然後按一下** Next **。**

   1. 將&#x200B;**Title**&#x200B;輸入為&#x200B;**ScreensValue**，然後按一下&#x200B;**Create**。
您的品牌中會建立一個區域。

## 步驟5:在活動{#step-setting-up-audience-segmentation}中建立區段

設定資料儲存區並定義活動（品牌和區域）後，請依照下列步驟在活動中建立區段。

1. **在活動中建立區段**

   1. 從您AEM的例項導覽至&#x200B;**Personalization** > **Activity** > **ScreensBrand** >**ScreensValue**。

   1. 按一下「建立&#x200B;**** > **建立活動」。** 「設 **定活動** 精靈」。

   1. 將&#x200B;**Title**&#x200B;輸入為&#x200B;**ValueCheck50**，將&#x200B;**Name**&#x200B;輸入為&#x200B;**valuecheck50**。 從下拉式清單中選取&#x200B;**定位引擎**&#x200B;為&#x200B;**ContextHub(AEM)**，然後按一下&#x200B;**Next**。

      ![影像](/help/user-guide/assets/context-hub/context-hub14.png)

   1. 從&#x200B;**設定活動精靈**&#x200B;按一下「新增體驗」。****

   1. 從&#x200B;**觀眾**&#x200B;中，選擇&#x200B;**Higherthan 50**，然後按一下&#x200B;**Add Experience**，然後將&#x200B;**Title**&#x200B;輸入為&#x200B;**highthon 50** **Name**&#x200B;為&#x200B;**高於50**。 按一下&#x200B;**確定**。

   1. 在&#x200B;**觀眾**&#x200B;中，選擇&#x200B;**小寫50**，然後按一下&#x200B;**新增體驗**，然後輸入&#x200B;**標題**&#x200B;小寫50 ****&#x200B;名稱&#x200B;**為** lowerthan50 **。**&#x200B;按一下&#x200B;**確定**。

      ![影像](/help/user-guide/assets/context-hub/context-hub15.png)

   1. 按一下&#x200B;**Next**，然後按一下&#x200B;**Save**。 **ValueCheck50活** 動現在已建立並設定。

      ![影像](/help/user-guide/assets/context-hub/context-hub16.png)

## 步驟5:在觀眾中編輯區段{#editing-audience-segmentation}

1. **編輯區段**

   1. 從您AEM的例項導覽至&#x200B;**個人化** > **觀眾** > **畫面**。

   1. 選取區段&#x200B;**Higherthan 50**，然後從動作列按一下「編輯&#x200B;**a3/>」。**

   1. 拖放&#x200B;**比較：屬性——對編輯器的值**&#x200B;元件。

   1. 按一下扳手圖示以開啟「比較屬性與值&#x200B;**」對話方塊。**

   1. 從&#x200B;**屬性名稱**&#x200B;的下拉式清單中選擇&#x200B;**googlessheets/value/1/0**。

      >[!NOTE]
googlesheets/ **value/1/0** 是指在下圖的google工作表中填入的行2和列：

      ![影像](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 從下拉菜單中選擇&#x200B;**Operator**&#x200B;作為&#x200B;**greater-than**。

   1. 將&#x200B;**Value**&#x200B;輸入為&#x200B;**70**。

      >[!NOTE]
      The AEM vertifice your data from the Google Sheet by showing your segment as green.

      ![影像](/help/user-guide/assets/context-hub/context-hub18.png)
   同樣地，將屬性值編輯為&#x200B;**Lowerthan50**。

   1. 拖放&#x200B;**比較：屬性——對編輯器的值**&#x200B;元件。

   1. 按一下扳手圖示以開啟「比較屬性與值&#x200B;**」對話方塊。**

   1. 從&#x200B;**屬性名稱**&#x200B;的下拉式清單中選擇&#x200B;**googlessheets/value/1/0**。

   1. 從下拉菜單中選擇&#x200B;**運算子**&#x200B;作為&#x200B;**less-than**。

   1. 將&#x200B;**值**&#x200B;輸入為&#x200B;**50**。



## 在渠道中啟用定位{#step-enabling-targeting-in-channels}

請依照下列步驟，在您的通道中啟用定位。

1. 導覽至其中一個AEM Screens頻道。 下列步驟示範如何使用在AEM Screens頻道中建立的&#x200B;**DataDrivenChannel**&#x200B;來啟用定位。

1. 選擇通道&#x200B;**TargetChannel**，然後從操作欄按一下&#x200B;**屬性**。

   ![影像](/help/user-guide/assets/context-hub/context-hub19.png)

1. 選擇&#x200B;**個人化**&#x200B;標籤以設定ContextHub組態。

   1. 將&#x200B;**ContextHub路徑**&#x200B;設為`/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations`和&#x200B;**區段路徑**&#x200B;設為`/conf/screens/settings/wcm/segments`，然後按一下&#x200B;**儲存**。

   1. 按一下&#x200B;**「儲存並關閉」**。

      >[!NOTE]
      使用ContextHub和區段路徑，您最初在此儲存上下文中心組態和區段。

      ![影像](/help/user-guide/assets/context-hub/context-hub20.png)

   1. 導覽並選取&#x200B;**TargetChannel**&#x200B;頻道，然後從動作列按一下「編輯&#x200B;**a3/>」。**

      >[!NOTE]
      如果您已正確設定所有項目，您會從編輯器的下拉式清單中看到&#x200B;**定位**&#x200B;選項，如下圖所示。

      ![影像](/help/user-guide/assets/context-hub/context-hub21.png)

## 更多資訊：範例使用案例{#learn-more-example-use-cases}

在您為AEM Screens項目配置ContextHub後，您可以遵循不同的使用案例來瞭解資料觸發資產在不同產業中扮演重要角色的方式：

1. **[零售庫存鎖定](retail-inventory-activation.md)**
1. **[旅行中心溫度激活](local-temperature-activation.md)**
1. **[酒店預訂激活](hospitality-reservation-activation.md)**

---
title: 庫存驅動渠道
seo-title: 庫存驅動渠道
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: a7e7aa08-8f9e-4458-bdce-225cf29a6da4
contentOwner: jsyal
discoiquuid: 9989ef4c-9fdd-4bf2-9f7c-0c74a9cc4e7f
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 庫存驅動渠道{#inventory-driven-channel}

## 開始使用庫存導向的通道 {#getting-started-with-inventory-driven-channels}

本節說明使用案例範例，著重說明如何使用Google工作表建立和管理資料導向的資產變更。

### 先決條件 {#preconditions}

開始此使用案例之前，請務必瞭解如何：

* **[建立和管理渠道](managing-channels.md)**
* **[建立和管理位置](managing-locations.md)**
* **[建立和管理計畫](managing-schedules.md)**
* **[裝置註冊](device-registration.md)**

### 主要操作者 {#primary-actors}

內容作者

### 術語 {#terminolgies}

請遵循以下條款，這些條款在瞭解和設定不同使用案例中的專案方面扮演重要角色：

**「活動** 」活動是指類別。

**區域** Project主要

**資料的** 「對象位置」

**品牌** -品牌

**區段** 」是指您嘗試定位的資產容器。

### 基本流：設定專案 {#basic-flow-setting-up-the-project}

>[!NOTE]
>
>**先決條件：**
>
>在您深入瞭解專案中設定和使用資料導向資產變更的詳細資訊之前，請務必使用序列頻道建立AEM Screens專案。 為了示範， **DataDrivenAsset** project會建立 **DataDrivenAsset**，並將名為 **DataDrivenTextOverlay********** 、標題為DataDiveringTheasterDataDivedAsset的DataRestaurant頻道排序，並新增至專案（如下圖所示）。
>
>建立4個不同的通道僅供展示之用，並在不同通道中展示4個不同的使用案例。 如果您只想依循一個使用案例做為需求，請自由建立一個序列頻道。

![screen_shot_2019-05-01at42043pm](assets/screen_shot_2019-05-01at42043pm.png)

請依照下列章節建立範例專案，以在AEM Screens專案中使用Google Sheets建立和管理資料導向的資產變更：

## 步驟1:設定資料庫 {#step-setting-up-database}

>[!CAUTION]
>
>Google Sheets用於以下範例資料庫系統，從中擷取值，僅供教育用途。 Adobe不會為生產環境使用Google Sheets背書。
>
>如需詳細資訊，請參閱 [Google檔案中的「取得API金鑰](https://developers.google.com/maps/documentation/javascript/get-api-key) 」。

1. 登入Google Docs。

   >[!NOTE]
   >
   >您必須先在Google雲端硬碟中擁有帳戶，才能建立新的Google工作表。

1. 開始新的空白試算表。 將內容新增至您的Google工作表並儲存。 為進行示範，Google工作表會命名為 **ContextHubDemo**。
1. 按一 **下** 「Google工作表」右上角的「共用」，以開啟「與其 **他人共用** 」對話方塊。 按一 **下「進階** 」選項，並將設定變更為「 **開啟——任何具有連結的人**」，如下圖所示。

   此步驟可讓您存取Google工作表中的值。

   ![screen_shot_2019-04-22at115829am](assets/screen_shot_2019-04-22at115829am.png)

1. 當您按一下 **前述步驟** 中的「儲存」時，將會取得Google工作表的連結。 保存按一下以供將來參照使用，然後按一下「 **完成**」。

   ![screen_shot_2019-04-22at120242pm](assets/screen_shot_2019-04-22at120242pm.png)

>[!CAUTION]
>
>Google Sheets會用於下列範例，以利教育用途。 Adobe不會為生產環境使用Google Sheets背書。

## 步驟2:啟用Google Sheets REST API {#step-enabling-the-google-sheets-rest-apis}

設定好Google Sheet後，您必須啟用Google Sheet REST API才能存取值。

如要瞭解如何啟用Google工作表的REST API，請參閱Google API檔案。

1. 導覽至 [Google API Console](https://console.developers.google.com/apis/credentials)。 Click **CREATE** to create a new project.

   ![screen_shot_2019-04-22at125028pm](assets/screen_shot_2019-04-22at125028pm.png)

1. 將項目名 **稱輸入為** AssetChange **，然後單** 擊CREATE ****。
1. 在您建立專案後，就需要設定API金鑰。 按一 **下「建立認證** 」並選取「**API金鑰**」，以產生專案的API金鑰。 儲存API金鑰以供日後參考使用。

   >[!NOTE]
   >
   >此示範專案使用免費的Google API金鑰。 如需詳細資訊，請參閱Google網站「取得 **API金鑰」上的定價和限制** 。

### 驗證Google工作表的設定 {#verifying-the-setup-of-google-sheets}

```
Verify the data in your Google Sheets using the steps below
```

[https://sheets.googleapis.com/v4/spreadsheets/](https://sheets.googleapis.com/v4/spreadsheets/)&lt;您的工作表ID&gt;/values/Sheet1?key=&lt;您的API金鑰&gt;

例如：

如果** Google Sheets**連結如 *下：*

`https://docs.google.com/spreadsheets/d/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/edit?usp=sharing`，則

**工作表ID** 為： `1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M`

**API金鑰** : `AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

在上述語法中新增兩個值：

`https://sheets.googleapis.com/v4/spreadsheets/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/values/Sheet1?key=AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

您現在應該可以在工作表中檢視資料。

## 步驟2:設定AEM以擷取Google工作表的內容 {#step-configuring-aem-to-fetch-the-content-of-the-google-sheets}

以下章節說明如何設定Adobe Experience Manager(AEM)以從Google工作表擷取內容。

1. 導覽至您的AEM例項，然後按一下左側邊欄中的工具圖示。 按一 **下Sites** —&gt; **ContextHub**，如下圖所示。

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **建立新的ContextHub商店設定**

   1. 導覽至 **全域** &gt;預 **設** &gt; **ContextHub設定**。

   1. 按一下**「建立&gt;設定容器」, **然後輸入標題為** ContextHubDemo**。

   1. **** 導覽至&#x200B;**「** ContextHubDemo **&gt;** ContentHub商店設定……」開啟「配 **置」嚮導**
   1. 將Google Sheets **輸入為** Google Sheets **,Google Store Name** as **Google Sheets Store Name,************as Contexthushusonp.Type Store**
   1. 按「下一 **步」**
   1. 輸入您的特定json設定。 例如，您可以使用下列json進行示範。
   1. 按一下&#x200B;**「儲存」**。

   ```
   {
     "service": {
       "host": "sheets.googleapis.com",
       "port": 80,
       "path": "/v4/spreadsheets/<your sheet it>/values/Sheet1",
       "jsonp": false,
       "secure": true,
       "params": {
         "key": "<your API key>"
       }
     },
     "pollInterval": 3000
   }
   ```

   >[!NOTE]
   >
   >在上述范常式式碼中， **pollInterval** 定義值重新整理的頻率（以毫秒為單位）。
   >
   >
   >將您從步驟1 *擷取的程式碼取代**為&lt;Sheet ID&gt;和&lt;API金鑰&gt;***:設定資料庫。**

   >[!CAUTION]
   如果您建立Google Sheets會將設定儲存在舊版資料夾以外（例如在您自己的專案資料夾中），則定位將無法立即使用。
   如果您想要在全域舊式資料夾外設定Google Sheets商店設定，則必須將 **Store Name** （商店名稱）設 **為區段，而** Store Type **（商店類型）******&#x200B;設為Aem.segmentationProduct。 此外，您必須略過如上定義json的程式。

1. **在活動中建立品牌**

   1. 從您的AEM例項導覽至「個人化 **&gt;活動」****。**

   1. 按一下**建立** &gt;建 **立品牌**

   1. 從「建 **立頁面** 」精靈中選 **取「品牌」** ，然後按「下一 **步」**

   1. 輸入Title **as** ContextHubDemo **，然後按一** 下Create ****。 您的品牌現在已建立，如下所示。
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)

1. 

>[!CAUTION]
已知問題：
若要新增區域，請從URL移除主版，例如
[https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master](https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master)

1. 在品牌中建立區域**

   1. 按一 **下「建立** &gt;建 **立區域」**

   1. 從* *** Create Page**精靈中選取** 「區域」，然後按一下「下一步」

   1. 將標題輸 **入為****GoogleSheets** ，然後按一 **下建立**。 您的區域將會在活動中建立。

1. **在觀眾中建立區段**

   1. 從您的AEM例項導覽至「個 **人化** &gt;觀眾 **&gt;** We.Retail ****」。
   1. 按一 **下「建立** &gt;建 **立內容中樞區段」**。 「新建ContextHub區段」對話方塊隨即開啟。
   1. 將「標 **題** 」輸入 **為SheetA1 1** ，然後單 **擊建立**。 同樣地，請建立另一個名為 **SheetA2 2的區段**。

1. **編輯區段**

   1. 選取區 **段工作表A1 1** (在步驟(5)中建立)，然後從動作列按 **一下編輯** 。

   1. 拖放比 **較：屬性** -編輯器的值元件。
   1. 按一下扳手圖示以開啟「 **比較屬性與值** 」對話方塊。
   1. 從「 **屬性名稱」(Property name)的下拉式清單中選取** Googlesheets/value/1/0 ****。

   1. 從下 **拉式選單中** ，選取「運算子」為「**等於**」。

   1. 將值輸 **入** 1 ****。
   >[!NOTE]
   AEM會將區段顯示為綠色，以驗證您來自Google工作表的資料。

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   同樣地，請將屬性值編輯 **為工作表A1 2**。

   1. 拖放比 **較：屬性** -編輯器的值元件。
   1. 按一下扳手圖示以開啟「 **比較屬性與值** 」對話方塊。
   1. 從「 **屬性名稱」(Property name)的下拉式清單中選取** Googlesheets/value/1/0 ****。

   1. 從下 **拉式選單中** ，選取「運算子」為「**等於**」。

   1. 將值 **輸入****為2**。
   >[!NOTE]
   上述步驟中套用的規則只是您如何設定區段以實施下列使用案例的範例。

## 步驟3:在AEM畫面頻道中設定內容中樞組態 {#step-setting-up-context-hub-configurations-in-aem-screens-channel}

請依照下列步驟來設定ContextHub組態和區段至AEM畫面頻道的路徑。

1. 導覽至您所建立的其中一個AEM畫面頻道(**DataDrivenRetail**)，做為先決條件。
1. 選取渠道(**DataDrivenRetail**)，然後從動作列按 **一下「屬性** 」。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 選擇「個 **人化** 」標籤以設定ContextHub組態。

   1. 選擇ContextHub路徑 **,** 作為libs **&gt;** settings **&gt; Default Settings** &gt; Default Zetings ****************&gt; Configurations Journations CloudSelectLoudLouds。

   1. 選擇「路 **徑** 」段 **作為** conf ****We.Retail *** &gt; **Retail *設定*** Settings **** &gt; **** LickSelectLightSelectZht。

   1. 按一 **下儲存並關閉**。
   >[!NOTE]
   使用ContextHub和區段路徑，您最初在此儲存上下文中心組態和區段。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

   >[!NOTE]
   如果您未從上述對話方 **塊中選取「定位設定」下的「品牌****** 」，則啟動「定位」程式時，必須選取「品牌」和「活動」。

1. 從DataDrivenAssets &gt; **Channels **導覽並選 **取DataDrivenRetail** ，然後從動作列按一下 **Edit****** 。

   >[!NOTE]
   如果您已正確設定所有項目，您會從編輯器的下拉式清單中看到 **Targeting** （定位）選項，如下圖所示。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   為渠道配置ContextHub配置後，如果您想要遵循以下所有使用案例，請務必遵循1到4的前述步驟，對於其他三個順序渠道。

## 使用案例1:零售庫存啟動 {#use-case-retail-inventory-activation}

下列使用案例會根據您的Google工作表中的值，展示3種不同的影像。

### 說明 {#description}

此使用案例會展示三種不同顏色的運動衫的零售庫存。 根據Google Sheets中記錄的庫存中可用的汗衫數量，螢幕上會顯示數量最多的影像（紅色、綠色或藍色汗衫）。

在此使用案例中，紅色、綠色或藍色毛衣會根據可用毛衣數的最高值顯示在您的螢幕上。

### 過程 {#procedure}

請依照下列步驟實施「零售庫存啟動」使用案例：

1. **填入Google工作表**

   1. 導覽至ContextHubDemo google工作表。
   1. 為3種不同的運動衫新增3欄（紅色、綠色和藍色）及對應值。
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **依需求設定觀眾**

   1. 導覽至對象中的區段(在步驟2的步驟(5)中 ***建立：設定AEM以擷取Google工作表的內容***)。
   1. 新增三個 **新區段For_Red**、 **For_Green**&#x200B;和 **For_Blue**。

   1. 選 **取For_Red** ，然後從動作 **列按一下「編輯** 」。

   1. 拖放比 **較：屬性** -對編輯器的屬性，然後按一下配置表徵圖以編輯屬性。
   1. 從「 **第一個屬性名稱」的下拉式清單中選取****Googlesheets/value/1/2**

   1. 從下 **拉式選單中** ，選取「運算子」為「大於」**

   1. 選擇數 **據類型** ，作為 **數字**

   1. 從「 **第二個屬性名稱」(****Second Property name)的下拉式清單中，選取Googlesheets/value/1/1**

   1. 拖放**另一個比較：屬性——對編輯器的屬性**，然後按一下配置表徵圖以編輯屬性。
   1. 從「 **第一個屬性名稱」的下拉式清單中選取****Googlesheets/value/1/2**

   1. 從下 **拉式選單中** ，選取「運算子」為「大於」**

   1. 選擇 **資料類型** ，作為 **數字**

   1. 從「 **第二個屬性名稱」(****Second Property name)的下拉式清單中，選取Googlesheets/value/1/0**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同樣地，請編輯比較屬性規則並新 **增至For_Blue** 區段，如下圖所示：

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同樣地，請編輯比較屬性規則並新增至** For_Green **segment，如下圖所示：

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   您會注意到，對於 **For_Green** 和 **** For_Green區段，無法在編輯器中載入資料，因為目前僅第一個比較與Google工作表中的值相同，有效。

1. 導覽並選取您的**DataDrivenRetail **channel（序列頻道），然後從動作列按 **一下「編輯** 」。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   您應該已使用「屬 **性」(Properties** ) **&gt;「個人化」(Personalization** **ContextHub)頁籤來設定ContextHub****** Configurations。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   如果您未在設定專案的「設定」下新增 **Brand** (品牌 **Configurations)，如上圖所示，則需要在設定** ContextHub Configurations時選取 ************ BrandBrandActivityActivity，同時在下一步驟開始定位程式時，選擇Targeting。

1. **新增預設影像**

   1. 新增預設影像至您的頻道，然後按一下「定 **位」**。
   1. 從下 **拉式選單選** 擇「品牌 **」和「活動** 」，然後按一下「開始 **定位」**。

   1. 按一下 **開始定位**。
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   在開始定位之前，您必須按一下從側邊欄上「**+新增體驗定位」，新增區段(** For_Green **、** For_Red **和** For_Blue **** )，如下圖所示。

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 將影像新增至所有三個不同的畫格，如下所示。

   ![retail_targeting](assets/retail_targeting.gif)

1. **勾選預覽**

   1. 按一下「 **預覽」。** 此外，請開啟您的Google工作表並更新其值。
   1. 變更所有三個不同欄的值，您會注意到顯示影像會根據庫存中的最高值而更新。
   ![retail_result](assets/retail_result.gif)

## 使用案例2:旅行中心氣象啟用 {#use-case-travel-center-weather-activation}

下列使用案例會根據您的Google工作表中的值，展示兩個不同的影像。

### 說明 {#description-1}

對於此使用案例，如果您的Google Sheets的「值」小於50，則會顯示含熱飲的影像，如果值大於或等於50，則會顯示含冷飲的影像。 若有其他值或無值，播放器將顯示預設影像。

### 過程 {#procedure-1}

請依照下列步驟，為您的AEM Screens專案實作旅行中心氣象啟用使用案例：

1. **填入Google工作表**

   1. 導覽至ContextHubDemo google工作表。
   1. 添加帶有 **Heading1的列** ，其中包含相應的溫度值。
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **根據需求在「對象」中設定區段**

   1. 導覽至對象中的區段(在步驟2的步驟(5)中 ***建立：設定AEM以擷取Google工作表的內容***)。
   1. 選擇「 **工作表A1 1** 」，然後單 **擊編輯**。

   1. 選擇比較屬性，然後按一下設定圖示以編輯屬性。
   1. 從屬 **性名稱的下拉式清單中選取** 「Googlesheets/value/1/0 **」**

   1. 從下 **拉式選單中** ，將運算子選為**大於或等於*

   1. 將值 **輸入** 50 **。**

   1. 同樣地，選擇**工作表A1 2 **並按一下「編 **輯」**。

   1. 選擇比較屬性，然後按一下設定圖示以編輯屬性。
   1. 從屬 **性名稱的下拉式清單中選取** 「Googlesheets/value/1/0 **」**

   1. 從下 **拉式選單中** ，選取「運算子」為「小於**」

   1. 將值 **輸入** 50 **。**

1. 導覽並選取您的頻道()，然後從動作 **列按一下** 「編輯」。 在下列範例中， **DataDrivenWeather**，會使用循序頻道來展示功能。

   >[!NOTE]
   您的頻道應已有預設影像，且應依步驟(3)所述預先設定觀眾

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   您應該已使用「屬 **性」(Properties** ) **&gt;「個人化」(Personalization** **ContextHub)頁籤來設定ContextHub****** Configurations。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

   >[!NOTE]
   如果您未在設定專案的「設定」下新增 **Brand** (品牌 **Configurations)，如上圖所示，則需要在設定** ContextHub Configurations時選取 ************ BrandBrandActivityActivity，同時在下一步驟開始定位程式時，選擇Targeting。

1. 從編 **輯器中選取** 「定位」，然後從下拉式選單中選取「品牌 **」和「活動** 」，然後按一下「 ********&#x200B;開始定位」。

   >[!NOTE]
   如果您在為項目設 **定** ContextHub配置時在「定位配置」下添加品牌 **，則無需在此步驟中選擇************** BrandBrand和Activity。

   ![new_activity3](assets/new_activity3.gif)

1. 勾選預覽

   1. 按一下「 **預覽」。** 此外，請開啟您的Google工作表並更新其值。
   1. 將值變更為小於50，您就可以檢視夏季飲品的影像。 如果Google Sheet中的值大於或等於50，則應該能夠檢視熱飲影像。
   ![result3](assets/result3.gif)

## 使用案例3:酒店預訂激活 {#use-case-hospitality-reservation-activation}

下列使用案例會根據Google工作表中套用的值和公式，顯示兩個不同的影像。

### 說明 {#description-2}

在此使用案例中，Google Sheet會填入兩間餐廳 **Restaurant1** 和 **Restaurant2的預訂百分比**。 公式會根據Restaurant1和Restaurant2的值套用，並根據公式，值1或2會指派給 **AdTarget** 欄。

如果 **Restaurant1** &gt; **Restaurant2**，則 **AdTaget值為1，否則****** AdTarget的值為2。 Value 1會產 *生Steak food* option（牛排食品），而Value 2會在顯示畫面 *上顯示Thai* food（泰式食品）選項。

### 程式方法 {#procedural-approach}

請依照下列步驟，為您的AEM Screens專案實作酒店預訂啟動使用案例：

1. 填入Google工作表並新增公式。

   例如，將公式套用至第三欄 **AdTarget**，如下圖所示。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **根據需求在「對象」中設定區段**

   1. 導覽至對象中的區段(在步驟2的步驟(5)中 ***建立：設定AEM以擷取Google工作表的內容***)。
   1. 選擇「 **工作表A1 1** 」，然後單 **擊編輯**。

   1. 選擇比較屬性，然後按一下設定圖示以編輯屬性。
   1. 從屬 **性名稱的下拉式清單中選取** 「Googlesheets/value/1/2 **」**

   1. 從下 **拉式選單中** ，將運算子選取為**equal **

   1. 將值 **輸入****為1**

   1. 同樣地，選擇**工作表A1 2 **並按一下「編 **輯」**。

   1. 選擇比較屬性，然後按一下設定圖示以編輯屬性。
   1. 從屬 **性名稱的下拉式清單中選取** 「Googlesheets/value/1/2 **」**

   1. 將運算 **元選** 為 **2**

1. 導覽並選取您的頻道()，然後從動作 **列按一下** 「編輯」。 在下列範例中 **,DataDrivenRestaurant**，會使用循序頻道來展示功能。

   >[!NOTE]
   您的頻道應已擁有預設影像，且應依照步驟(3)所述預先設定觀眾。

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   您應該已使用「屬 **性」(Properties** ) **&gt;「個人化」(Personalization** **ContextHub)頁籤來設定ContextHub****** Configurations。

   ![screen_shot_2019-05-08at14903pm](assets/screen_shot_2019-05-08at14903pm.png)

   >[!NOTE]
   如果您未在設定專案的「設定」下新增 **Brand** (品牌 **Configurations)，如上圖所示，則需要在設定** ContextHub Configurations時選取 ************ BrandBrandActivityActivity，同時在下一步驟開始定位程式時，選擇Targeting。

1. 從編 **輯器中選取** 「定位」，然後從下拉式選單中選取「品牌 **」和「活動** 」，然後按一下「 ********&#x200B;開始定位」。
1. 勾選預覽

   1. 按一下「 **預覽」。** 此外，請開啟您的Google工作表並更新其值。
   1. 變更Restaurant1 &gt; Restaurant2中的值，您應該可以檢視牛排圖片和Restaurant1 &lt; Restaurant12的影像，您應該可以在螢幕上檢視泰國美食圖片。
   ![result5](assets/result5.gif)

## 使用案例4:數位選單板文字覆蓋 {#use-case-digital-menu-board-text-overlay}

以下使用案例說明在餐館和快餐店中常見的數位選單板使用案例。

### 說明 {#description-3}

下列使用案例說明順序頻道中文字覆蓋的使用情形，以及Google工作表中價格值更新如何觸發文字覆蓋元件更新中的更新。

### 程式方法 {#procedural-approach-1}

請依照下列步驟，為您的AEM Screens專案實作包含文字覆蓋使用案例的數位選單板：

1. **填入Google工作表**

   1. 導覽至您的Google工作表。
   1. 為使用案例新增定價值的欄，如下圖所示。
   ![screen_shot_2019-05-05at111344am](assets/screen_shot_2019-05-05at111344am.png)

1. **將影像新增至序列色版**

   1. 導覽並選取您的頻道(**DataDrivenAssets** —&gt; **Channels** —&gt; **DataDrivenTextOverlay**)。

   1. 按一 **下動作列** 中的「編輯」以開啟編輯器。
   1. 在編輯器中拖放蘋果餅圖。
   ![screen_shot_2019-05-05at112933am](assets/screen_shot_2019-05-05at112933am.png)

1. **新增文字覆蓋至影像**

   1. 在編輯器中選擇影像，然後按一下「配置」。
   1. 導覽至「文 **字覆蓋** 」索引標籤，並新增文字覆蓋至影像。 若要從您的Google Sheets取得值，請確定值已包含在捲曲的字元中。 例如，從google工作表擷取價格，在定義文字覆蓋時， **會以{price}** 提及。

   1. 導覽至 **ContextHub** 標籤，並設定要從google工作表擷取的值，如下圖所示。
   ![textoverlay_result](assets/textoverlay_result.gif)

1. **勾選預覽**

   <!-- Edit text in steps below. wonky-->

   1. 按一下「 **預覽**」。  此外，請開啟您的Google工作表並更新其值。
   1. 變更「 **Price** 」（價格）下方的值，您會注意到文字覆蓋中所使用的值會隨之更新，如下圖所示。
   ![textoverlay_result-1](assets/textoverlay_result-1.gif)

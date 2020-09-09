---
title: 使用動態內嵌序列
seo-title: 使用動態內嵌序列
description: 請依照本頁瞭解如何在AEM Screens專案中實作動態內嵌序列。
seo-description: 請依照本頁瞭解如何在AEM Screens專案中實作動態內嵌序列。
uuid: 1f442489-2eeb-4dd8-b892-911fcccb3377
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: a40eb5bb-fbf7-4c0d-a34a-db79b884de8f
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '2535'
ht-degree: 1%

---


# 使用動態內嵌序列 {#using-dynamic-embedded-sequence}

使用動態內嵌序列涵蓋下列主題：

* **概覽**
* **在AEM畫面中使用動態內嵌體驗**
* **查看結果**
* **限制用戶和修改ACL**

## 概覽 {#overview}

***動態內嵌序列*** (Dynamic Embedded Sequences)是為遵循父項子項階層的大型專案所建立，其中子項在位置檔案夾而非頻道檔案夾中參考。 它可讓使用者透過渠道角色將序列內嵌 ***於渠道***。 它可讓使用者使用主頻道內的內嵌序列，為不同辦公室定義特定位置的預留位置。

將渠道指派給顯示時，您可以選擇指定顯示路徑或渠道的角色，以便根據上下文解析為實際渠道。

若要使用動態內嵌序列，請依頻道角色指 ***派頻道***。 渠道角色定義顯示的上下文。 角色由各種動作定位，且與實際執行角色的通道無關。 本節說明一個使用案例，可依角色定義渠道，以及如何將該內容運用到全域渠道。 您也可以將角色視為指派的識別碼，或在的上下文中為渠道的別名。

### 使用動態內嵌序列的優點 {#benefits-of-using-dynamic-embedded-sequences}

將序列頻道置於位置而非頻道資料夾的主要優點，是可讓本機或地區作者編輯與其相關的內容，同時不受階層上層編輯頻道的限制。

參照「依 *角色的頻道*」，可讓您建立頻道的本機版本，以便動態解析特定位置的內容，也可讓您建立全域頻道，運用特定位置頻道的內容。

>[!NOTE]
>
>**嵌入序列與動態嵌入序列**
>
>動態內嵌序列類似於內嵌序列，但允許使用者遵循階層，其中對一個頻道所做的變更／更新會傳播至相關的其他頻道。 它遵循父——子階層，也包含影像或視訊等資產。
>
>***「動態內嵌序列*** 」可讓您顯示特定位置的內容，而「內嵌 ***序列*** 」則只顯示內容的一般幻燈片。 此外，在設定動態內嵌序列時，您需要使用頻道角色和名稱來設定頻道。 如需實際實作，請參閱以下步驟。
>
>若要進一步瞭解如何實作內嵌序列，請參閱「AEM畫 [面中的內嵌](embedded-sequences.md) 序列」。

以下範例針對下列關鍵詞提供解決方案：

* 全 ***局序列的主序列*** (channel)
* ***動態內嵌序列元件*** ，用於序列中每個可本機自訂的部分
* ***個別序列頻道*** ，在顯示中具 *有與動態內嵌序列元* 件的角色相符的角 **色&#x200B;**。**

>[!NOTE]
>
>若要進一步瞭解頻道指派，請參閱「AEM畫面」文 **[件中「編寫」區段下的「頻道指派](channel-assignment.md)** 」。

## 使用動態內嵌序列 {#using-dynamic-embedded-sequence-2}

下節說明如何在AEM Screens頻道中建立動態內嵌序列。

### 必備條件 {#prerequisites}

開始實作此功能之前，請確定您已具備下列必要條件，可開始實作動態內嵌序列：

* 建立AEM Screens專案(在此範例中為 **Demo**)

* 在「頻道」資料夾 **下建立** 「 **全域** 」

* 將內容新增至 **全域頻道** (請&#x200B;*檢查&#x200B;**Resources.zip**，以取得相關資產*)

下圖顯示Channels資料 **夾中** ，具 **有Global Channel** （全域頻道）的Demo **專案** 。
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### 資源 {#resources}

您可以下載下列資源（影像並將這些資源新增至資產），並進一步將這些資源用作頻道內容以進行展示。

[取得檔案](assets/resources.zip)

>[!NOTE]
>
>如需如何建立專案以及如何建立序列頻道的詳細資訊，請參閱下列資源：
>
>* **[建立和管理專案](creating-a-screens-project.md)**
>* **[管理渠道](managing-channels.md)**

>



在AEM Screens專案中實作動態內嵌序列涉及三項主要工作：

1. **設定項目分類法，包括渠道、位置和顯示**
1. **建立排程**
1. **將排程指派給每個顯示**

請依照下列步驟來實作功能：

>[!CAUTION]
>
>在實作動態內嵌序列時，請在每個位置下建 **立頻道時** ，請留意 **「名稱」和「標題** 」欄位。 請謹慎遵循命名法的指示。

1. **建立兩個位置資料夾。**

   導覽至AEM Screens專案中的 **Locations** （位置）檔案夾，並建立兩個位置檔案夾，做 **為A** 和 **B地區**。

   >[!NOTE]
   >
   >在建立「 **地區A** 」位置資料夾時，請確保輸入「 **Title** as **Region A** 」資料夾，並且可以將 ******** Name欄位留空，以便自動提貨地區- A Name。
   >
   >類似地，建立位置資料夾 **Region B**，如下所示：

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >要瞭解如何建立位置，請參閱創 **[建和管理位置](managing-locations.md)**。

1. **在每個位置資料夾下建立兩個位置和一個頻道。**

   1. 導覽至 **演示** —>位 **置** —> **地區A**。
   1. 選擇 **地區A** ，然後從動作列 **按一下「+建立** 」。
   1. 從精 **靈中** ，選擇「 **Title** as **Store 1」（標題為商店1）**。 同樣地，從精靈中建立另一個名為「 **Store 2** 」(將Title（標題） **為「Store 2****」（商店2）的**&#x200B;位置。 在建立商店1和 **商店** 2時，您可將「名 **稱」欄位保留為空******。
   1. 重複步驟(b)，現在從精靈中選 **取「序列頻道** 」。 輸入「地 **區A** 」和「地區A名稱」, **作** 為此渠 **道的地** 區Title **** 渠道。

   >[!CAUTION]
   >
   >請確定在建立渠道 **A**&#x200B;時，輸入 **Title** as **Region A，輸入** Name Name ******** as region。

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   同樣地，在「地區B」下 **建立兩個名為** 「商店3 **」和「商店4」的** 位置 ****。 此外，請建立「序列 **渠道** 」, **其中「序列渠道」的** 「區域」為「B」,「 **名稱」**********&#x200B;為「區域」。

   >[!CAUTION]
   >
   >請確定您可以針對「地區A」和「地區B」中建立的頻道，使 **用相同的名稱** ，做 **為地** 區 ****。

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **在每個位置下建立顯示和頻道。**

   1. 導覽至 **Demo** —> **Locations** —> **A** — ****> Store 1區域。
   1. 選 **取「商店1** 」，然後從動作列按 **一下「+建立** 」。
   1. 從向 **導中選擇** 「顯示」並建立 **Store1Display。**
   1. 重複步驟(b)，此時從嚮導中選 **擇「序列通道** 」。 輸入 **Store** **1Channel的Title** , **Name** as store **Marked**。

   >[!CAUTION]
   >
   >當您建立序列頻道時，頻道的 **Title** （標題）可視您的需求，但是，所有本機頻道的 **Name** （名稱）應相同。
   >在此，在 **A** 和 **Region B** Store **ChareDobe Store 3Store PhidStore Phore 4Store下，與** Region Region B **Store************************** CharenAdChChareshamechameshan Shon Chan Phon Shon Shon Shon Shon Phon Phon Phon Shon Phon Shon Phon Shon Phon Phon Shon Shon Phon Shon Phon Ashan Phon Phon Phon Phon Phon Ashan B.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   同樣地，在「商店2 **」（名稱為「商店」）下，建立** Store2Display **和channel** Store2Channel的 ********&#x200B;顯示。

   >[!NOTE]
   >請確定您可以對在「商店1」和「商店2」中建立的頻道使 **用相同的名稱** ，以做為商店 ********。

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   請依照上述步驟建立渠道並顯示在「 **Store 3** 」和「 **Store 4** 」的「 **B區」下**。 同樣地，請務必在建立channel **** Store3Channel和 **Store4Channel時，使用與** store ******** 相同的名稱。

   下圖顯示 **Store 3中的顯示和頻道**。

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   下圖顯示 **Store 4中的顯示和頻道**。

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **將內容新增至各自位置的頻道。**

   導航至演示 **-** Demo **-** Locations **- >** Region A **-> Click Region And Edit Region****** from the Action 拖放您要新增至渠道的資產。

   >[!NOTE]
   >您可以使用上 ***述「資源」區段的******* Resources.zip檔案，將影像當做頻道內容的資產使用。

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   同樣地，導航至 **Demo** -> **Locations** -> **Region B** -> **B Region B** -> **Click Action and Edit action from the** the action to drag the assets and drop to your channel，如下所示：

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   請依照上述步驟和資源，將內容新增至下列頻道：

   * **Store1Channel**
   * **Store2Channel**
   * **Store3Channel**
   * **Store4Channel**

1. **建立排程**

   導覽並選取 **AEM Screens專案中的「排程** 」檔案夾，然後按一下動作列中的「 **建立** 」，以建立新的排程。

   下圖顯示在 **Demo專案中建立的AdSchedule** ( **AdSchedule** )。

   ![screen_shot_2018-09-13at3307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **將渠道指派給計畫**

   1. 導覽至 **Demo** —> **Schedules** —> **Ad Schedule** （演示計畫），然後從操作欄 **** 中按一下DashboardAdSchedule。
   1. 按一下 **+ 「從已分配的通道****」面板指定通道** ，開啟「通 **** 道分配」對話框。
   1. 選擇 **參考渠道**。 依路徑.
   1. 選擇「 **Channel Path** as **Demo** —> ***Channels*** — ***> Global*** Zhop」。
   1. 將渠道角 **色輸入為****GlobalAdSegment**。
   1. 選擇「受 **支援的事件** 」作 **為「初始載入**」、「 **空閒」螢幕**，以及「用戶 ****&#x200B;交互執行」。
   1. 按一下&#x200B;**「儲存」**。

   **按角色為地區分配渠道：**

   1. 按一下 **+ 「從已分配的通道****」面板指定通道** ，開啟「通 **** 道分配」對話框。
   1. 選擇 **參考渠道**。 依名稱.
   1. 輸入渠 **道名稱** ，作 **為地區***。
   1. 將渠道角 **色輸入** 「地 **區廣告區段」**。
   1. 按一下&#x200B;**「儲存」**。

   **依角色為商店指派渠道：**

   1. 按一下 **+ 「從已分配的通道****」面板指定通道** ，開啟「通 **** 道分配」對話框。
   1. 選擇 **參考渠道**。 依名稱.
   1. 輸入渠 **道名稱** ，作為 **商店**。
   1. 輸入渠 **道角色** ，作 **為StoreAdSegment**。
   1. 按一下&#x200B;**「儲存」**。

   下圖依路徑和角色顯示指派的頻道。

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **將動態內嵌序列設定為全域頻道。**

   導覽至您 **最初在** Demo **專案中建立的「全域頻道」** 。

   從動 **作按一下** 「編輯」以開啟編輯器。

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   在頻道編輯器中 **拖放兩個動態內嵌序列元件** 。

   從其中一個元件中開啟屬性，並將渠道分配角 **色輸入為** RegionAd **Segment**。

   同樣地，選擇其它元件並開啟屬性以將渠道分 **配角色輸入****為StoreAdSegment**。

   ![channeldisplay4](assets/channeldisplay4.gif)

1. **將排程指派給每個顯示**

   1. 導覽至每個顯示，例如 **A** —> **Locations** A **—>** Store 1Demo Store ********-> Demo1 Display Store。
   1. 從動 **作按一下** 「控制面板」，以開啟顯示控制面板。
   1. 按一 **下……** 從「指 **派渠道與排程」面板** ，然後按一 **下+指派排程**。
   1. 選擇「排程」的路徑(例如，此處， **Demo** —> **Schedules** —>**AdSchedule**)。
   1. 按一下&#x200B;**「儲存」**。

## 查看結果 {#viewing-the-results}

在您設定頻道和顯示完成後，請啟動AEM Screens播放器以檢視內容。

>[!NOTE]
>
>若要瞭解AEM Screen Player，請參閱下列資源：
>
>* [AEM Screens播放器下載](https://download.macromedia.com/screens/)
>* [使用AEM Screens Player](working-with-screens-player.md)



以下輸出會根據顯示路徑，確認您在AEM Screens播放器中的頻道內容。

**方案1**:

如果您將顯示路徑指派為 **A** —> **Locations** —> **Region A ——** Store 1Display Store ********— Following Accont，則AEM Screens player上將會顯示顯示該顯示路徑。

![channeldisplay1](assets/channeldisplay1.gif)

**方案1**:

如果您將顯示路徑指派為 **Adobe** —> **Locations** —> **Region B** —— — ******** Store 3 Display Store — Following Display Store，則會在您的AEM Screens播放器上顯示。

![channeldisplay2](assets/channeldisplay2.gif)

## 限制用戶和修改ACL {#restricting-users-and-modifying-the-acls}

您可以建立全域、地區或本機作者，以編輯與其相關的內容，同時限制您在階層的上方編輯頻道。

您需要修改ACL，以根據用戶的位置限制用戶訪問內容。

### 範例使用案例 {#example-use-case}

以下範例可讓您為上述Demo專案建立3位使用者。

將權限分配給每個組如下：

**群組**:

* **全域作者**:由可存取 **** Demo專案中所有位置和頻道，並擁有所有讀取、寫入和編輯權限的使用者組成。

* **地區——作者**:由具有「地區A」和「地區B」之讀取、寫入和編 **輯權限** 的 **使用者組成**。

* **商店——作者**:包含僅對 **Store 1**、 **Store 2**、 **Store 3**&#x200B;和 **** Store 4具有讀取、寫入和編輯權限的用戶。

#### 建立用戶組、用戶和設定ACL的步驟 {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>要詳細瞭解如何使用ACL分離項目，以便讓每個個人或團隊處理自己的項目，請參閱 **設定ACL**。

按照以下步驟建立組、用戶並根據權限修改ACL:

1. **建立群組**

   1. 導覽至 **Adobe Experience Manager**。
   1. Click **Tools** --> **Security** --> **Groups**.
   1. 按一 **下「建立群組** 」，然後在 **** ID中輸入Global-Author ****。
   1. 按一下&#x200B;**「儲存並關閉」**。

   同樣地，請建立其他兩個群 **組，例如Region-Author****和Store-Author**。

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **建立使用者並新增使用者至群組**

   1. 導覽至 **Adobe Experience Manager**。
   1. Click **Tools** --> **Security** --> **Users**.
   1. 按一 **下「建立使用者** 」，然後在 **** ID中輸入「全域使用者」 ****。
   1. 輸入 **密碼** ，並確認此用戶的密碼。
   1. 按一下「 **組** 」頁籤，並在「選擇組」中輸入組名，例如，輸入 **Global-Author**，將 ******** Global-UserAddited添加到特定組。
   1. 按一下&#x200B;**「儲存並關閉」**。

   同樣地，請建立其他兩個使用者， **例如Region-User****和** Store-User **，並分別將這些使用者新增至** Region-Author **和** Store-Author。

   >[!NOTE]
   >在群組中新增使用者，然後指派權限給每個特定使用者群組是最佳做法。

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **將所有群組新增至參與者**

   1. 導覽至 **Adobe Experience Manager**。
   1. Click **Tools** --> **Security** --> **Groups**.
   1. 從列 **表中選擇** 「參與者」，然後選擇「 **成員** 」頁籤。
   1. 選擇 **Group** ，如 **Global-Author**、 **Region-Author** 和 **** Store-Author to Contributor。
   1. 按一下&#x200B;**「儲存並關閉」**。

1. **存取每個群組的權限**

   1. 導覽至「使 *用者* 」，然後使用此UI修改不同群組的權限。
   1. 搜尋「全 **域作者」** ，然後按一 **下「權限** 」標籤，如下圖所示。
   1. 同樣地，您也可以存取「地 **區——作者」****和「商店——作者」的權限**。

   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **修改每個群組的權限**

   **針對全域作者：**

   1. 導覽至「權 **限** 」標籤
   1. 導覽至 ***/content/screens/demo*** ，並檢查所有權限
   1. 導覽至 ***/content/screens/demo/locations*** ，並檢查所有權限
   1. 導覽至 ***/content/screens/demo/locations/region-a*** ，並檢查所有權限。 同樣地，請檢查 **地區b的權限**。

   請參閱下圖以瞭解步驟：
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   下圖顯示 **User** Store **Global Store** 1,Global StoreA StoreDoreDoreDoreGlobalDoreDoreDoreGlobalDoreDobeDobeDoreADoreGioGioDGioGioDGioGionGioGioGionDDion **Gro An An GrioninDDDDD Grionion AnNN AnGinN** N **NNNAN** NinininNininADNNNNA **************** 4

   ![全域](assets/global.gif)

   **針對地區作者：**

   1. 導覽至「權 **限** 」標籤。
   1. 導覽至 ***/content/screens/demo*** ，並僅檢查「 **Read** 」權限。
   1. 導覽至 ***/content/screens/demo/locations*** ，並僅檢查「 **Read** 」（讀取）權限。
   1. 導覽至 ***/content/screens/demo/channels*** ，並取消檢查全域 **頻道的權限** 。
   1. 導覽至 ***/content/screens/demo/locations***/***region-a*** ，並檢查所有權限。 同樣地，請檢查 **地區b的權限**。

   請參閱下圖以瞭解步驟：

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   下面的圖片顯示，現在Region-User可以同時訪問 **A** 和 **B** Region Store **Store****************** Store 3StoreStore 3D And Store 4StoreDoreDores 4StoreJut Does不會訪問GlobalChe Chinal Chinanal Chananal Channel

   ![地區](assets/region.gif)

   **對於商店作者：**

   1. 導覽至「權 **限** 」標籤。
   1. 導覽至 ***/content/screens/demo*** ，並僅檢查「 **Read** 」權限。
   1. 導覽至 ***/content/screens/demo/locations*** ，並僅檢查「 **Read** 」（讀取）權限。
   1. 導覽至 ***/content/screens/demo/channels*** ，並取消檢查全域 **頻道的權限** 。
   1. 導覽至 ***/content/screens/demo/locations/region-a*** ，並僅檢查「 **Read** 」權限。 同樣地，請只勾選 **地區** b的 **「讀取」權限**。
   1. 導覽至 ***/content/screens/demo/locations***/***region-a /store-1*** ，並檢查所有權限。 同樣地，請檢查 **store-2、store-3** 和 **store-4的權限**。

   請參閱下圖以瞭解步驟：

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   下圖顯示， **Store-User** 只有4個 **Store 1**、 **Store 22、********************** Store 4Store、Store 4StoreGareGlobalDreagion(Global Dregion Ad A Drigion Ad B Chan)通道的存取範圍。

   ![商店](assets/store.gif)

>[!NOTE]
>
>要詳細瞭解設定權限的資訊，請參閱 [設定ACL](setting-up-acls.md)。


---
title: 在AEM畫面中設定作者和發佈
seo-title: 在AEM畫面中設定作者和發佈
description: AEM Screens架構類似傳統的AEM Sites架構。 內容是在AEM作者例項上編寫，然後轉送複製至多個發佈例項。 請依照本頁瞭解如何設定AEM畫面的作者和發佈。
seo-description: AEM Screens架構類似傳統的AEM Sites架構。 內容是在AEM作者例項上編寫，然後轉送複製至多個發佈例項。 請依照本頁瞭解如何設定AEM畫面的作者和發佈。
uuid: 0a6e87e7-0018-42ef-b484-9a3da61c636a
contentOwner: jsyal
content-type: reference
topic-tags: authoring
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: f2397d11-a18b-4779-b77b-5f99b797f40c
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 在AEM畫面中設定作者和發佈 {#configuring-author-and-publish-in-aem-screens}

本頁反白說明下列主題：

* **設定作者和發佈例項**
* **設定發佈拓撲**
* **管理出版物：將內容更新從作者傳送至裝置發佈**

## 必備條件 {#prerequisites}

在開始使用作者和發佈伺服器之前，您應具備下列相關知識：

* **AEM Topology**
* **建立和管理AEM畫面專案**
* **裝置註冊程式**

>[!NOTE]
>
>只有在您已安裝AEM 6.4 Screens Feature Pack 2時，才能使用此AEM Screens功能。 若要存取此功能套件，您必須聯絡Adobe支援並要求存取權。 一旦您擁有權限，就可從「套件共用」下載。

## 設定作者和發佈例項 {#configuring-author-and-publish-instances}

>[!NOTE]
>
>若要進一步瞭解作者和發佈架構概觀，以及內容如何在AEM作者例項上編寫，然後轉送複製至多個發佈例項，請參閱「作者和發佈架構概觀」 [](author-publish-architecture-overview.md)。

下節介紹如何在作者和發佈拓撲上設定複製代理。

您可以設定一個簡單範例，其中代管一個作者和兩個發佈例項：

* 作者—&gt; localhost:4502
* Publish 1(pub1)—&gt; localhost:4503
* Publish(pub2)—&gt; localhost:4504

## 在作者上設定複製代理 {#setting-replication-agents}

要建立複製代理，您必須學習如何建立標準複製代理。

螢幕需要3個複製代理：

1. **預設複製代&#x200B;***理(指定為&#x200B;***Standard Replication Agent**)
1. **螢幕複製代理**
1. **反向複寫代理**

### 步驟1:建立預設複製代理 {#step-creating-a-default-replication-agent}

按照以下步驟建立預設複製代理：

1. 導覽至您的AEM例項—&gt; hammer圖示—&gt; **Operations** —&gt; **Configuration**。

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. 從左側導 **航樹中** ，選擇「複製」。

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. 從「復 **制」資料夾中選擇** 「作者上的代理」 ，然後單 **擊「新建****** 」以建立新的標準複製代理。

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. 輸入「 **Title** and **Name** （標題和名稱）」以建立複製代理，然後按一下「 **Create**（建立）」。

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. 按一下右鍵複製代理，然後按一下 **開啟** ，編輯設定。

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. 按一下 **編輯** ，開啟「代理 **** 設定」對話框以輸入詳細資訊。

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. 導航至「傳 **輸** 」頁籤並輸入 **URI**、 **User** 和 **Password** Applord

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >您也可以複製和更名現有的預設複製代理。


#### 建立標準複製代理 {#creating-standard-replication-agents}

1. 為pub1建立標準複製代理（應已設定現成可用的預設代理）(例如， *https://&lt;hostname&gt;:4503/bin/receive?sling:authRequestLogin=1*)
1. 為pub2建立標準複製代理。 您可以複製pub1的rep代理，並通過更改傳輸配置中的埠來更新要用於pub2的傳輸。 (例如， *https://&lt;hostname&gt;:4504/bin/receive?sling:authRequestLogin=1*)

#### 建立螢幕複製代理 {#creating-screens-replication-agents}

1. 建立適用於pub1的AEM Screens複製代理。 現成可用，有一個名為「螢幕複製代理」，指向埠4503。 這必須啟用。
1. 建立適用於pub2的AEM Screens複製代理。 複製pub1的Screens複製代理，並將pub2的埠更改為4504。

#### 建立螢幕反向複製代理 {#creating-screens-reverse-replication-agents}

1. 為pub1建立標準反向複製代理。
1. 為pub2建立標準的反向複製代理。 您可以複製pub1的反向代表代理，並通過更改傳輸配置中的埠來更新要用於pub2的傳輸。

## 設定發佈拓撲 {#setting-up-publish-topology}

### 步驟1:設定Apache Sling Oak-Based Discovery {#step-configure-apache-sling-oak-based-discovery}

在拓撲中為所有Publish執行個體設定Apache Sling Oak-Based Discovery

針對每個發佈例項：

1. 導航到 `https://<host>:<port>/system/console/configMgr`
1. 選取 **Apache Sling Oak-Based Discovery Service** Configuration。
1. 更新拓撲連接器URL:新增所有參與發佈例項的URL，即 `https://localhost:4502/libs/sling/topology/connector`
1. 拓撲連接器白名單：適應涵蓋參與發佈實例的IP或子網
1. 啟 **用自動停止本地環路**

每個發佈實例的配置應相同，而自動停止本地循環可防止無限循環。

#### 步驟2:驗證發佈拓撲 {#step-verify-publish-topology}

對於任何「發佈」例項，請導覽至 `https://<host>:<port>/system/console/topology`。 您應看到拓撲中表示的每個發佈實例。

#### 步驟3:設定ActiveMQ Artemis群集 {#step-setup-activemq-artemis-cluster}

通過此步驟，可以為ActiveMQ Artemis群集建立加密口令。
拓撲中所有發佈實例的群集用戶和口令必須相同。 需要加密ActiveMQ Artemis配置的口令。 由於每個實例都有自己的加密密鑰，因此必須使用加密支援來建立加密的密碼字串。 然後，在ActiveMQ的OSGi配置中將使用加密的口令。

在每個發佈例項上：

1. 在OSGi控制台中，導航到 **MAIN** —&gt; **Crypto Support** (*https://&lt;host&gt;:&lt;port&gt;/system/console/crypto*)。
1. 在純文字檔案中鍵入所需的純文字檔案密碼（所有實例都相同） ****
1. 按一 **下保護**。
1. 將「受保護的 **文字」值複製** 到記事本或文字編輯器。 此值將用於ActiveMQ的OSGi配置中。

由於每個發佈實例預設具有唯一的加密密鑰，因此您需要在每個發佈實例上執行此步驟，並保存下次配置的唯一密鑰。

*例如*,

Pub1 - `{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`Pub2 - `{8d3d113c834cc4f52c2daee0da3cb0a21122a31f0138bfe4b70c9ead79415f41}`

#### 步驟4:激活ActiveMQ Artemis群集 {#step-activate-activemq-artemis-cluster}

在每個發佈例項上：

1. 導覽至OSGi config管理 *器https://&lt;host&gt;:&lt;port&gt;/system/console/configMgr*
1. 選擇 **Apache activeMQ Artemis JMS提供程式配置** 。
1. 更新下列項目：

* ***群集密碼***:（在每個個別實例中使用前一步驟的加密值）
* ***主題***:{name:'commands'，地址：'com.adobe.cq.screens.commands', maxConsumers:50}

#### 驗證ActiveMQ Artemis群集 {#verify-activemq-artemis-cluster}

請依照每個「發佈」例項的下列步驟：

1. 導航至「OSGi控制台」 -&gt;「主」&gt;「ActiveMQ Artemis」 `[https://localhost:4505/system/console/mq`。
1. 驗證並檢查以查看群集資訊&gt;拓撲&gt;節點=2、成員=2下的其他實例的埠。
1. 發送測試消息(在「Broker Information（代理資訊）」下螢幕頂部)
1. 在欄位中輸入下列變更：

   1. **目標**:/com.adobe.cq.screens/devTestTopic
   1. **文字**:Hello World
   1. 檢視每個例項的error.log，以查看訊息是否已在叢集中傳送及接收

>[!NOTE]
>
>導覽至OSGI主控台時，在前一步驟中儲存組態後可能需要幾秒鐘的時間。 您也可以檢查error.log以取得詳細資訊。

例如，在成功配置ActiveMQ Artemis伺服器時，將顯示以下映像。

如果未在 */system/console/mq中看到以下配置*，請導航至 */system/console/mq* ，然後按一下 **** Restart（重新啟動）以重新啟動代理。

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### 移除反向連結頁首需求 {#remove-referrer-header-requirement}

請遵循每個「發佈」例項的步驟：

1. 導覽至 **OSGi控制台** &gt;設 **定管理員**
1. 選取 **Apache Sling Referrer Filter**
1. 更新設定並 **勾選允許空白**

### 設定作者和發佈例項 {#configuring-author-and-publish-instance}

設定發佈主題後，您必須設定作者和發佈例項，才能檢視實作的實際結果：

>[!NOTE]
>
>**必備條件**
>
>若要開始使用此範例，請建立新的AEM Screens專案，然後在您的專案中建立位置、顯示和頻道。 將內容新增至您的頻道，並指派頻道至顯示器。

#### 步驟1:啟動AEM Screens Player（裝置） {#step-starting-an-aem-screens-player-device}

1. 啟動個別的瀏覽器視窗。
1. 使用網頁瀏覽器( *亦即*,Web Browser`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` )前往「畫面播放器」，或啟動AEM Screens應用程式。 當您開啟裝置時，會注意到裝置的狀態為未註冊。

>[!NOTE]
>
>您可以使用您下載的AEM Screens應用程式或使用網頁瀏覽器來開啟AEM Screens播放器。

#### 步驟2:在作者上註冊裝置 {#step-registering-a-device-on-author}

1. 前往或選 `https://localhost:4502/screens.html/content/screens/we-retail` 取您的專案，並導覽至「裝置&gt;裝置管理員」。
1. 選擇 **註冊設備**。
1. 按一 **下「裝置註冊** 」以檢視裝置。
1. 選擇要註冊的設備，然後按一下「 **Register Device（註冊設備）**」。
1. 驗證註冊代碼，然後按一下「 **驗證**」。
1. 輸入裝置的標題，然後按一下「 **註冊**」。

#### 步驟3:將設備指派給顯示 {#step-assigning-the-device-to-display}

1. 在前一 **步驟的對話方塊中** ，按一下「指定顯示」(Assign Display)。
1. 從「位置」檔案夾中選取渠道的顯 **示路徑** 。
1. 按一下 **指派**。
1. 按一下 **完成** ，完成該過程，現在已分配設備。

檢查您的播放器，您就會看到您在頻道中新增的內容。

#### 步驟4:發佈裝置設定以發佈例項 {#step-publishing-device-configuration-to-publish-instances}

**驗證設備**

之前，請執行以下步驟，確認設備ID。 若要驗證，請在CRXDELite中搜尋裝置ID，路徑為 */home/users/screens/{project}/devices*。

按照以下步驟複製設備用戶：

1. 導覽至使用者管理頁面(例如： `https://localhost:4502/useradmin`
1. 搜尋 **screens-devices-master群組**
1. 在群組上按一下滑鼠右鍵，然後按一下「啟 **動」**

>[!CAUTION]
>
>請勿啟動author-publish-screens-service，因為它是系統使用者，由作者工作使用。

您也可以從「裝置管理控制台」啟動裝置。 請遵循下列步驟：

1. 導覽至您的畫面專案—&gt; **裝置**。
1. 從動作列按一下「**裝置管理員**」。
1. 選取裝置，然後從動 **作列按一下** 「啟動」，如下圖所示。

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>或者，在啟動裝置後，您也可以從動作列按一下「**編輯伺服器URL **」來編輯或更新伺服器URL，如下圖所示，您的變更將傳播至AEM Screens播放器。

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### 發佈檢查清單 {#publishing-check-list}

以下幾點摘要了「發佈檢查」清單：

* *Screens Device User* —— 這會儲存為AEM使用者，並從「工具 **** &gt; **Security** &gt;使用者」啟 **動**。 使用者會在前面加上「畫面」，並加上長的序號字串。

* *專案* - AEM Screens專案。
* *位置* -設備所連接的位置。
* *頻道* -在位置顯示的一個或多個頻道
* *排程* -如果使用排程，請確定已發佈
* *位置、計畫和渠道資料夾* -如果相應資源位於資料夾內。

確認檢查清單後，您需要確認渠道中的下列變更／行為：

* 發佈裝置設定後，會開啟「畫面播放器」設定，並將它指向「發佈」例項。 此外，您也可以從裝置管理主控台啟動裝置。
* 在「作者」上更新某些頻道內容並加以發佈，並驗證已更新的頻道現在會顯示在AEM Screens播放器上。
* 將「畫面」播放器連接至不同的發佈例項並驗證上述行為。

#### 步驟5:在「管理面板」中指向裝置以發佈例項 {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. 從「螢幕」播放器檢視管理員UI，在左上角長按以開啟「管理」功能表、在您啟用觸控功能的AEM Screens播放器上，或使用滑鼠來開啟。
1. 按一下側 **面板** 中的「配置」(Configuration)選項。
1. 將作者例項變更為在 **Server中發佈例項**。

檢視AEM Screens播放器中的變更。

或者，您也可以使用下列步驟從裝置管理控制台更新／編輯伺服器URL:

1. 導覽至您的AEM Screens專案，然後選取「裝 **置** 」檔案夾。
1. 從動 **作列按一下「裝置管理器** 」。
1. 選取裝置，然後從動作列按一下「**編輯伺服器URL **」，如下圖所示，您的變更將會傳播至AEM Screens播放器。

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

## 管理出版物：將內容更新從作者傳送至裝置發佈 {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

您可以從AEM Screens發佈和取消發佈內容。 「管理出版物」功能可讓您將內容更新從作者傳送至裝置。 您可以針對整個AEM Screens專案，或僅針對其中一個頻道、位置、裝置、應用程式或排程發佈／取消發佈內容。

### 管理AEM Screens專案的出版物 {#managing-publication-for-an-aem-screens-project}

請依照下列步驟，將內容更新從作者傳送至AEM Screens專案的裝置：

1. 導覽至您的AEM Screens專案。
1. 從動 **作列按一下「管理出版物** 」，以發佈專案以發佈例項。

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. 將打 **開「管理出版物** 」嚮導。 您可以選取「 **動作** 」，也可以排程目前或之後的發佈時間。 按一 **下「下一步**」。

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. 選中該框以從「管理出版物」嚮導中選 **擇整個項目** 。

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. 從動 **作列按一下「+包含子項** 」，並取消勾選所有選項以發佈專案中的所有模組，然後按一下「新增以 **發佈** 」。

   >[!NOTE]
   >
   >預設情況下，將選中所有框，您必須手動取消選中這些框才能發佈項目中的所有模組。

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

1. 從「管 **理出版物** 」精靈 **按一下「發佈」。**

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >等待幾秒／分鐘，讓內容進入發佈執行個體。
   >
   >
   >使用 **更新離線內容管理出版物** (Manage Publication)是兩個步驟的程式，其步驟必須正確。
   >
   >
   >
   >    1. 如果在使用「管理出版物」進 **行發佈前觸發「更新離線內容** 」，工作流程 **將無法運作**。
      >
      >    
   1. 如果專案中沒有變更，而「更新離線內容」沒有變更，工作流程將 **無法運作**。
   >    1. 如果作者在管理出版物工作流程中按一下「發佈」按鈕後，未完成復製程式（內容仍在上傳至發佈例項），工作流程將無法運作。 ****


1. 在您完成管理出版物工作流程後，您必須觸發作者中的更新離線內容，以便在作者例項上離線建立更新。

   導覽至專案，然後從動作 **列按一下「更新離線內容** 」。 此動作會將相同的命令轉送至發佈例項，以便離線Zip也能在發佈例項上建立。

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)

   >[!CAUTION]
   >
   >您必須先發佈，然後觸發更新離線內容，如前面步驟所概述。

### 管理渠道的出版物 {#managing-publication-for-a-channel}

請依照下列步驟，將內容更新從作者傳送至AEM Screens專案中頻道的裝置：

>[!NOTE]
>
>只有在渠道中有變更時，才要遵循本節。 如果頻道在先前更新離線內容後沒有任何變更，則個別頻道的管理出版工作流程將無法運作。

1. 導覽至您的「畫面」專案，然後選取頻道。
1. 從動 **作列按一下「管理出版物** 」，以發佈渠道以發佈例項。

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. 將打 **開「管理出版物** 」嚮導。 您可以選取「 **動作** 」，也可以排程目前或之後的發佈時間。 按一 **下「下一步**」。

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. 從「管 **理出版物** 」精靈 **按一下「發佈」。**

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >等待幾秒／分鐘，讓內容進入發佈執行個體。

1. 在您完成管理出版物工作流程後，您必須觸發作者中的更新離線內容，以便在作者例項上離線建立更新。

   導覽至頻道控制面板，然後按一下「 **更新離線內容」**。 此動作會將相同的命令轉送至發佈例項，以便離線Zip也能在發佈例項上建立。

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >您必須先發佈，然後觸發更新離線內容，如前面步驟所概述。

### 頻道和裝置重新指派： {#channel-and-device-re-assignment}

如果您已重新指派裝置，則必須在裝置重新指派至新顯示後，同時發佈初始顯示和新顯示。

同樣地，如果您已重新指派渠道，則必須在將渠道重新指派至新顯示後，同時發佈初始顯示和新顯示。
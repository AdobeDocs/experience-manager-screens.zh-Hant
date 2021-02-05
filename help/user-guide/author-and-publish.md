---
title: 在AEM畫面中設定作者和發佈
seo-title: 在AEM畫面中設定作者和發佈
description: AEM Screens架構類似傳統的AEM Sites架構。 內容是在AEM作者例項上編寫，然後轉送複製至多個發佈例項。 請依照本頁瞭解如何設定AEM畫面的作者和發佈。
seo-description: AEM Screens架構類似傳統的AEM Sites架構。 內容是在AEM作者例項上編寫，然後轉送複製至多個發佈例項。 請依照本頁瞭解如何設定AEM畫面的作者和發佈。
translation-type: tm+mt
source-git-commit: 235aa979543455882c72fa262cf7320c4298de5e
workflow-type: tm+mt
source-wordcount: '1910'
ht-degree: 0%

---


# 在AEM Screens {#configuring-author-and-publish-in-aem-screens}中設定作者和發佈

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

>[!IMPORTANT]
>
>如果要將多個發佈實例與調度程式一起使用，則必須更新調度程式中的dispatcher.any檔案。 如需詳細資訊，請參閱[啟用嚴格作業](dispatcher-configurations-aem-screens.md#enable-sticky-session)。

## 設定作者和發佈例項{#configuring-author-and-publish-instances}

>[!NOTE]
>
>若要進一步瞭解作者和發佈架構概觀，以及如何在AEM作者例項上編寫內容，然後將內容轉送複製至多個發佈例項，請參閱[作者和發佈架構概觀](author-publish-architecture-overview.md)。

下節介紹如何在作者和發佈拓撲上設定複製代理。

您可以設定一個簡單範例，其中代管一個作者和兩個發佈例項：

* 作者—> localhost:4502
* Publish 1(pub1)—> localhost:4503
* Publish 2(pub2)—> localhost:4504

## 在作者{#setting-replication-agents}上設定複製代理

要建立複製代理，您必須學習如何建立標準複製代理。

螢幕需要3個複製代理：

1. **預設複製代 ***理(指*** 定為標準複製代理**)
1. **螢幕複製代理**
1. **反向複寫代理**

### 步驟1:建立預設複製代理{#step-creating-a-default-replication-agent}

按照以下步驟建立預設複製代理：

1. 導覽至您的AEM實例—>槌子圖示—> **Operations** —> **Configuration**。

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. 從左側導航樹中選擇&#x200B;**Replication**。

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. 從&#x200B;**Replication**&#x200B;資料夾中選擇&#x200B;**Agent on author** ，然後按一下&#x200B;**New**&#x200B;建立新的標準複製代理。

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. 輸入&#x200B;**Title**&#x200B;和&#x200B;**Name**&#x200B;以建立複製代理，然後按一下&#x200B;**Create**。

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. 按一下右鍵複製代理，然後按一下&#x200B;**開啟**&#x200B;以編輯設定。

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. 按一下&#x200B;**編輯**&#x200B;開啟&#x200B;**代理設定**&#x200B;對話框以輸入詳細資訊。

   >[!NOTE]
   >
   >用戶需要檢查&#x200B;**Enabled**&#x200B;以啟用複製代理。 您必須在「預設」、「螢幕」和「反向複製代理」上選中此選項。

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. 導航至&#x200B;**Transport**&#x200B;頁籤並輸入&#x200B;**URI**、**User**&#x200B;和&#x200B;**Password**。

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >您也可以複製和更名現有的預設複製代理。


#### 建立標準複製代理{#creating-standard-replication-agents}

1. 為pub1建立標準複製代理（應已設定現成可用的預設代理）(例如，*https://&lt;hostname>:4503/bin/receive?sling:authRequestLogin=1*)
1. 為pub2建立標準複製代理。 您可以複製pub1的rep代理，並通過更改傳輸配置中的埠來更新要用於pub2的傳輸。 (例如，*https://&lt;hostname>:4504/bin/receive?sling:authRequestLogin=1*)

#### 建立螢幕複製代理{#creating-screens-replication-agents}

1. 建立適用於pub1的AEM Screens複製代理。 現成可用，有一個名為「螢幕複製代理」，指向埠4503。 這必須啟用。
1. 建立適用於pub2的AEM Screens複製代理。 複製pub1的Screens複製代理，並將pub2的埠更改為4504。

#### 建立螢幕反向複製代理{#creating-screens-reverse-replication-agents}

1. 為pub1建立標準反向複製代理。
1. 為pub2建立標準的反向複製代理。 您可以複製pub1的反向代表代理，並通過更改傳輸配置中的埠來更新要用於pub2的傳輸。

## 設定發佈拓撲{#setting-up-publish-topology}

### 步驟1:設定Apache Sling Oak-Based Discovery {#step-configure-apache-sling-oak-based-discovery}

在拓撲中為所有Publish執行個體設定Apache Sling Oak-Based Discovery

針對每個發佈例項：

1. 導航到 `https://<host>:<port>/system/console/configMgr`
1. 選擇「**Apache Sling Oak-Based Discovery Service** Configuration」。
1. 更新拓撲連接器URL:新增所有參與發佈例項的URL，其為：
   * `https://localhost:4503/libs/sling/topology/connector`
   * `https://localhost:4504/libs/sling/topology/connector`
1. **拓撲連接器白名單**:適應涵蓋參與發佈實例的IP或子網
1. 啟用&#x200B;**自動停止本地環路**

每個發佈實例的配置應相同，而自動停止本地循環可防止無限循環。

#### 步驟2:驗證發佈拓撲{#step-verify-publish-topology}

對於任何發佈實例，請導航至`https://:/system/console/topology`。 應在&#x200B;**傳出拓撲連接器**&#x200B;下查看拓撲中表示的每個發佈實例。

#### 步驟3:設定ActiveMQ Artemis群集{#step-setup-activemq-artemis-cluster}

通過此步驟，可以為ActiveMQ Artemis群集建立加密口令。
拓撲中所有發佈實例的群集用戶和口令必須相同。 需要加密ActiveMQ Artemis配置的口令。 由於每個實例都有自己的加密密鑰，因此必須使用加密支援來建立加密的密碼字串。 然後，在ActiveMQ的OSGi配置中將使用加密口令。

在每個發佈例項上：

1. 在OSGi控制台中，導航至&#x200B;**MAIN** —> **加密支援**(`https://&lt;host&gt;:&lt;port&gt;/system/console/crypto`)。
1. 在&#x200B;**純文字檔案**&#x200B;中鍵入所需的純文字檔案密碼（所有實例都相同）
1. 按一下&#x200B;**Protect**。
1. 將值&#x200B;**Protected Text**&#x200B;複製到記事本或文字編輯器。 此值將用於ActiveMQ的OSGi配置中。

由於每個發佈實例預設具有唯一的加密密鑰，因此您需要在每個發佈實例上執行此步驟，並保存下次配置的唯一密鑰。

>[!NOTE]
>
>密碼應以大括弧開頭和結尾。 例如：
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### 步驟4:激活ActiveMQ Artemis群集{#step-activate-activemq-artemis-cluster}

在每個發佈例項上：

1. 導覽至OSGi Config Manager `https://&lt;host&gt;:&lt;port&gt;/system/console/configMgr`
1. 選擇「**Apache ActiveMQ Artemis JMS提供程式**&#x200B;配置」
1. 更新下列項目：

   * ***群集密碼***:（在每個個別實例中使用前一步驟的加密值）
   * ***主題***:{name:&#39;commands&#39;，地址：&#39;com.adobe.cq.screens.commands&#39;, maxConsumers:50}

#### 驗證ActiveMQ Artemis群集{#verify-activemq-artemis-cluster}

請依照每個「發佈」例項的下列步驟：

1. 導航至「OSGi控制台->主> ActiveMQ Artemis `https://localhost:4505/system/console/mq`」。
1. 驗證並檢查以查看群集資訊>拓撲>節點=2、成員=2下的其他實例的埠。
1. 發送測試消息(在「Broker Information（代理資訊）」下螢幕頂部)
1. 在欄位中輸入下列變更：

   1. **目標**:/com.adobe.cq.screens/devTestTopic
   1. **文字**:Hello World
   1. 檢視每個例項的error.log，以查看消息是否在群集中發送和接收

>[!NOTE]
>
>在前述步驟中儲存設定後，導覽至OSGi主控台可能需要幾秒鐘的時間。 您也可以檢查error.log以取得詳細資訊。

例如，在成功配置ActiveMQ Artemis伺服器時，將顯示以下映像。

如果未在&#x200B;*/system/console/mq*&#x200B;中看到以下配置，請導航至&#x200B;*/system/console/mq* ，然後按一下&#x200B;**Restart**&#x200B;重新啟動代理。

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### 移除反向連結頁首要求{#remove-referrer-header-requirement}

請遵循每個「發佈」例項的步驟：

1. 導航至&#x200B;**OSGi控制台** > **配置管理器**
1. 選取&#x200B;**Apache Sling Referrer Filter**
1. 更新配置和&#x200B;**選中允許空**

### 設定作者和發佈例項{#configuring-author-and-publish-instance}

在設定發佈拓撲後，您需要配置作者和發佈實例，以查看實施的實際結果：

>[!NOTE]
>
>**必備條件**
>
>若要開始使用此範例，請建立新的AEM Screens專案，然後在您的專案中建立位置、顯示和頻道。 將內容新增至您的頻道，並指派頻道至顯示器。

#### 步驟1:啟動AEM Screens Player(device){#step-starting-an-aem-screens-player-device}

1. 啟動個別的瀏覽器視窗。
1. 使用&#x200B;*網頁瀏覽器*&#x200B;移至「畫面播放器」，即`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html`或啟動AEM Screens應用程式。 當您開啟裝置時，會注意到裝置的狀態為未註冊。

>[!NOTE]
>
>您可以使用您下載的AEM Screens應用程式或使用網頁瀏覽器來開啟AEM Screens播放器。

#### 步驟2:在作者上註冊設備{#step-registering-a-device-on-author}

1. 前往`https://localhost:4502/screens.html/content/screens/we-retail`或選取專案，然後導覽至「裝置>裝置管理員」。
1. 選擇&#x200B;**註冊設備**。
1. 按一下&#x200B;**設備註冊**&#x200B;查看設備。
1. 選擇要註冊的設備，然後按一下&#x200B;**註冊設備**。
1. 驗證註冊代碼，然後按一下&#x200B;**驗證**。
1. 輸入裝置的標題，然後按一下「註冊」。****

#### 步驟3:將設備分配給顯示{#step-assigning-the-device-to-display}

1. 從上一步的對話方塊中，按一下「指定顯示」。****
1. 從&#x200B;**Locations**&#x200B;資料夾中選取頻道的顯示路徑。
1. 按一下&#x200B;**Assign**。
1. 按一下&#x200B;**完成**&#x200B;以完成該過程，現在已分配設備。

檢查您的播放器，您就會看到您在頻道中新增的內容。

#### 步驟4:發佈裝置設定以發佈例項{#step-publishing-device-configuration-to-publish-instances}

**驗證設備**

之前，請執行以下步驟，確認設備ID。 若要驗證，請在CRXDE Lite中搜尋裝置ID，路徑為&#x200B;*/home/users/screens/we-retail/devices*。

按照以下步驟複製設備用戶：

1. 導覽至使用者管理頁面(例如：`https://localhost:4502/useradmin`
1. 搜尋&#x200B;**screens-devices-master**&#x200B;群組
1. 在群組上按一下滑鼠右鍵，然後按一下「啟動&#x200B;**」**

>[!CAUTION]
>
>請勿啟動author-publish-screens-service，因為它是系統使用者，由作者工作使用。

您也可以從「裝置管理控制台」啟動裝置。 請遵循下列步驟：

1. 導覽至您的畫面專案—> **裝置**。
1. 從操作欄中按一下&#x200B;**設備管理器**。
1. 選擇設備，然後按一下操作欄中的&#x200B;**激活** ，如下圖所示。

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>或者，在啟動裝置後，您也可以按一下動作列上的「編輯伺服器URL **」來編輯或更新伺服器URL，如下圖所示，您的變更將會傳播至AEM Screens播放器。**

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### 發佈檢查清單{#publishing-check-list}

以下幾點摘要了「發佈檢查」清單：

* *Screens Device User* - This is stored as an AEM user **, be activated from** Tools **>** Security **>** Users.使用者會在前面加上「畫面」，並加上長的序號字串。

* *專案* - AEM Screens專案。
* *位置* -設備所連接的位置。
* *頻道* -在該位置顯示的一個或多個頻道
* *排程* -如果使用排程，請確定已發佈
* *位置、計畫和渠道資料夾* -如果相應資源位於資料夾內。

請依照下列步驟來驗證作者／發佈行為：

1. 在作者實例上更新某些頻道內容
1. 執行&#x200B;**管理出版物**，將所有新變更發佈到所有發佈實例
1. 按&#x200B;**啟動**&#x200B;從&#x200B;**設備管理器**&#x200B;啟動設備
1. **編輯** URL從作者例項URL到其中一個發佈例項URL
1. 驗證AEM Screens播放器上顯示的已更新頻道內容
1. 使用不同的發佈實例重複這些步驟


#### 步驟5:在「管理面板{#step-pointing-the-device-to-publish-instance-in-the-admin-panel}」中指向裝置以發佈例項

1. 從「螢幕」播放器檢視管理員UI，在左上角長按以開啟「管理」功能表、在您啟用觸控功能的AEM Screens播放器上，或使用滑鼠來開啟。
1. 按一下側面板中的&#x200B;**Configuration**&#x200B;選項。
1. 將作者實例更改為在&#x200B;**Server**&#x200B;中發佈實例。

檢視AEM Screens播放器中的變更。

或者，您也可以使用下列步驟從裝置管理控制台更新／編輯伺服器URL:

1. 導覽至您的AEM Screens專案，然後選取&#x200B;**Devices**&#x200B;檔案夾。
1. 從操作欄中按一下&#x200B;**設備管理器**。
1. 選取裝置，然後從動作列按一下「編輯伺服器URL **」，如下圖所示，您的變更將會傳播至AEM Screens播放器。**

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

**管理出版物**&#x200B;功能可讓您將內容更新從作者傳送至裝置。 您可以針對整個AEM Screens專案，或僅針對其中一個頻道、位置、裝置、應用程式或排程來發佈／取消發佈內容。 若要進一步瞭解此功能，請參閱[隨選內容更新](on-demand-content.md)。



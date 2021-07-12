---
title: 在AEM Screens中設定作者和發佈
seo-title: 在AEM Screens中設定作者和發佈
description: AEM Screens架構類似傳統AEM Sites架構。 內容是在AEM製作例項上製作，然後轉送複製到多個發佈例項。 請詳閱本頁，了解如何為AEM Screens設定作者和發佈。
seo-description: AEM Screens架構類似傳統AEM Sites架構。 內容是在AEM製作例項上製作，然後轉送複製到多個發佈例項。 請詳閱本頁，了解如何為AEM Screens設定作者和發佈。
feature: 管理畫面
role: Admin, Developer
level: Intermediate
exl-id: 5aef5f35-d946-4bf8-a2a8-c3ed532b7eef
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1907'
ht-degree: 0%

---

# 在AEM Screens中設定作者和發佈 {#configuring-author-and-publish-in-aem-screens}

本頁面重點說明下列主題：

* **設定製作和發佈例項**
* **設定發佈拓撲**
* **管理發布：將內容更新從作者傳送至裝置**

## 必備條件 {#prerequisites}

開始使用作者和發佈伺服器之前，您應先了解：

* **AEM拓撲**
* **建立和管理AEM Screens專案**
* **設備註冊過程**

>[!NOTE]
>
>只有在您已安裝AEM 6.4 Screens Feature Pack 2時，才能使用此AEM Screens功能。 若要存取此Feature Pack，您必須聯絡Adobe支援並要求存取權。 擁有權限後，您就可以從「封裝共用」下載。

>[!IMPORTANT]
>
>如果您想要與Dispatcher搭配使用多個發佈例項，必須更新Dispatcher.any檔案。 如需詳細資訊，請參閱[啟用嚴格工作階段](dispatcher-configurations-aem-screens.md#enable-sticky-session)。

## 設定製作和發佈例項 {#configuring-author-and-publish-instances}

>[!NOTE]
>
>若要深入了解製作和發佈架構概觀，以及如何在AEM製作例項上製作內容，然後轉送至多個發佈例項，請參閱[製作和發佈架構概觀](author-publish-architecture-overview.md)。

以下章節說明如何在製作和發佈拓撲上設定復寫代理。

您可以設定一個簡單範例，在其中托管一個製作和兩個發佈例項：

* 作者 — > localhost:4502
* Publish 1(pub1)—> localhost:4503
* Publish 2(pub2)—> localhost:4504

## 在作者上設定復寫代理 {#setting-replication-agents}

要建立複製代理，您必須了解如何建立標準複製代理。

Screens需要3個複製代理：

1. **預設復寫代 ***理(指*** 定為標準復寫代理**)
1. **Screens複製代理**
1. **反向複寫代理**

### 步驟1:建立預設複製代理 {#step-creating-a-default-replication-agent}

請按照以下步驟建立預設複製代理：

1. 導航到AEM實例 — >錘表徵圖 — > **Operations** —> **Configuration**。

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. 從左側導航樹中選擇&#x200B;**Replication**。

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. 從&#x200B;**Replication**&#x200B;資料夾中選擇作者&#x200B;**上的代理，然後按一下**&#x200B;新建&#x200B;**以建立新的標準複製代理。**

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. 輸入&#x200B;**Title**&#x200B;和&#x200B;**Name**&#x200B;以建立複製代理，然後按一下&#x200B;**Create**。

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. 按一下右鍵複製代理，然後按一下&#x200B;**開啟**&#x200B;以編輯設定。

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. 按一下&#x200B;**編輯**&#x200B;以開啟&#x200B;**代理設定**&#x200B;對話框以輸入詳細資訊。

   >[!NOTE]
   >
   >用戶需要檢查&#x200B;**Enabled**&#x200B;以啟用複製代理。 您必須在「預設」、「螢幕」和「反向復寫代理」上核取此選項。

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. 導航到&#x200B;**Transport**&#x200B;頁簽，然後輸入&#x200B;**URI**、**User**&#x200B;和&#x200B;**Password**。

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >您也可以複製和重新命名現有的預設復寫代理。


#### 建立標準復寫代理  {#creating-standard-replication-agents}

1. 為pub1建立標準復寫代理（應已設定現成預設代理）(例如&#x200B;*https://&lt;hostname>:4503/bin/receive?sling:authRequestLogin=1*)
1. 為pub2建立標準複製代理。 您可以複製pub1的rep代理，並通過更改傳輸配置中的埠來更新要用於pub2的傳輸。 (例如， *https://&lt;hostname>:4504/bin/receive?sling:authRequestLogin=1*)

#### 建立Screens復寫代理 {#creating-screens-replication-agents}

1. 為pub1建立AEM Screens復寫代理。 現成可用，有一個名為Screens Replication Agent ，指向埠4503。 這必須啟用。
1. 為pub2建立AEM Screens復寫代理。 複製pub1的Screens復寫代理，並將pub2的埠更改為指向4504。

#### 建立Screens反向復寫代理 {#creating-screens-reverse-replication-agents}

1. 為pub1建立標準反向複製代理。
1. 為pub2建立標準反向複製代理。 您可以複製pub1的反向rep代理，並通過更改傳輸配置中的埠來更新要用於pub2的傳輸。

## 設定發佈拓撲 {#setting-up-publish-topology}

### 步驟1:設定Apache Sling Oak-Based Discovery {#step-configure-apache-sling-oak-based-discovery}

為拓撲中的所有發佈執行個體設定Apache Sling Oak-Based Discovery

對於每個發佈例項：

1. 導航到 `https://<host>:<port>/system/console/configMgr`
1. 選擇&#x200B;**Apache Sling Oak-Based Discovery Service**&#x200B;設定。
1. 更新拓撲連接器URL:新增所有參與發佈例項的URL，其為：
   * `https://localhost:4503/libs/sling/topology/connector`
   * `https://localhost:4504/libs/sling/topology/connector`
1. **拓撲連接器白名單**:適應涵蓋參與發佈實例的IP或子網
1. 啟用&#x200B;**自動停止本地循環**

每個發佈例項的設定應相同，而自動停止本機回圈可防止無限回圈。

#### 步驟2:驗證發佈拓撲 {#step-verify-publish-topology}

對於任何發佈例項，請導覽至`https://:/system/console/topology`。 您應該會在&#x200B;**傳出拓撲連接器**&#x200B;下看到拓撲中表示的每個發佈實例。

#### 步驟3:安裝ActiveMQ Artemis群集 {#step-setup-activemq-artemis-cluster}

此步驟允許您為ActiveMQ Artemis群集建立加密的密碼。
拓撲中所有發佈實例的群集用戶和口令必須相同。 需要加密ActiveMQ Artemis配置的密碼。 由於每個實例都有各自的加密密鑰，因此必須使用加密支援來建立加密的密碼字串。 然後，在ActiveMQ的OSGi配置中將使用加密的密碼。

在每個發佈例項上：

1. 在OSGi控制台中，導航到&#x200B;**MAIN** —> **Crypto Support**(`https://&lt;host&gt;:&lt;port&gt;/system/console/crypto`)。
1. 在&#x200B;**純文字**&#x200B;中鍵入所需的純文字密碼（對於所有實例均相同）
1. 按一下&#x200B;**Protect**。
1. 將值&#x200B;**Protected Text**&#x200B;複製到記事本或文字編輯器。 此值將用於ActiveMQ的OSGi配置中。

由於每個發佈實例預設具有唯一的加密密鑰，因此您需要在每個發佈實例上執行此步驟，並保存下次配置時的唯一密鑰。

>[!NOTE]
>
>密碼的開頭和結尾應為大括弧。 例如：
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### 步驟4:激活ActiveMQ Artemis群集 {#step-activate-activemq-artemis-cluster}

在每個發佈例項上：

1. 導覽至OSGi設定管理員`https://&lt;host&gt;:&lt;port&gt;/system/console/configMgr`
1. 選擇&#x200B;**Apache ActiveMQ Artemis JMS提供程式**&#x200B;配置
1. 更新下列項目：

   * ***群集密碼***:為每個個別執行個體使用上一步的加密值
   * ***主題***:  `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### 驗證ActiveMQ Artemis群集 {#verify-activemq-artemis-cluster}

在每個Publish執行個體上遵循下列步驟：

1. 導航到OSGi控制台 — >主> ActiveMQ目標`https://localhost:4505/system/console/mq`。
1. 驗證並檢查以查看群集資訊>拓撲>節點=2,members=2下的其他實例的埠。
1. 發送測試消息（在螢幕頂部的「代理資訊」下）
1. 在欄位中輸入下列變更：

   1. **目的地**:/com.adobe.cq.screens/devTestTopic
   1. **文字**:《你好世界》
   1. 查看每個實例的error.log ，以查看該消息是否已在群集中發送和接收

>[!NOTE]
>
>在前一步驟中儲存設定後，導覽至OSGi主控台可能需要數秒的時間。 您也可以查看error.log以取得詳細資訊。

例如，成功配置ActiveMQ Artemis Server時將顯示以下映像。

如果未在&#x200B;*/system/console/mq*&#x200B;中看到以下配置，請導航至&#x200B;*/system/console/mq*，然後按一下&#x200B;**重新啟動**&#x200B;以重新啟動代理。

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### 移除反向連結標題需求 {#remove-referrer-header-requirement}

請依照每個Publish例項上的步驟操作：

1. 導覽至&#x200B;**OSGi Console** > **Configuration Manager**
1. 選取&#x200B;**Apache Sling Referrer Filter**
1. 更新配置並檢查「允許空&#x200B;**」**

### 設定製作和發佈例項 {#configuring-author-and-publish-instance}

設定發佈拓撲後，您需要配置製作和發佈實例，以查看實施的實際結果：

>[!NOTE]
>
>**必備條件**
>
>若要開始使用此範例，請建立新的AEM Screens專案，然後在專案中建立位置、顯示和管道。 新增內容至頻道，並將頻道指派給顯示器。

#### 步驟1:啟動AEM Screens播放器（裝置） {#step-starting-an-aem-screens-player-device}

1. 啟動個別的瀏覽器視窗。
1. 使用&#x200B;*網頁瀏覽器*（即`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html`）前往Screens播放器，或啟動AEM Screens應用程式。 當您開啟設備時，您會注意到設備的狀態為未註冊。

>[!NOTE]
>
>您可以使用下載的AEM Screens應用程式或使用網頁瀏覽器開啟AEM Screens播放器。

#### 步驟2:在作者上註冊裝置 {#step-registering-a-device-on-author}

1. 前往`https://localhost:4502/screens.html/content/screens/we-retail`或選取您的專案，然後導覽至「裝置>裝置管理員」。
1. 選擇&#x200B;**註冊設備**。
1. 按一下&#x200B;**設備註冊**&#x200B;查看設備。
1. 選擇要註冊的設備，然後按一下&#x200B;**註冊設備**。
1. 驗證註冊代碼，然後按一下&#x200B;**Validate**。
1. 輸入設備的標題，然後按一下&#x200B;**註冊**。

#### 步驟3:為顯示指定設備 {#step-assigning-the-device-to-display}

1. 按一下前一步驟的對話框中的&#x200B;**指定顯示**。
1. 從&#x200B;**Locations**&#x200B;資料夾中選取通道的顯示路徑。
1. 按一下&#x200B;**Assign**。
1. 按一下&#x200B;**完成**&#x200B;以完成該過程，現在已分配設備。

檢查您的播放器，您就會看到您在頻道中新增的內容。

#### 步驟4:將裝置配置發佈到發佈實例 {#step-publishing-device-configuration-to-publish-instances}

**驗證設備**

之前，請執行下列步驟，確認裝置ID。 若要驗證，請在CRXDE Lite中搜尋裝置ID，路徑為&#x200B;*/home/users/screens/we-retail/devices*。

請按照以下步驟複製設備用戶：

1. 導覽至使用者管理頁面(例如：`https://localhost:4502/useradmin`
1. 搜索&#x200B;**screens-devices-master**&#x200B;組
1. 按一下右鍵組，然後按一下&#x200B;**激活**

>[!CAUTION]
>
>請勿啟動author-publish-screens-service，因為它是系統使用者，供作者工作使用。

您也可以從「裝置管理控制台」啟動裝置。 請遵循下列步驟：

1. 導覽至您的Screens專案 — > **裝置**。
1. 按一下操作欄中的&#x200B;**設備管理器**。
1. 選擇設備，然後按一下操作欄中的&#x200B;**激活**，如下圖所示。

![screen_shot_2019-02-21at111036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>或者，在激活設備後，您也可以按一下操作欄中的&#x200B;**編輯伺服器URL**&#x200B;來編輯或更新伺服器URL，如下圖所示，您的更改將傳播到AEM Screens播放器。

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### 發佈檢查清單 {#publishing-check-list}

以下幾點匯總了「發佈檢查」清單：

* *Screens裝置使用者*  — 這會儲存為AEM使用者，並從「工具 **>** 安全性 **>** 使用者」 ****&#x200B;啟用。使用者會加上前置詞「screens」，並加上長序列化字串。

* *專案*  -AEM Screens專案。
* *位置*  — 裝置所連線的位置。
* *管道*  — 在位置顯示的一或多個管道
* *排程*  — 如果使用排程，請確定已發佈
* *位置、排程和管道資料夾*  — 如果對應的資源位於資料夾內。

請依照下列步驟來驗證作者/發佈行為：

1. 更新製作例項上的某些管道內容
1. 執行&#x200B;**管理出版物**&#x200B;以發佈所有發佈實例的新更改
1. 按&#x200B;**激活**&#x200B;從&#x200B;**設備管理器**&#x200B;激活設備
1. **編** 輯從製作例項URL到其中一個發佈例項URL的URL
1. 驗證AEM Screens播放器上顯示的更新頻道內容
1. 使用不同的發佈例項重複這些步驟


#### 步驟5:在「管理面板」中指向裝置以發佈例項 {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. 從Screens播放器檢視管理員UI，在左上角長按以開啟「管理員」功能表、啟用觸控的AEM Screens播放器，或使用滑鼠。
1. 按一下側面板中的&#x200B;**Configuration**&#x200B;選項。
1. 在&#x200B;**Server**&#x200B;中將製作例項變更為發佈例項。

檢視AEM Screens播放器中的變更。

或者，您也可以使用下列步驟從裝置管理控制台更新/編輯伺服器URL:

1. 導覽至您的AEM Screens專案，並選取&#x200B;**Devices**&#x200B;資料夾。
1. 按一下操作欄中的&#x200B;**設備管理器**。
1. 選取裝置，然後按一下動作列中的&#x200B;**編輯伺服器URL**，如下圖所示，您的變更將會傳播至AEM Screens播放器。

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

**管理出版物**&#x200B;功能可讓您將內容更新從作者傳送至裝置，以發佈至裝置。 您可以發佈/取消發佈整個AEM Screens專案的內容，或僅發佈其中一個管道、位置、裝置、應用程式或排程的內容。 若要深入了解此功能，請參閱[隨需內容更新](on-demand-content.md)。

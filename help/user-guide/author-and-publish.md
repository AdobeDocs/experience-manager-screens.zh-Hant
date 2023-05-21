---
title: 在AEM Screens配置作者和發佈
description: AEM Screens的建築與AEM Sites的傳統建築很相似。 內容在作者實例AEM上創作，然後轉發複製到多個發佈實例。 請按照本頁瞭解如何為AEM Screens配置作者和發佈。
exl-id: 5aef5f35-d946-4bf8-a2a8-c3ed532b7eef
source-git-commit: ab959584c01c10f76c231ab89b574886ad7346c5
workflow-type: tm+mt
source-wordcount: '1988'
ht-degree: 0%

---


# 在AEM Screens配置作者和發佈 {#configuring-author-and-publish-in-aem-screens}

此頁突出顯示以下主題：

* **配置作者和發佈實例**
* **設定發佈拓撲**
* **管理發布：將內容更新從作者傳送到設備**

## 必備條件 {#prerequisites}

在開始使用作者和發佈伺服器之前，您應先瞭解：

* **拓AEM撲**
* **建立和管理AEM Screens項目**
* **設備註冊過程**

>[!NOTE]
>
>只有安裝了6.4螢幕功能包2AEM時，此AEM Screens功能才可用。 要訪問此功能包，必須聯繫Adobe支援並請求訪問。 擁有權限後，您可以從包共用下載它。

>[!IMPORTANT]
>
>如果要將多個發佈實例與調度程式一起使用，則必須更新調度程式中的dispatcher.any檔案。 請參閱 [啟用粘滯會話](dispatcher-configurations-aem-screens.md#enable-sticky-session) 的子菜單。

## 配置作者和發佈實例 {#configuring-author-and-publish-instances}

>[!NOTE]
>
>要瞭解有關作者的詳細資訊並發佈體系結構概述，以及如何在作者實例上創AEM作內容，然後將內容轉發複製到多個發佈實例，請參閱 [作者和發佈體系結構概述](author-publish-architecture-overview.md)。

下節介紹如何在作者和發佈拓撲上設定複製代理。

您可以設定一個簡單的示例，在其中托管一個作者和兩個發佈實例：

* 作者 — > localhost:4502
* 發佈1(pub1)—> localhost:4503
* 發佈2(pub2)—> localhost:4504

## 在作者上設定複製代理 {#setting-replication-agents}

要建立複製代理，必須瞭解如何建立標準複製代理。

螢幕需要3個複製代理：

1. **預設複製代理 ***(指定為*** 標準複製代理**)
1. **螢幕複製代理**
1. **反向複寫代理**

### 步驟1:建立預設複製代理 {#step-creating-a-default-replication-agent}

按照以下步驟建立預設複製代理：

1. 導航到AEM實例 — >錘表徵圖 — > **操作** —> **配置**。

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. 選擇 **複製** 的下界。

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. 選擇 **作者代理** 從 **複製** 資料夾，按一下 **新建** 建立新的標準複製代理。

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. 輸入 **標題** 和 **名稱** 建立複製代理，然後按一下 **建立**。

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. 按一下右鍵複製代理，然後按一下 **開啟** 按鈕。

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. 按一下 **編輯** 開啟 **代理設定** 對話框。

   >[!NOTE]
   >
   >用戶需要檢查 **已啟用** 啟用複製代理。 必須在「預設」、「螢幕」和「反向複製代理」上選中此選項。

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. 導航到 **運輸** ，然後輸入 **URI**。 **用戶** 和 **密碼**。

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >您還可以複製和更名現有的預設複製代理。


#### 建立標準複製代理  {#creating-standard-replication-agents}

1. 為pub1建立標準複製代理（應已配置現成預設代理）(例如， *https://&lt;hostname>:4503/bin/receive?sling:authRequestLogin=1*)
1. 為pub2建立標準複製代理。 您可以複製pub1的複製代理，並通過更改傳輸配置中的埠來更新用於pub2的傳輸。 (例如， *https://&lt;hostname>:4504/bin/receive?sling:authRequestLogin=1*)

#### 建立螢幕複製代理 {#creating-screens-replication-agents}

1. 為pub1建立螢幕複製代理。 出廠時，有一個名為Screens Replication Agent的代理，它指向埠4503。 這需要啟用。
1. 為pub2建立螢幕複製代理。 複製pub1的螢幕複製代理，並將pub2的埠更改為4504。

   >[!NOTE]
   >要瞭解如何配置螢幕複製代理，請參見 [配置螢幕複製代理](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/configure-screens-replication.html?lang=en)。

#### 建立螢幕反向複製代理 {#creating-screens-reverse-replication-agents}

1. 為pub1建立反向複製代理。
1. 為pub2建立反向複製代理。 您可以複製pub1的反向複製代理，並通過更改傳輸配置中的埠來更新用於pub2的傳輸。

## 設定發佈拓撲 {#setting-up-publish-topology}

### 步驟1:配置基於Apache Sling Oak的發現 {#step-configure-apache-sling-oak-based-discovery}

為拓撲中的所有發佈實例設定基於Apache Sling Oak的發現

對於每個發佈實例：

1. 瀏覽到 `https://<host>:<port>/system/console/configMgr`
1. 選擇 **基於Apache Sling Oak的發現服務** 配置。
1. 更新拓撲連接器URL:添加以下所有參與發佈實例的URL:
   * `https://publish:4503/libs/sling/topology/connector`
   * `https://publish:4504/libs/sling/topology/connector`
1. **拓撲連接器白名單**:適應覆蓋所有發佈實例的IP或子網。 確保將所有發佈實例的IP/主機名列為白名，但不帶埠號。

1. 啟用 **自動停止本地循環**

每個發佈實例的配置應相同，自動停止本地循環可防止無限循環。

#### 步驟2:驗證發佈拓撲 {#step-verify-publish-topology}

對於任何發佈實例，導航至 `https://:/system/console/topology`。 您應看到拓撲中表示的每個發佈實例 **傳出拓撲連接器**。

#### 第3步：設定ActiveMQ Artemis群集 {#step-setup-activemq-artemis-cluster}

此步驟允許您為ActiveMQ Artemis群集建立加密密碼。
拓撲中所有發佈實例的群集用戶和口令必須相同。 需要加密ActiveMQ Artemis配置的口令。 由於每個實例都有其自己的加密密鑰，因此有必要使用加密支援建立加密的密碼字串。 然後，在ActiveMQ的OSGi配置中將使用加密的密碼。

在每個發佈實例上：

1. 在OSGi控制台中，導航至 **主** —> **加密支援** (`https://&lt;host&gt;:&lt;port&gt;/system/console/crypto`)。
1. 鍵入所需的純文字檔案密碼（對於所有實例都相同） **純文字檔案**
1. 按一下 **Protect**。
1. 複製值 **受保護文本** 記事本或文本編輯器。 此值將用於ActiveMQ的OSGi配置。

由於預設情況下每個發佈實例都具有唯一的加密密鑰，因此您需要在每個發佈實例上執行此步驟，並保存下次配置的唯一密鑰。

>[!NOTE]
>
>密碼應以大括弧開頭和結尾。 例如：
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### 第4步：激活ActiveMQ Artemis群集 {#step-activate-activemq-artemis-cluster}

在每個發佈實例上：

1. 導航到OSGi配置管理器 `https://&lt;host&gt;:&lt;port&gt;/system/console/configMgr`
1. 選擇 **Apache ActiveMQ Artemis JMS提供程式** 配置
1. 更新以下內容：

   * ***群集密碼***:對每個實例使用上一步的加密值
   * ***主題***: `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### 驗證ActiveMQ Artemis群集 {#verify-activemq-artemis-cluster}

對每個「發佈」實例執行以下步驟：

1. 導航至OSGi控制台 — >主> ActiveMQ Artemis `https://localhost:4505/system/console/mq`。
1. 驗證並檢查以查看「群集資訊」>「拓撲」>「節點=2, members=2」下其他實例的埠。
1. 發送Test消息（Broker資訊下螢幕頂部）
1. 在欄位中輸入以下更改：

   1. **目標**:/com.adobe.cq.screens/devTestTopic
   1. **文本**:《你好世界》
   1. 查看每個實例的error.log以查看消息是否在群集中發送和接收的

>[!NOTE]
>
>導航到OSGi控制台，可能需要在保存上一步中的配置後幾秒鐘。 您還可以檢查error.log以瞭解更多詳細資訊。

例如，成功配置ActiveMQ Artemis Server時，將顯示以下影像。

如果您未從 */system/console/mq*，然後導航 */system/console/mq* 按一下 **重新啟動** 以重新啟動代理。

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### 刪除引用程式標頭要求 {#remove-referrer-header-requirement}

按照每個「發佈」實例上的步驟操作：

1. 導航到 **OSGi控制台** > **配置管理器**
1. 選擇 **Apache Sling引用篩選器**
1. 更新配置和 **選中允許空**

### 配置作者和發佈實例 {#configuring-author-and-publish-instance}

設定發佈拓撲後，需要配置作者和發佈實例，以查看實施的實際結果：

>[!NOTE]
>
>**必備條件**
>
>要開始使用此示例，請建立一個新的AEM Screens項目，然後在項目中建立位置、顯示和通道。 將內容添加到頻道，並將頻道分配到顯示器。

#### 步驟1:啟動AEM Screens播放器（設備） {#step-starting-an-aem-screens-player-device}

1. 啟動單獨的瀏覽器窗口。
1. 使用 *web瀏覽器*&#x200B;就是，`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` 或者啟動AEM Screens應用。 開啟設備時，您會注意到設備的狀態為未註冊。

>[!NOTE]
>
>你可以使用你下載的AEM Screens應用或使用Web瀏覽器開啟AEM Screens播放器。

#### 步驟2:在作者上註冊設備 {#step-registering-a-device-on-author}

1. 轉到 `https://localhost:4502/screens.html/content/screens/we-retail` 或選擇項目並導航到「設備」>「設備管理器」。
1. 選擇 **寄存器設備**。
1. 按一下 **設備註冊** 來查看設備。
1. 選擇要註冊的設備，然後按一下 **寄存器設備**。
1. 驗證註冊代碼並按一下 **驗證**。
1. 輸入設備標題，然後按一下 **註冊**。

#### 第3步：將設備分配給顯示 {#step-assigning-the-device-to-display}

1. 按一下 **分配顯示** 的上界。
1. 從 **位置** 的子菜單。
1. 按一下 **分配**。
1. 按一下 **完成** 完成該過程，現在已分配設備。

檢查播放器，您將看到在頻道中添加的內容。

#### 第4步：發佈設備配置以發佈實例 {#step-publishing-device-configuration-to-publish-instances}

**驗證設備**

按照以下步驟複製設備用戶：

1. 導航到用戶管理頁(例如： `https://localhost:4502/useradmin`
1. 搜索 **螢幕設備主** 組
1. 按一下右鍵組，然後按一下 **激活**

>[!CAUTION]
>
>不要激活作者發佈螢幕服務，因為它是系統用戶，由作者作業使用。

您也可以從設備管理控制台激活設備。 請遵循下列步驟：

1. 導航到您的螢幕項目 — > **設備**。
1. 按一下 **設備管理器** 按鈕。
1. 選擇設備並按一下 **激活** 按下圖所示。

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>或者，激活設備後，您還可以通過按一下編輯或更新伺服器URL **編輯伺服器URL** 從操作欄中，如下圖所示，您所做的更改將傳播到AEM Screens播放器。

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### 發佈檢查清單 {#publishing-check-list}

以下幾點匯總了「發佈檢查」清單：

* *螢幕設備用戶*  — 此儲存為用戶AEM，並從 **工具** > **安全** > **用戶**。 用戶將用長序列化字串作為&quot;screens&quot;的前置詞。

* *項目* -AEM Screens項目。
* *位置*  — 設備連接的位置。
* *通道*  — 在位置顯示的一個或多個通道
* *計畫*  — 如果使用計畫，請確保發佈
* *位置、計畫和通道資料夾*  — 如果相應資源位於資料夾內。

按照以下步驟驗證作者/發佈行為：

1. 在作者實例上更新某些渠道內容
1. 執行 **管理發布** 發佈所有發佈實例的新更改
1. 按 **激活** 從 **設備管理器**
1. **編輯URL** 從作者實例URL到其中一個發佈實例URL
1. 驗證AEM Screens播放器上顯示的更新頻道內容
1. 使用其他發佈實例重複這些步驟


#### 第5步：在「管理」面板中指向要發佈實例的設備 {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. 從螢幕播放器中查看管理員UI，在左上角按長時間以開啟「管理員」菜單，在啟用觸摸的AEM Screens播放器上，或使用滑鼠開啟。
1. 按一下 **配置** 的上界。
1. 將作者實例更改為在中發佈實例 **伺服器**。

查看您的AEM Screens播放器中的更改。

或者，您也可以通過設備管理控制台使用以下步驟更新/編輯伺服器URL:

1. 導航到您的AEM Screens項目並選擇 **設備** 的子菜單。
1. 按一下 **設備管理器** 按鈕。
1. 選擇設備並按一下 **編輯伺服器URL** 從操作欄中，如下圖所示，您所做的更改將傳播到AEM Screens播放器。

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

的 **管理發布** 功能允許您將內容更新從作者發佈到設備。 您可以發佈/取消發佈整個AEM Screens項目的內容，或僅發佈渠道、位置、設備、應用程式或計畫之一的內容。 要瞭解有關此功能的詳細資訊，請參閱 [按需內容更新](on-demand-content.md)。

## 故障排除提示 {#troubleshoot-tips}

按照下面的部分，獲取有關作者/發佈設定的常見問題的答案。

### 如何在初始註冊和分配後將重定向從https添加到http? {#add-redirect}

**解決方案**
設定啟用 `Proxy/Load Balancer Connection in the Jetty configuration` 至 `true`。

### 如何使用外部資產更新離線內容和播放器下載問題 `/content/dam/projects/<project>`? {#update-offline-content}

**解決方案**
為批量離線更新螢幕服務用戶和螢幕設備主組授予讀取權限 `/content/dam` 或要使用的特定資產（如果希望限制性更強）。

### 如何解決螢幕複製代理錯誤？ {#replication-agent}

**解決方案**
確保在代理配置中未選中「用於反向複製」選項。 螢幕複製代理不能用作反向複製代理，此功能的作用範圍是將設備命令從作者轉發到發佈。
---
title: 複製資料觸發器以發佈伺服器
seo-title: 複製資料觸發器至發佈伺服器
description: 將資料觸發器複製至發佈伺服器。
seo-description: 將資料觸發器複製至發佈伺服器。
translation-type: tm+mt
source-git-commit: c9d618c4d38e8b1f74125c89cc9d25a1dcde54bb

---


# 將資料觸發器複製至發佈伺服器 {#replicating-data-triggers}

使用ContextHub和AEM Targeting Engine根據作者／發佈設定中的資料觸發器自訂內容時，所有與ContextHub和個人化相關的設定在發佈時不會自動與頻道複製。

請依照本頁瞭解個別發佈這些設定所需的手冊步驟。

這基本上可歸結為手動發佈：

1. ContextHub商店和UI模組組態
1. 個人化受眾
1. 個人化活動

## 將資料觸發器複製至發佈伺服器的步驟 {#replicating-data-triggers-publish}

請依照下列步驟，將資料觸發器複製至發佈伺服器。

### 步驟1:複製ContextHub配置 {#replicating-contexthub-configurations}

1. 導覽至「 **工具** >部署 **>散發** >發佈代理」 **>****** 「發佈代理」，然後按一下以設定您的發佈代理設定。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!Note]
   >或者，您也可以使 `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` 用導覽至畫面，以設定和測試連線。

1. 按一 **下動作列中的「測試連線** 」，驗證作者與發佈例項的通訊，如下圖所示。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!Note]
   >如果測試失敗，您需要在作者和發佈實例之間修正複製代理配置。 如需詳細資 [訊，請參閱Test Connection](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) 疑難排解。

1. 從「 **Distribution Agent** 」螢幕樹中選擇「添加 **」，然後選擇項目的配置路徑，例如**`/conf/screens/settings/cloudsettings/configuration`。

1. 按一 **下提交**。

### 複製觀眾 {#replicating-audiences}

1. 導覽至您的AEM例項>個人 **化** > **觀眾** ，或 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` 直接導覽。

1. 深入探討您的專案資料夾，例如 `/conf/screens/`。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. 從使用者介面選取所有對象和區段。

1. 按一 **下動作列中的** 「管理出版物」。

1. 按一 **下「下** 一步」 **和「發佈**」。

### 複製活動 {#replicating-activities}

1. 導覽至您的AEM例項>個人 **化** >活 **動** ，或 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` 直接導覽。

1. 深入探討您的專案資料夾，即 `/content/campaigns/screens/…`。

1. 從用戶介面中選擇所有活動。

1. 按一 **下動作列中的** 「管理出版物」。

1. 按一 **下「下** 一步」 **和「發佈**」。

>[!IMPORTANT]
>
>複製ContextHub組態和觀眾是在專案設定期間完成，同時複製活動，而且每次在頻道內變更目標時都需要複製。

#### 結果 {#result}

如果複製成功，您應在發佈實例（或類似於您的項目）上查看以下結構：

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 測試連線疑難排解 {#troubleshoot-test}

如果在複製ContextHub配置時測試連線失敗，請依照下列章節疑難排解問題：

1. 導覽至「工具>部 **署** > **散發** >發 **布代理」**。

1. 從動 **作列按一下** 「編輯」，並確定「匯入工具端點」欄位中的端點URL **** ，也會指向Distribution agent中的發佈伺服器URL。
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. 如果您未使用預設的管理員認證，則需要使用不同的使用者名稱和密碼來設定散發代理。

   請遵循下列步驟：

   1. 導覽至「工具> **作業** > **Web Console** 」 `http://localhost:4502/system/console/configMgr`以開啟 **Adobe Experience Manager Web Console畫面**。
   1. 搜尋 **Apache Sling Distribution Transport憑證——使用者憑證式DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 建立設定，方法 **是填入Name**、 **User name** 和 **password**，例如 ** slingTransportSecretProvider。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Click **Save**
   1. 使用 `Cmd +F` 來搜尋 **Apache Sling Distribution Agent - Forward Agents Factory** ，以開啟設定並搜尋 **Transport Secret Provider**。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. 使用更 `(name=default)` 新 `(name=slingTransportSecretProvider)`。
   1. 按一 **下「儲存** 」，然後從AEM例項的「 **Distribution Agent** 」畫面再次執行測試連線。

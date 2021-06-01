---
title: 將資料觸發器複製到發佈伺服器
seo-title: 將資料觸發器複製到發佈伺服器
description: 請參照本頁面，了解如何將資料觸發器複製到發佈伺服器。
seo-description: 將資料觸發器複製到發佈伺服器。
feature: 管理畫面、資料觸發
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 2%

---


# 將資料觸發器複製到發佈伺服器{#replicating-data-triggers}

使用ContextHub和AEM鎖定目標引擎根據製作/發佈設定中的資料觸發器來自訂內容時，所有與ContextHub和個人化相關的設定在發佈時不會自動與管道複製。

請依照本頁了解分別發佈這些設定所需的手冊步驟。

這基本上可歸因於手動發佈：

1. ContextHub存放區和UI模組設定
1. 個人化對象
1. 個人化活動

## 將資料觸發器複製到發佈伺服器{#replicating-data-triggers-publish}的步驟

請依照下列步驟，將資料觸發器複製到發佈伺服器。

### 步驟1:複製ContextHub配置{#replicating-contexthub-configurations}

1. 導覽至&#x200B;**工具** > **部署** > **發佈** > **發佈代理** ，然後按一下發佈代理以配置您的設定。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >或者，您也可以使用`http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish`直接導覽至畫面，以設定和測試連線。

1. 按一下動作列中的「**測試連線**」 ，驗證作者與發佈例項的通訊，如下圖所示。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >如果測試失敗，您需要修正製作與發佈執行個體之間的復寫代理設定。 如需詳細資訊，請參閱[疑難排解測試連線](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) 。

1. 從&#x200B;**分發代理**&#x200B;螢幕樹中選擇&#x200B;**添加**&#x200B;並選擇項目的配置路徑，例如`/conf/screens/settings/cloudsettings/configuration`。

1. 按一下&#x200B;**Submit**。

### 復寫對象{#replicating-audiences}

1. 導覽至您的AEM例項> **個人化** > **對象**&#x200B;或使用`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html`直接導覽。

1. 深入鑽研至您的專案資料夾，例如`/conf/screens/`。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. 從使用者介面中選取所有對象和區段。

1. 按一下動作列中的&#x200B;**管理出版物** 。

1. 按一下「**Next**」和「**Publish**」。

### 複製活動{#replicating-activities}

1. 導覽至您的AEM例項> **個人化** > **活動**&#x200B;或使用`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html`直接導覽。

1. 深入鑽研至您的專案資料夾，即`/content/campaigns/screens/…`。

1. 從使用者介面中選取所有活動。

1. 按一下動作列中的&#x200B;**管理出版物** 。

1. 按一下「**Next**」和「**Publish**」。

>[!IMPORTANT]
>
>在專案設定期間複製ContextHub設定和對象時，會同時複製活動，且每次在管道內變更目標時都需要。

#### 結果 {#result}

如果復寫成功，您應在發佈執行個體（或專案的類似結構）上檢視下列結構：

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 測試連接{#troubleshoot-test}故障排除

如果複製ContextHub設定時測試連線失敗，請依照以下章節疑難排解問題：

1. 導覽至工具> **部署** > **發佈** > **發佈代理**。

1. 從動作列按一下&#x200B;**編輯**，並確保&#x200B;**匯入工具端點**欄位中的端點URL也指向發佈代理中的發佈伺服器URL。
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. 如果您未使用預設的管理員憑證，則需要使用不同的使用者名稱和密碼來設定發佈代理程式。

   請遵循下列步驟：

   1. 導覽至工具> **操作** > **Web控制台** `http://localhost:4502/system/console/configMgr`以開啟&#x200B;**Adobe Experience Manager Web控制台螢幕**。
   1. 搜尋&#x200B;**Apache Sling Distribution Transport憑證 — 以DistributionTransportSecretProvider**&#x200B;為基礎的使用者憑證

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 建立配置，方法是填入&#x200B;**Name**、**User name**&#x200B;和&#x200B;**password**，例如&#x200B;*slingTransportSecretProvider*。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. 按一下&#x200B;**儲存**
   1. 使用`Cmd +F`搜索&#x200B;**Apache Sling Distribution Agent - Forward Agent Factory**&#x200B;以開啟配置並搜索&#x200B;**傳輸密碼提供程式**。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. 使用`(name=slingTransportSecretProvider)`更新`(name=default)`。
   1. 按一下&#x200B;**Save**，然後從AEM實例的&#x200B;**Distribution Agent**&#x200B;螢幕再次運行測試連接。

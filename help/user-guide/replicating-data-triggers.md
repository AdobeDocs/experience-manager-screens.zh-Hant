---
title: 將資料觸發器復寫至發佈伺服器
description: 瞭解如何將資料觸發器復寫至AEM Screens的發佈伺服器。
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 1%

---

# 將資料觸發器復寫至發佈伺服器 {#replicating-data-triggers}

使用ContextHub和AEM鎖定目標引擎根據作者/發佈設定中的資料觸發器自訂內容時，所有ContextHub和Personalization相關設定在發佈時不會自動與管道復寫。

本頁可協助您瞭解分別發佈這些設定所需的手動步驟。

此過程基本上取決於手動發佈以下內容：

1. ContextHub存放區和UI模組設定
1. Personalization對象
1. Personalization活動

## 將資料觸發程式複製到發佈伺服器的步驟 {#replicating-data-triggers-publish}

請依照下列步驟，將資料觸發程式復寫至發佈伺服器。

### 步驟1：復寫ContextHub設定 {#replicating-contexthub-configurations}

1. 瀏覽至&#x200B;**工具** > **部署** > **發佈** > **發佈代理程式**，然後按一下發佈代理程式，以便您可以設定設定。

   ![影像1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >或者，您可以使用`http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish`直接瀏覽至畫面來設定及測試連線。

1. 按一下動作列中的&#x200B;**測試連線**，您就可以驗證作者與發佈執行個體的通訊，如下所示：

   ![影像1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >如果測試失敗，請修正製作和發佈執行個體之間的復寫代理程式設定。 如需詳細資訊，請參閱[測試連線疑難排解](/help/user-guide/replicating-data-triggers.md#troubleshoot-test)。

1. 從&#x200B;**發佈代理程式**&#x200B;熒幕樹狀結構按一下&#x200B;**新增**，然後按一下專案的設定路徑，例如`/conf/screens/settings/cloudsettings/configuration`。

1. 按一下「**提交**」。

### 復寫對象 {#replicating-audiences}

1. 導覽至您的AEM執行個體> **Personalization** > **對象**，或使用`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html`直接導覽。

1. 向下展開至您的專案資料夾，例如`/conf/screens/`。

   ![影像1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. 從使用者介面按一下所有對象和區段。

1. 按一下動作列中的&#x200B;**管理出版物**。

1. 按一下&#x200B;**下一步**&#x200B;和&#x200B;**發佈**。

### 復寫活動 {#replicating-activities}

1. 導覽至您的AEM執行個體> **Personalization** > **活動**，或使用`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html`直接導覽。

1. 向下展開至您的專案資料夾，也就是`/content/campaigns/screens/…`。

1. 按一下使用者介面中的所有活動。

1. 按一下動作列中的&#x200B;**管理出版物**。

1. 按一下&#x200B;**下一步**&#x200B;和&#x200B;**發佈**。

>[!IMPORTANT]
>
>復寫ContextHub設定和對象是在專案設定期間在復寫活動期間完成的，並且每當頻道內的目標定位變更時都需要。

#### 結果 {#result}

如果複製成功，您應在發佈執行個體上檢視以下結構（或專案中類似結構）：

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 疑難排解測試連線 {#troubleshoot-test}

如果復寫ContextHub設定時測試連線失敗，請遵循以下章節以疑難排解問題：

1. 導覽至&#x200B;**工具** > **部署** > **發佈** > **發佈代理程式**。

1. 按一下動作列中的&#x200B;**編輯**，並確定&#x200B;**Importer端點**欄位中的端點URL也指向發佈代理程式中的發佈伺服器URL。
   ![影像1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. 如果您未使用預設的管理員認證，則必須使用不同的使用者名稱和密碼來設定發佈代理程式。

   請遵循下列步驟：

   1. 導覽至「工具> **作業** > **網頁主控台** `http://localhost:4502/system/console/configMgr`，以便您可以開啟&#x200B;**Adobe Experience Manager網頁主控台畫面**。
   1. 搜尋&#x200B;**`Apache Sling Distribution Transport Credentials - User Credentials based DistributionTransportSecretProvider`**

      ![影像1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 建立設定，方法是填入&#x200B;**名稱**、**使用者名稱**&#x200B;和&#x200B;**密碼**，例如&#x200B;*slingTransportSecretProvider*。

      ![影像1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. 按一下&#x200B;**儲存**
   1. 使用`Cmd +F`搜尋&#x200B;**Apache Sling Distribution Agent - Forward Agents Factory**&#x200B;以開啟設定並搜尋&#x200B;**傳輸機密提供者**。

      ![影像1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. 使用`(name=slingTransportSecretProvider)`更新`(name=default)`。
   1. 按一下「儲存」****，然後再次從AEM執行個體的&#x200B;**散發代理程式**&#x200B;畫面執行測試連線。

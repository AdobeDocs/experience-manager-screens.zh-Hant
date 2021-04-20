---
title: 複製資料觸發器以發佈伺服器
seo-title: 複製資料觸發器至發佈伺服器
description: 請依照本頁瞭解如何複製資料觸發器至發佈伺服器。
seo-description: 將資料觸發器複製至發佈伺服器。
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 2%

---


# 將資料觸發器複製到發佈伺服器{#replicating-data-triggers}

當使用ContextHub和AEMTargeting Engine根據作者／發佈設定中的資料觸發器自訂內容時，所有與ContextHub和個人化相關的設定在發佈時不會自動與頻道複製。

請依照本頁瞭解個別發佈這些設定所需的手冊步驟。

這基本上可歸結為手動發佈：

1. ContextHub商店和UI模組組態
1. 個人化受眾
1. 個人化活動

## 將資料觸發器複製到發佈伺服器{#replicating-data-triggers-publish}的步驟

請依照下列步驟，將資料觸發器複製至發佈伺服器。

### 步驟1:複製ContextHub配置{#replicating-contexthub-configurations}

1. 導覽至「**工具** > **部署** > **分發** > **發佈代理**」，然後按一下發佈代理以設定您的設定。

   ![影像1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >或者，您也可以使用`http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish`直接導覽至畫面，以設定和測試連線。

1. 按一下動作列的「測試連線」(**Test Connection)**，驗證作者與發佈例項的通訊，如下圖所示。

   ![影像1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >如果測試失敗，您需要在作者和發佈實例之間修正複製代理配置。 有關詳細資訊，請參閱[測試連接故障排除](/help/user-guide/replicating-data-triggers.md#troubleshoot-test)。

1. 從&#x200B;**Distribution Agent**&#x200B;螢幕樹中選擇&#x200B;**Add** ，並選擇項目的配置路徑，例如`/conf/screens/settings/cloudsettings/configuration`。

1. 按一下&#x200B;**提交**。

### 複製觀眾{#replicating-audiences}

1. 導覽至您AEM的例項> **個人化** > **觀眾**&#x200B;或使用`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html`直接導覽。

1. 深入探討您的專案資料夾，例如`/conf/screens/`。

   ![影像1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. 從使用者介面選取所有對象和區段。

1. 從操作欄中按一下「管理出版物」(**Manage Publication**)。

1. 按一下「**Next**」和「**Publish**」。

### 複製活動{#replicating-activities}

1. 導覽至您AEM的例項> **個人化** > **活動**&#x200B;或使用`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html`直接導覽。

1. 深入查看您的項目資料夾，即`/content/campaigns/screens/…`。

1. 從用戶介面中選擇所有活動。

1. 從操作欄中按一下「管理出版物」(**Manage Publication**)。

1. 按一下「**Next**」和「**Publish**」。

>[!IMPORTANT]
>
>複製ContextHub組態和觀眾是在專案設定期間完成，同時複製活動，而且每次在頻道內變更目標時都需要複製。

#### 結果 {#result}

如果複製成功，您應在發佈實例（或類似於您的項目）上查看以下結構：

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 測試連接疑難排解{#troubleshoot-test}

如果在複製ContextHub配置時測試連線失敗，請依照下列章節疑難排解問題：

1. 導覽至「工具> **部署** > **散發** > **發佈代理**」。

1. 從動作列按一下「**編輯**」，並確保&#x200B;**匯入工具端點**欄位中的端點URL也指向Distribution Agent中的發佈伺服器URL。
   ![影像1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. 如果您未使用預設的管理員認證，則需要使用不同的使用者名稱和密碼來設定散發代理。

   請遵循下列步驟：

   1. 導覽至「工具> **操作** > **Web控制台** `http://localhost:4502/system/console/configMgr`」以開啟&#x200B;**Adobe Experience ManagerWeb控制台螢幕**。
   1. 搜尋&#x200B;**Apache Sling Distribution Transport Credentials —— 使用者認證，以DistributionTransportSecretProvider**

      ![影像1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 建立設定，方法是填入&#x200B;**Name**、**User name**&#x200B;和&#x200B;**password**，例如&#x200B;*slingTransportSecretProvider*。

      ![影像1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. 按一下&#x200B;**保存**
   1. 使用`Cmd +F`搜尋&#x200B;**Apache Sling Distribution Agent - Forward Agents Factory**&#x200B;以開啟設定並搜尋&#x200B;**Transport Secret Provider**。

      ![影像1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. 使用`(name=slingTransportSecretProvider)`更新`(name=default)`。
   1. 按一下&#x200B;**Save**，然後從實例的&#x200B;**Distribution Agent**&#x200B;螢幕再次運行測AEM試連接。

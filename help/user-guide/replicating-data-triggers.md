---
title: 複製資料觸發器以發佈伺服器
seo-title: 複製資料觸發器至發佈伺服器
description: 將資料觸發器複製至發佈伺服器。
seo-description: 將資料觸發器複製至發佈伺服器。
translation-type: tm+mt
source-git-commit: a8ded0c15e0e3cbaf0999da796789991b20d24cb

---


# 將資料觸發器複製至發佈伺服器 {#replicating-data-triggers}

使用ContextHub和AEM Targeting Engine根據作者／發佈設定中的資料觸發器自訂內容時，所有與ContextHub和個人化相關的設定在發佈時不會自動與頻道複製。

請依照本頁瞭解個別發佈這些設定所需的手冊步驟。

這基本上可歸結為手動發佈：

1. ContextHub商店和UI模組組態
1. 個人化受眾
1. 個人化活動

## 將資料觸發器複製至發佈伺服器的步驟 {#replicating-data-triggers-publish}

請遵循下列步驟，將資料觸發器複製至發佈伺服器：

### 複製ContextHub配置 {#replicating-contexthub-configurations}

1. 導覽至「 **工具** >部署 **>散發** >發佈代理 ******** http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish」
1. 按一下「測試連線」按鈕，驗證作者是否可正確與發佈例項通訊
1. 如果測試失敗，您需要在作者和發佈之間修正複製代理配置
1. 確定端點URL也指向Distribution Agent中的發佈伺服器URL
1. 編輯>匯入工具端點
1. 按一下「散發」標籤
1. 「選擇添加樹」單選按鈕
1. 在路徑瀏覽器中，選取專案的設定路徑(例如/conf/screens/settings/cloudsettings/configuration)
1. 按一下「提交」

### 複製觀眾 {#replicating-audiences}

1. 導覽至「工具>個人化>觀眾http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html」
1. 深入探討您的專案資料夾(即/conf/screens/)
1. 在UI中選取所有對象／區段
1. 按一下「管理出版物」
1. 按「下一步」
1. 按一下「發佈」

### 複製活動 {#replicating-activities}

1. 導覽至「工具>個人化>活動http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html」
1. 深入探討您的專案資料夾(即/content/campaigns/screens/...)
1. 在UI中選取所有活動
1. 按一下「管理出版物」
1. 按「下一步」
1. 按一下「發佈」

> [!Note]
>複製ContextHub組態和觀眾是在專案設定期間完成，同時複製活動，而且每次在頻道內變更目標時都需要複製。

#### 結果 {#result}

如果複製成功，您應在發佈實例（或類似於您的項目）上查看以下結構：

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`
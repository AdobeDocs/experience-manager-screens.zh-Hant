---
title: 配置螢幕複製代理
description: 按照此頁獲取有關如何配置螢幕複製代理的資訊。
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: 93bbffa2d752bfbd92702487802d40e7e8e287b8
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 3%

---

# 配置螢幕複製代理 {#configuring-screens-replication-agent}

此頁介紹如何配置螢幕複製代理。

## 目標 {#objective}

螢幕複製代理負責提供命令資料，如 *用戶*。 *密碼*。 *重新引導計畫*。 *maxNumberOfLogFilesToKeep*，以及從發佈到作者的更多這樣的價值。 必須配置此項，以便作者可以顯示設備ping。

>[!NOTE]
>要瞭解有關螢幕複製代理的詳細資訊，請參見 [螢幕複製代理和命令](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=en#screens-replication-agents-and-commands)。

必須完成以下兩節，才能完成螢幕複製代理的配置：

1. [啟用用戶和更新密碼](#enable-users)
1. [更新螢幕複製代理的設定](#replicate-agent)

## 啟用用戶和更新密碼 {#enable-users}

按照以下步驟啟用用戶並更新螢幕接收方用戶的密碼：

>[!NOTE]
>出於安全原因，建議避免使用screens-receiver-user的管理員密碼。

1. 導航到AEM作者實例。

1. 按一下工具 — > **安全** —> **用戶**。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. 搜索 **螢幕接收用戶**。

1. 選擇 **螢幕接收用戶** 按一下 **啟用** 按鈕。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. 按一下 **確定** 確認。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication3.png)

   啟用用戶後，您將看到 **螢幕接收用戶** 如 **已啟用** 下 **狀態** 的子菜單。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. 選擇 **螢幕接收用戶** 按一下 **屬性** 按鈕。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. 按一下 **更改密碼** 在 **帳戶設定** 從 **詳細資訊** 頁籤，如下圖所示。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. 在 **更改密碼** 對話框，然後按一下 **保存**。

   >[!NOTE]
   >您應在中輸入現有管理員用戶密碼 **您的密碼** 的子菜單。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. 按一下 **保存並關閉**。

1. 選擇 **螢幕接收用戶** 按一下 **激活** 按鈕。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. 按一下 **確定** 確認。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. 選擇 **螢幕接收用戶** 按一下 **禁用** 按鈕。

   >[!IMPORTANT]
   > 禁用 **螢幕接收用戶** 僅從作者實例中禁用此用戶，而發佈實例中的所有用戶仍然處於活動狀態。 不按一下 **停用** 從操作欄中，因為停用將同時從發佈實例中刪除用戶。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. 按一下 **確定** 確認。

## 更新螢幕複製代理的設定 {#replicate-agent}

按照以下部分更新螢幕複製代理中的設定：

>[!IMPORTANT]
>必須在所有現有螢幕複製代理上完成以下步驟。

1. 導航到實AEM例。

1. 按一下工具 — > **部署** —> **複製**。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. 按一下 **作者代理**。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 在作者上搜索所有螢幕複製代理，然後按一下連結，如下圖所示。

   >[!NOTE]
   >搜索所有螢幕複製代理。 螢幕複製代理名稱將包含字母 **S** 的雙曲餘切值。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. 按一下 **編輯**。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. 檢查 **已啟用** 從 **設定** 頁籤。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. 導航到 **運輸** 的 **代理設定** 對話框並更新 **用戶** 至 **螢幕接收用戶** 並輸入您在第(8)步中設定的密碼 [啟用用戶和更新密碼](#enable-users)。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. 按一下 **確定**。

1. 完成上述步驟後，可按一下 **Test連接** 驗證連接。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   如果連接驗證成功，則已完成配置螢幕複製代理。

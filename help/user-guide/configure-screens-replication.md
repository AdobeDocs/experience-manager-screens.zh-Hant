---
title: 設定Screens復寫代理
description: 瞭解如何設定Screens復寫代理。
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 4%

---

# 設定Screens復寫代理 {#configuring-screens-replication-agent}

以下頁面說明如何設定Screens復寫代理程式。

## 目標 {#objective}

Screens復寫代理程式負責將命令資料（例如&#x200B;*user*、*password*、*rebootSchedule*、*maxNumberOfLogFilesToKeep*），以及其他許多此類值從發佈到作者。 請務必設定此代理程式，讓作者可以顯示裝置Ping。

>[!NOTE]
>若要深入瞭解Screens復寫代理程式，請參閱[Screens復寫代理程式與命令](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands)。

如果您要完成Screens復寫代理程式的設定，請完成這兩節：

1. [啟用使用者及更新密碼](#enable-users)
1. [更新Screens復寫代理程式的設定](#replicate-agent)

## 啟用使用者及更新密碼 {#enable-users}

請依照下列步驟，啟用使用者並更新`screens-receiver-user`的密碼：

>[!NOTE]
>基於安全考量，建議您避免使用`screens-receiver-user`的管理密碼。

1. 導覽至您的AEM Author例項。

1. 按一下「工具」 > 「**安全性**」 > 「**使用者**」。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. 搜尋&#x200B;**`screens-receiver-user`**。

1. 按一下&#x200B;**`screens-receiver-user`**，然後按一下動作列中的&#x200B;**啟用**。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. 按一下&#x200B;**確定**&#x200B;確認。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication3.png)

   啟用使用者後，**狀態**&#x200B;欄位下的&#x200B;**`screens-receiver-user`**&#x200B;顯示為&#x200B;**已啟用**。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. 按一下&#x200B;**`screens-receiver-user`**，然後按一下動作列中的&#x200B;**屬性**。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. 從&#x200B;**詳細資料**&#x200B;標籤按一下&#x200B;**帳戶設定**&#x200B;底下的&#x200B;**變更密碼**，如下圖所示。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. 在&#x200B;**變更密碼**&#x200B;對話方塊中輸入新密碼，然後按一下&#x200B;**儲存**。

   >[!NOTE]
   >在&#x200B;**您的密碼**&#x200B;欄位中輸入現有的管理員使用者密碼。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. 按一下&#x200B;**「儲存並關閉」**。

1. 按一下&#x200B;**`screens-receiver-user`**，然後按一下動作列中的&#x200B;**啟動**。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. 按一下&#x200B;**確定**&#x200B;確認。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. 按一下&#x200B;**`screens-receiver-user`**，然後按一下動作列中的&#x200B;**停用**。

   >[!IMPORTANT]
   > 停用&#x200B;**`screens-receiver-user`**&#x200B;只會從編寫執行個體中停用此使用者，而且發佈執行個體中的所有使用者都會保持作用中。 請勿在動作列中按一下&#x200B;**[停用**]，因為停用也會從發佈執行個體中移除使用者。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. 按一下&#x200B;**確定**&#x200B;確認。

## 更新Screens復寫代理程式的設定 {#replicate-agent}

請依照以下章節，更新AEM Screens復寫代理程式中的設定：

>[!IMPORTANT]
>在所有現有AEM Screens復寫代理程式上完成下列步驟。

1. 導覽至您的AEM執行個體。
1. 按一下[工具] > [部署] > [復寫] > [部署] **> [復寫]****。**

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. 按一下作者上的&#x200B;**代理程式**。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 在作者上搜尋所有AEM Screens復寫代理程式，然後按一下連結，如下圖所示。

   >[!NOTE]
   >搜尋所有AEM Screens復寫代理。 Screens復寫代理程式名稱在標題中包含字母&#x200B;**S**。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. 按一下&#x200B;**編輯**。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. 從&#x200B;**設定**&#x200B;索引標籤檢查&#x200B;**已啟用**。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. 從&#x200B;**代理程式設定**&#x200B;對話方塊瀏覽至&#x200B;**傳輸**&#x200B;標籤，並將&#x200B;**使用者**&#x200B;更新為&#x200B;**`screens-receiver-user`**，然後輸入您在[啟用使用者並更新密碼](#enable-users)的步驟(8)中先前設定的相同密碼。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. 按一下&#x200B;**「確定」**。

1. 完成上述步驟後，請按一下[測試連線] **以驗證連線。**

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   如果連線驗證成功，表示您已完成Screens復寫代理程式的設定。

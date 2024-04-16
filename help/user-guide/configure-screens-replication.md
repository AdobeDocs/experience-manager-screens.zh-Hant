---
title: 設定Screens復寫代理
description: 瞭解如何設定Screens復寫代理。
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 4%

---

# 設定Screens復寫代理 {#configuring-screens-replication-agent}

以下頁面說明如何設定Screens復寫代理程式。

## 目標 {#objective}

Screens復寫代理程式負責帶入命令資料，例如 *使用者*， *密碼*， *rebootSchedule*， *maxNumberOfLogFilesToKeep*，以及發佈到作者的更多這類值。 您必須進行此設定，讓作者可以顯示裝置Ping。

>[!NOTE]
>若要深入瞭解Screens復寫代理，請參閱 [Screens復寫代理和命令](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands).

如果您要完成Screens復寫代理程式的組態，請完成這兩個段落：

1. [啟用使用者及更新密碼](#enable-users)
1. [更新Screens復寫代理程式的設定](#replicate-agent)

## 啟用使用者及更新密碼 {#enable-users}

請依照下列步驟，啟用使用者並更新密碼 `screens-receiver-user`：

>[!NOTE]
>基於安全考量，建議避免使用管理密碼用於 `screens-receiver-user`.

1. 導覽至您的AEM Author例項。

1. 按一下「工具」 > **安全性** > **使用者**.

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. 搜尋 **`screens-receiver-user`**.

1. 按一下 **`screens-receiver-user`** 並按一下 **啟用** 從動作列移除。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. 按一下 **確定** 以確認。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication3.png)

   啟用使用者後，您會看到 **`screens-receiver-user`** 作為 **已啟用** 在 **狀態** 欄位。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. 按一下 **`screens-receiver-user`** 並按一下 **屬性** 從動作列移除。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. 按一下 **變更密碼** 在 **帳戶設定** 從 **詳細資料** 標籤，如下圖所示。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. 輸入新密碼，在 **變更密碼** 對話方塊並按一下 **儲存**.

   >[!NOTE]
   >在中輸入現有的管理員使用者密碼 **您的密碼** 欄位。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. 按一下&#x200B;**「儲存並關閉」**。

1. 按一下 **`screens-receiver-user`** 並按一下 **啟動** 從動作列移除。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. 按一下 **確定** 以確認。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. 按一下 **`screens-receiver-user`** 並按一下 **停用** 從動作列移除。

   >[!IMPORTANT]
   > 正在停用 **`screens-receiver-user`** 僅會從Authoring執行個體中停用此使用者，且Publishing執行個體中的所有使用者都會保持作用中。 不要按一下 **停用** ，因為停用也會將使用者從「發佈」執行個體中移除。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. 按一下 **確定** 以確認。

## 更新Screens復寫代理程式的設定 {#replicate-agent}

請依照以下章節，更新AEM Screens復寫代理程式中的設定：

>[!IMPORTANT]
>在所有現有AEM Screens復寫代理程式上完成下列步驟。

1. 導覽至您的AEM執行個體。
1. 按一下「工具」 > **部署** > **復寫**.

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. 按一下 **作者上的代理程式**.

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 在作者上搜尋所有AEM Screens復寫代理，然後按一下連結，如下圖所示。

   >[!NOTE]
   >搜尋所有AEM Screens復寫代理。 Screens復寫代理程式名稱包含字母 **S** 在標題中。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. 按一下 **編輯**.

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. 檢查 **已啟用** 從 **設定** 標籤。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. 瀏覽至 **傳輸** 標籤從 **代理程式設定** 對話方塊並更新 **使用者** 至 **`screens-receiver-user`** 並輸入您之前在步驟(8)中設定的相同密碼 [啟用使用者及更新密碼](#enable-users).

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. 按一下&#x200B;**「確定」**。

1. 完成上述步驟後，請按一下 **測試連線** 以驗證連線。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   如果連線驗證成功，表示您已完成設定Screens復寫代理程式。

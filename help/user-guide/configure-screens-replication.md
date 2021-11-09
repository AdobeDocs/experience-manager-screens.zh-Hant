---
title: 配置Screens複製代理
description: 請依照本頁面操作，以取得如何設定Screens復寫代理的資訊。
role: Developer
level: Intermediate
source-git-commit: 42e6adb7f8aa60854637a48fbb08525a0a971276
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 3%

---


# 配置螢幕複製代理 {#configuring-screens-replication-agent}

以下頁面說明如何配置Screens複製代理。

>[!NOTE]
>要了解有關Screens複製代理的詳細資訊，請參閱 [螢幕複製代理和命令](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=en#screens-replication-agents-and-commands).

您必須完成這兩個區段，才能完成Screens Replication Agent的設定：

1. [啟用用戶並更新密碼](#enable-users)
1. [更新Screens復寫代理的設定](#replicate-agent)

## 啟用用戶並更新密碼 {#enable-users}

請依照下列步驟，啟用使用者並更新screens-receiver-user的密碼：

>[!NOTE]
>基於安全考量，建議避免使用screens-receiver-user的管理密碼。

1. 導覽至您的AEM例項。

1. 按一下「工具 — >」 **安全性** —> **使用者**.

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. 搜尋 **screens-receiver-user**.

1. 選取 **screens-receiver-user** 按一下 **啟用** 從動作列。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. 按一下 **確定** 確認。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication3.png)

   啟用使用者後，您會看到 **screens-receiver-user** as **已啟用** 在 **狀態** 欄位。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. 選取 **screens-receiver-user** 按一下 **屬性** 從動作列。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. 按一下 **更改密碼** 在 **帳戶設定** 從 **詳細資料** 標籤，如下圖所示。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. 在 **更改密碼** 對話框，然後按一下 **儲存**.

   >[!NOTE]
   >您應輸入 **管理員** in **密碼** 欄位。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. 按一下 **儲存並關閉**.

1. 選取 **screens-receiver-user** 按一下 **啟動** 從動作列。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. 按一下 **確定** 確認。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. 選取 **screens-receiver-user** 按一下 **停用** 從動作列。

   >[!IMPORTANT]
   > 停用 **screens-receiver-user** 僅會停用製作例項中的此使用者，而發佈例項中的所有使用者仍保持作用中狀態。 不點按 **停用** 從動作列中，因為停用也會將使用者從發佈執行個體中移除。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. 按一下 **確定** 確認。

## 更新Screens復寫代理的設定 {#replicate-agent}

請依照下節，更新Screens復寫代理中的設定：

1. 導覽至您的AEM例項。

1. 按一下「工具 — >」 **部署** —> **復寫**.

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. 按一下 **作者代理**.

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 在作者上搜尋Screens復寫代理，然後按一下連結，如下圖所示。

   >[!NOTE]
   >使用字母搜尋Screens復寫代理 **S** 包含在作者名稱中。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. 按一下 **編輯**.

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. 檢查 **已啟用** 從 **設定** 標籤。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. 導覽至 **運輸** 標籤 **代理設定** 對話框中，輸入您在步驟(8)中設定的相同密碼 [啟用用戶並更新密碼](#enable-users). 按一下 **確定**.

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1f.png)

1. 完成上述步驟後，您可以按一下 **測試連線** 來驗證連接。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   如果連接驗證成功，則您已完成配置Screens複製代理。
---
title: 配置Screens複製代理
description: 請依照本頁面操作，以取得如何設定Screens復寫代理的資訊。
role: Developer
level: Intermediate
source-git-commit: 9f0beddf87d9f5473fdedc292d3c24e96b85cdd4
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 6%

---


# 配置螢幕複製代理 {#configuring-screens-replication-agent}

本節說明如何配置Screens復寫代理。

## 啟用用戶並更新密碼 {#enable-users}

請遵循下列步驟：

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

## 正在更新Screens複製代理 {#replicate-agent}

請依照下節，更新Screens復寫代理中的設定：

1. 導覽至您的AEM例項。

1. 按一下「工具 — >」 **部署** —> **復寫**.

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1a.png)

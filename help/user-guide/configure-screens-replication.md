---
title: 設定Screens復寫代理
description: 請依照此頁面取得如何設定Screens復寫代理的資訊。
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 3%

---

# 設定Screens復寫代理 {#configuring-screens-replication-agent}

以下頁面說明如何設定Screens復寫代理程式。

## 目標 {#objective}

Screens復寫代理程式負責帶入命令資料，例如 *使用者*， *密碼*， *rebootSchedule*， *maxNumberOfLogFilesToKeep*，以及發佈到作者的更多這類值。 您必須進行此設定，讓作者可以顯示裝置Ping。

>[!NOTE]
>若要深入瞭解Screens復寫代理，請參閱 [Screens復寫代理和命令](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=en#screens-replication-agents-and-commands).

您必須完成這兩個段落，才能完成Screens復寫代理程式的設定：

1. [啟用使用者及更新密碼](#enable-users)
1. [更新Screens復寫代理程式的設定](#replicate-agent)

## 啟用使用者及更新密碼 {#enable-users}

請依照下列步驟，啟用使用者並更新screens-receiver-user的密碼：

>[!NOTE]
>基於安全考量，建議您避免使用screens-receiver-user的管理密碼。

1. 導覽至您的AEM Author例項。

1. 按一下「工具」 > **安全性** > **使用者**.

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. 搜尋 **screens-receiver-user**.

1. 選取 **screens-receiver-user** 並按一下 **啟用** 從動作列移除。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. 按一下 **確定** 以確認。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication3.png)

   啟用使用者後，您將會看到 **screens-receiver-user** 作為 **已啟用** 在 **狀態** 欄位。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. 選取 **screens-receiver-user** 並按一下 **屬性** 從動作列移除。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. 按一下 **變更密碼** 在 **帳戶設定** 從 **詳細資料** 標籤，如下圖所示。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. 輸入新密碼，在 **變更密碼** 對話方塊並按一下 **儲存**.

   >[!NOTE]
   >您應輸入現有的管理員使用者密碼 **您的密碼** 欄位。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. 按一下 **儲存並關閉**.

1. 選取 **screens-receiver-user** 並按一下 **啟動** 從動作列移除。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. 按一下 **確定** 以確認。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. 選取 **screens-receiver-user** 並按一下 **停用** 從動作列移除。

   >[!IMPORTANT]
   > 正在停用 **screens-receiver-user** 僅會從編寫執行個體中停用此使用者，而發佈執行個體中的所有使用者仍會保持作用中。 不要按一下 **停用** ，因為停用也會將使用者從發佈執行個體中移除。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. 按一下 **確定** 以確認。

## 更新Screens復寫代理程式的設定 {#replicate-agent}

請依照以下章節更新Screens復寫代理程式中的設定：

>[!IMPORTANT]
>您必須在所有現有Screens復寫代理程式上完成下列步驟。

1. 導覽至您的AEM執行個體。

1. 按一下「工具」 > **部署** > **復寫**.

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. 按一下 **作者上的代理程式**.

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 搜尋作者上的所有Screens復寫代理，然後按一下連結，如下圖所示。

   >[!NOTE]
   >搜尋所有Screens復寫代理。 Screens復寫代理程式名稱將包含字母 **S** 在標題中。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. 按一下 **編輯**.

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. 檢查 **已啟用** 從 **設定** 標籤。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. 瀏覽至 **傳輸** 標籤從 **代理程式設定** 對話方塊並更新 **使用者** 至 **screens-receiver-user** 並輸入您之前在步驟(8)中設定的相同密碼 [啟用使用者及更新密碼](#enable-users).

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. 按一下 **確定**.

1. 完成上述步驟後，您可以按一下 **測試連線** 以驗證連線。

   ![影像](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   如果連線驗證成功，表示您已完成設定Screens復寫代理程式。

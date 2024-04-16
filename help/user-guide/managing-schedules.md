---
title: 建立和管理排程
description: 瞭解可將管道組織成可重複使用的群組的排程，這樣您就不必針對要顯示內容的每個顯示分別重複其指派。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# 建立和管理排程 {#creating-and-managing-schedules}

**時程表** 在AEM Screens中，您可以將管道組織成可重複使用的群組，如此您就不必針對您想要顯示內容的每個顯示分別重複其指派。

排程，與合併時 ***日時段分割***，可讓您設定在一天中的特定時間執行多個管道的全域排程，並重複使用一次為所有的顯示設定的。

>[!NOTE]
>
>此AEM Screens功能僅在您已安裝AEM 6.3 Sites Feature Pack 1時可用。 若要存取此Feature Pack，請聯絡Adobe支援並要求存取權。 取得必要許可權後，即可從「封裝共用」下載。

## 建立排程 {#creating-a-schedule}

您可以為Screens專案建立排程，以管理使用案例的所有活動。

請依照下列步驟，為您的頻道建立排程：

1. 按一下Adobe Experience Manager連結（左上方），然後按一下Screens。 或者，您可以直接前往： `http://localhost:4502/screens.html/content/screens`.
1. 導覽至畫面專案，然後按一下 **時程表**.
1. 按一下 **建立** 從動作列移除。
1. 按一下 **排程** 從 **建立** 精靈並按一下 **下一個**.

1. 輸入 **名稱** 和 **標題** 並按一下 **建立**.

您可以在專案中看到具有指定名稱和標題的排程資料夾。


## 檢視控制面板 {#viewing-dashboard}

在專案中建立排程資料夾後，您就可以從排程儀表板檢視詳細資訊。

請依照下列步驟檢視排程控制面板。 下列範例顯示 `We.Retail` 專案：

1. 導覽至 **時程表** 畫面資料夾(例如， `We.Retail`)專案。

   ![chlimage_1](assets/chlimage_1.png)

1. 按一下 **儀表板** 從動作列移除。

   您可以檢視三個不同的面板，例如 **排程資訊**， **已指派的管道**、和 **指派的顯示區**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **排程資訊面板** 按一下「排程資訊面板」右上角的「屬性」以檢視/變更排程的屬性。

   **已指派的色版面板** 按一下「指定色版」面板右上角的+指定色版，開啟「指定色版」對話方塊。

   **指派的顯示面板** 按一下「指派的顯示面板」中的任一顯示，以開啟顯示圖示板。

---
title: 建立和管理排程
seo-title: 管理排程
description: 請依照本頁面了解排程，這可讓您將管道整理成可重複使用的群組，如此一來，您就不必針對要顯示內容的每個顯示器個別重複指派。
seo-description: 請依照本頁面了解排程，這可讓您將管道整理成可重複使用的群組，如此一來，您就不必針對要顯示內容的每個顯示器個別重複指派。
uuid: c05328a0-620a-4597-b7b3-f4433e78d4e9
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 75ed3c42-4be9-42ae-9d76-e0343af81516
feature: 製作畫面
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# 建立和管理排程 {#creating-and-managing-schedules}

**AEM Screens中的排程**&#x200B;可讓您將管道整理成可重複使用的群組，如此一來，您就不需要針對要顯示內容的每個顯示器個別重複指派。

與&#x200B;***DayParting***&#x200B;結合時的排程可讓您設定一個全域排程，並在一天中的特定時間執行多個管道，並一次對所有顯示器重複使用該設定。

>[!NOTE]
>
>只有在您已安裝AEM 6.3 Sites Feature Pack 1時，才能使用此AEM Screens功能。 若要存取此Feature Pack，您必須聯絡Adobe支援並要求存取權。 擁有權限後，您就可以從「封裝共用」下載。

## 建立排程 {#creating-a-schedule}

您可以為Screens專案建立排程，以管理您使用案例的所有活動。

請依照下列步驟建立管道排程：

1. 依序選取Adobe Experience Manager連結（左上角）和Screens。 或者，您也可以直接前往：`http://localhost:4502/screens.html/content/screens`。
1. 導覽至Screens專案，然後按一下&#x200B;**排程**。
1. 按一下動作列中的&#x200B;**建立**。
1. 從&#x200B;**建立**&#x200B;嚮導中選擇&#x200B;**調度**，然後按一下&#x200B;**下一步**。

1. 輸入&#x200B;**Name**&#x200B;和&#x200B;**Title**，然後按一下&#x200B;**Create**。

您會在專案中看到具有指定名稱和標題的排程資料夾。


## 檢視控制面板 {#viewing-dashboard}

在專案中建立排程資料夾後，您就可以從排程控制面板檢視詳細資訊。

請依照下列步驟來檢視排程控制面板。 下列範例顯示We.Retail專案的控制面板：

1. 導覽至Screens（例如We.Retail）專案的&#x200B;**Schedules**&#x200B;資料夾。

   ![chlimage_1](assets/chlimage_1.png)

1. 從動作列按一下&#x200B;**控制面板**&#x200B;以開啟排程的控制面板。

   您可以檢視三個不同的面板，例如&#x200B;**排程資訊**、**已指派通道**&#x200B;和&#x200B;**已指派顯示**。

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **排程資** 訊面板按一下「排程資訊面板」右上角的「屬性」 ，以檢視/變更排程的屬性。

   **指定的通** 道面板按一下「指定通道」面板右上角的「指定通道」，以開啟「通道分配」對話框。

   **已分配的** 顯示面板從「已分配的顯示面板」中選擇任何顯示以開啟顯示面板。

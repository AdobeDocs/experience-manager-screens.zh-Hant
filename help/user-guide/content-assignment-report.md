---
title: 內容指派報表
description: 瞭解與AEM Screens相關的內容指派報告的下載和使用情況。
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 2%

---

# 內容指派報表 {#content-assignment-report}

內容指派報告功能可讓AEM Screens管理員或作者以試算表格式匯出&#x200B;*內容指派報告*。

## 使用內容指派報表 {#using-content-assignment-report}

「內容指派報表」可讓AEM Screens作者或管理員下載報表，此報表包含在AEM Screens專案中建立的所有管道中的所有資產，例如影像、影片。 此外，它包含指派給所有指定顯示器的整個通道資訊，以及此後指派給其指定顯示器的所有裝置。

「內容指派報表」不僅可讓您預覽所選AEM Screens專案中的所有頻道、Assets、顯示區和裝置，並提供您專案的高層級結構。


### 必要條件 {#pre-reqs}

下載「內容指派報表」之前，請確定您已設定包含頻道、位置和裝置的AEM Screens專案。
如需更多詳細資訊，請參閱下列資源：

1. [建立和管理專案](/help/user-guide/creating-a-screens-project.md)
1. [建立和管理管道](/help/user-guide/managing-channels.md)
1. [建立和管理位置](/help/user-guide/managing-locations.md)
1. [建立和管理顯示器](/help/user-guide/managing-displays.md)
1. [建立裝置](/help/user-guide/managing-devices.md)
1. [指派管道](/help/user-guide/channel-assignment-latest-fp.md)


## 下載內容指派報告 {#downloading-content-assignment-report-fp}

當您設定AEM Screens專案並依前述步驟所示指派顯示給每個位置時，請下載「內容指派報表」 。

>[!NOTE]
>「內容指定報表」功能只能在專案層級存取。

請依照下列指示下載「內容指派報表」：

1. 導覽至您的AEM Screens專案，然後按一下專案&#x200B;**DemoScreens**。

1. 按一下動作列中的&#x200B;**內容指派報告**。

   ![影像](/help/user-guide/assets/content-assignment-report/can-download.png)

1. 下載的試算表包含兩個標籤，例如&#x200B;**位置**&#x200B;和&#x200B;**內容**。 「位置」標籤會顯示四個資料行，例如&#x200B;**位置**、**顯示器**、**管道**&#x200B;和&#x200B;**裝置**，這些資料行可用來調查與您的AEM Screens專案相關的這四個實體。

   ![影像](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >試算表中顯示的資料會以容易閱讀的格式依字母順序排序。

1. 從&#x200B;**管道**&#x200B;資料行選取任何管道會開啟&#x200B;**內容**&#x200B;標籤。 接著，系統會直接將您導覽至該頻道，並提供與該特定頻道相關聯的資產（影像和影片）資訊。

   ![影像](/help/user-guide/assets/content-assignment-report/report-sheet2.png)

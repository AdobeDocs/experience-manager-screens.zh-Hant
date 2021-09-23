---
title: 內容指派報表
description: 此頁面說明內容指派報表的下載與使用方式。
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: 9e750b874253a5d1786e5ef78fc41d96e72b702d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 2%

---

# 內容指派報表 {#content-assignment-report}

「內容指派報表」功能可讓AEM Screens管理員或作者以試算表格式匯出&#x200B;*內容指派報表*。

## 使用內容分配報表 {#using-content-assignment-report}

「內容指派報表」可讓AEM Screens作者或管理員下載報表，該報表包含在AEM Screens專案中建立之所有管道中的所有資產，例如影像、視訊。 此外，它還包括分配給所有指定顯示器的整個通道的資訊，以及此後分配給其指定顯示器的所有設備的資訊。

「內容指派報表」不僅可預覽所選AEM Screens專案中的所有管道、資產、顯示器和裝置，也可提供專案的高階結構。


### 先決條件 {#pre-reqs}

下載「內容指派報表」之前，請務必先透過「頻道」、「位置」和「裝置」設定AEM Screens專案。
如需詳細資訊，請參閱下列資源：

1. [建立和管理專案](/help/user-guide/creating-a-screens-project.md)
1. [建立和管理管道](/help/user-guide/managing-channels.md)
1. [建立和管理位置](/help/user-guide/managing-locations.md)
1. [建立和管理顯示](/help/user-guide/managing-displays.md)
1. [建立裝置](/help/user-guide/managing-devices.md)
1. [指派管道](/help/user-guide/channel-assignment-latest-fp.md)


## 下載內容指派報表 {#downloading-content-assignment-report-fp}

設定AEM Screens專案，並將顯示指派給每個位置（如前述步驟所示）後，您就可以下載「內容指派報表」。

>[!NOTE]
>「內容指派報表」功能只能在專案層級存取。

請依照下列指示下載「內容指派報表」：

1. 導覽至您的AEM Screens專案，並選取專案&#x200B;**DemoScreens**。

1. 按一下動作列中的&#x200B;**內容指派報表**。

   ![影像](/help/user-guide/assets/content-assignment-report/can-download.png)

1. 下載的試算表包含兩個標籤，例如&#x200B;**Locations**&#x200B;和&#x200B;**Content**。 「位置」標籤顯示四列，如&#x200B;**Locations**、**Displays**、**Channels**&#x200B;和&#x200B;**Devices**，這些欄可用來進一步調查與您的AEM Screens專案相關的這四個實體。

   ![影像](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >試算表中顯示的資料會依字母順序排序，且易於閱讀。

1. 您可以按一下&#x200B;**頻道**&#x200B;欄中的任何頻道，開啟&#x200B;**內容**&#x200B;標籤，該標籤將直接導覽至該頻道，並將提供與該特定頻道相關的資產（影像和視訊）資訊，如下圖所示。

   ![影像](/help/user-guide/assets/content-assignment-report/report-sheet2.png)

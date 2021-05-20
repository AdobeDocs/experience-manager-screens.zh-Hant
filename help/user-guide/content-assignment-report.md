---
title: 內容指派報表
description: 此頁面說明內容指派報表的下載與使用方式。
feature: 製作畫面
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 2%

---

# 內容指派報表 {#content-assignment-report}

「內容指派報表」功能可讓AEM Screens管理員或作者以試算表格式匯出&#x200B;*內容指派報表*。

## 使用內容指派報表{#using-content-assignment-report}

「內容指派報表」可讓AEM Screens作者或管理員下載報表，該報表包含在AEM Screens專案中建立之所有管道中的所有資產，例如影像、視訊。 此外，它還包括分配給所有指定顯示器的整個通道的資訊，以及此後分配給其指定顯示器的所有設備的資訊。

「內容指派報表」不僅可預覽所選AEM Screens專案中的所有管道、資產、顯示器和裝置，也可提供專案的高階結構。


### 先決條件{#pre-reqs}

下載「內容指派報表」之前，請務必先透過「頻道」、「位置」和「裝置」設定AEM Screens專案。
如需詳細資訊，請參閱下列資源：

1. [建立和管理專案](/help/user-guide/creating-a-screens-project.md)
1. [建立和管理管道](/help/user-guide/managing-channels.md)
1. [建立和管理位置](/help/user-guide/managing-locations.md)
1. [建立和管理顯示](/help/user-guide/managing-displays.md)
1. [建立裝置](/help/user-guide/managing-devices.md)
1. [指派管道](/help/user-guide/channel-assignment-latest-fp.md)


## 下載內容指派報表{#downloading-content-assignment-report-fp}

設定AEM Screens專案，並將顯示指派給每個位置（如前述步驟所示）後，您就可以下載「內容指派報表」。

>[!NOTE]
>「內容指派報表」功能只能在專案層級存取。

請依照下列指示下載「內容指派報表」：

1. 導覽至您的AEM Screens專案，並選取專案&#x200B;**DemoScreens**。

1. 按一下動作列中的&#x200B;**內容指派報表**。

   ![影像](/help/user-guide/assets/content-assignment-report/can-download.png)

   >[!NOTE]
   >下載的試算表包含四欄，例如&#x200B;**Channels**、**Assets**、**Displays**&#x200B;和&#x200B;**Devices**，這四欄可用來進一步調查與您的AEM Screens專案相關的這四個實體。

1. 系統會將Excel工作表下載至本機電腦，且前置詞名稱與AEM Screens專案名稱相同。 例如，如果您的專案名稱為&#x200B;**DemoScreens**，下載的檔案名稱將是&#x200B;**demoscreens-content-assignment-report.xlxs**。

   ![影像](/help/user-guide/assets/content-assignment-report/car-download1.png)

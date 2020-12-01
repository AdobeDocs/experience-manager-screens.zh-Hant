---
title: 內容指派報表
description: 本頁說明「內容指派報表」的下載與使用。
translation-type: tm+mt
source-git-commit: b93baeeb26e48b906ee1ddfc034112f8b73615af
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 2%

---


# 內容指派報表 {#content-assignment-report}

「內容指派報表」功能可讓AEM Screens管理員或作者以試算表格式匯出&#x200B;*內容指派報表*。

## 使用內容分配報表{#using-content-assignment-report}

「內容指派報表」可讓AEM Screens作者或管理員下載報表，該報表包含在AEM Screens專案中建立之所有頻道中的所有資產，例如影像、視訊。 此外，它還包括分配給所有指定顯示器的整個通道的資訊，以及今後分配給其指定顯示器的所有設備的資訊。

「內容指派報表」不僅可預覽選取的AEM Screens專案中的所有頻道、資產、顯示和裝置，還提供專案的高階結構。

### 使用內容分配報表{#downloading-content-assignment-report-fp}

#### 設定項目{#setting-up-project}

請依照下列步驟，從AEM Screens專案下載「內容指派報表」:

1. 建立標題為&#x200B;**DemoScreens**&#x200B;的AEM畫面。

   ![影像](/help/user-guide/assets/content-assignment-report/car-1.png)

1. 在&#x200B;**DemoScreens**&#x200B;中建立兩個序列頻道，例如&#x200B;**ChannelOne**&#x200B;和&#x200B;**ChannelTwo**。

   ![影像](/help/user-guide/assets/content-assignment-report/car-2.png)

1. 選擇&#x200B;**ChannelOne**，然後從操作欄中按一下&#x200B;**編輯**。 新增很少的資產（影像／視訊）至此頻道。 同樣地，將資產新增至&#x200B;**ChannelTwo**。

1. 導覽至&#x200B;**DemoScreens** —> **Locations**&#x200B;的「位置」檔案夾，並建立三個不同位置，標題為&#x200B;**SanJose**、**Dublin**&#x200B;和&#x200B;**SanFrancisco**。

   ![影像](/help/user-guide/assets/content-assignment-report/car-3.png)

1. 導覽至每個位置，並為每個位置建立顯示，例如&#x200B;**SanJoseMain**，位於&#x200B;**SanJose**&#x200B;位置下，**DublinMain**&#x200B;位置下，以及&#x200B;**SanFranciscoMain**&#x200B;在&#x200B;**SanFrancisco**&#x200B;位置下。****

1. 為每個顯示器指定設備。

   >[!NOTE]
   >要瞭解如何將通道分配給顯示器，請參閱[通道分配](/help/user-guide/channel-assignment.md)。

#### 下載內容分配報表{#downloading-content-assignment-report}

一旦您設定了AEM Screens專案，並指派顯示給前述步驟所示的每個位置，您就可以下載「內容指派報表」。

>[!NOTE]
>「內容指派報表」功能只能在專案層級存取。

請依照下列指示下載「內容指派報表」:

1. 導覽至您的AEM Screens專案，然後選取專案&#x200B;**DemoScreens**。

1. 從動作列按一下「內容指派報表」。 ****&#x200B;應將Excel表單下載到本機電腦。

   ![影像](/help/user-guide/assets/content-assignment-report/can-download.png)

   >[!NOTE]
   >下載的試算表包含四欄，例如&#x200B;**Channels**、**Assets**、**Displays**&#x200B;和&#x200B;**Devices**，可用來進一步調查與AEM Screens專案相關的這四個實體。






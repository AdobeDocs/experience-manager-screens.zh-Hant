---
title: 內嵌順序
description: 瞭解管道的內嵌序列可讓您在父管道中新增元件。 或者，重複使用其他管道的內容，並將其嵌入父管道。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: cdfaee19-15d9-4bcb-bc85-0b43c59d88d2
TQID: https://experienceleague.adobe.com/NK6M9ShPUQdDQQvgx7kD9c4uvfKjy61wJ6jSH0gB17E
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: ba4275ba-c29a-4197-90dc-5a633402ca3c
  - id: d4878390-3838-4e80-8cb3-33bc1a01ea16
  - id: d8a4be83-7d41-47be-b4a6-f8f3d35caceb
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 811
ht-degree: 0%

---

# 內嵌順序 {#embedded-sequences}

>[!IMPORTANT]
>此內容對AEM內部部署/AMS （AEM 6.5LTS和AEM 6.5）有效。 如需AEM as a Cloud Service Screens內容，請參閱[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

針對管道使用&#x200B;***內嵌序列***，可讓使用者在父管道中新增元件，也可以重複使用來自不同管道的內容，並將其內嵌到父管道中。

## 新增內嵌順序 {#adding-embedded-sequences}

您可以選擇將下列元件新增至序列頻道：

* 嵌入順序
* 動態嵌入序列

>[!NOTE]
>
>若要瞭解如何在您的Screens專案中使用其他元件，請參閱[將元件新增至頻道](adding-components-to-a-channel.md)。

### 新增內嵌順序 {#adding-an-embedded-sequence}

您可以將內嵌序列新增至頻道。 內嵌序列是另一個包含影像或視訊等資產的管道。 新增內嵌序列可讓使用者透過&#x200B;***頻道路徑***&#x200B;將序列新增至頻道。

>[!NOTE]
>***管道路徑***定義了管道的明確參照。
>若要深入瞭解&#x200B;*頻道路徑*，請參閱Screens編寫中的[頻道指定任務](channel-assignment.md)。

請依照下列步驟，將內嵌序列新增至您的頻道：

1. 按一下您要內嵌頁面的管道。 例如，**`We.Retail`店內** > **管道** > **閒置管道**。

1. 按一下動作列中的&#x200B;**編輯**。
1. 在編輯器模式中，按一下左側列中的元件圖示，即可新增內嵌頁面。 將&#x200B;**內嵌順序**&#x200B;拖放至編輯器。
1. 連按兩下&#x200B;**內嵌順序**&#x200B;元件，以便您將頻道新增至您的原始順序頻道。
1. 按一下通道的&#x200B;**通道路徑**。
1. 在&#x200B;**順序**&#x200B;索引標籤中，按一下內嵌頻道的&#x200B;**持續時間（毫秒）**。 根據預設，持續時間設定為&#x200B;**-1**，表示內嵌頻道已完全執行。 如果使用者指定持續時間，則次序列會在指定時間中斷（即切斷）。

1. 將&#x200B;**計量播放策略**&#x200B;設定為&#x200B;**標準**。

預設為&#x200B;**標準**。 將值設定為&#x200B;**標準** （播放所有專案）表示子序列會在父序列的每個週期中完全執行。 另一個可能的值為&#x200B;**播放單一專案**。 此值在每次執行時只顯示一個子序列專案。 例如，第一個回圈上的第一個專案，以及第二個回圈上的第二個專案。

>[!IMPORTANT]
>
>將內嵌順序中使用的管道指派給相同顯示。
>
>依照下列步驟將內嵌序列新增至管道後，請依照下列步驟操作：
>
>1. 導覽至顯示區，然後從&#x200B;**位置**&#x200B;資料夾按一下顯示區。
>1. 從動作列按一下&#x200B;**儀表板**。
>1. 在顯示控制面板上，按一下&#x200B;**已指派的管道和已排程的面板**&#x200B;中的&#x200B;**+指派管道**，以開啟&#x200B;**管道指派對話方塊**。
>
>1. 按一下您在內嵌順序中使用的管道路徑，在&#x200B;**管道路徑**&#x200B;中。
>1. 請確定&#x200B;**優先順序**&#x200B;低於主要管道。
>
>1. 請勿按一下任何&#x200B;**支援的事件**。
>1. 完成時，按一下&#x200B;**儲存**。
>

下列範例顯示將內嵌序列(**Idle Channel - Night**)新增至現有通道(**Idle Channel**)。

![新2](assets/new2.gif)

### 新增動態內嵌序列 {#adding-a-dynamic-embedded-sequence}

您可以將動態內嵌序列新增至頻道。 動態內嵌序列與內嵌序列類似，但允許使用者遵循階層，對其中一個管道所做的變更/更新會傳播至相關的另一個管道。 它遵循上下階層，也包含影像或視訊等資產。 新增動態序列可讓使用者依頻道角色新增頻道。

>[!NOTE]
>
>***頻道角色***&#x200B;定義顯示的內容。
>
>若要深入瞭解&#x200B;*頻道角色*，請參閱編寫Screens中的[頻道指定任務](channel-assignment.md)。

請依照下列步驟，將內嵌序列新增至您的頻道：

1. 按一下您要內嵌動態序列的管道。 例如，**`We.Retail`店內** > **管道** > **閒置管道**。

1. 按一下動作列中的&#x200B;**編輯**。
1. 在編輯器模式中，按一下左側列中的元件圖示，即可新增動態內嵌序列。 將&#x200B;**動態** **內嵌順序**&#x200B;拖放至編輯器。

1. 連按兩下&#x200B;**動態** **內嵌順序**&#x200B;元件，讓您可以將頁面新增至順序頻道。

1. 輸入&#x200B;**頻道指派角色**。
1. 將&#x200B;**計量播放策略**&#x200B;設定為&#x200B;**標準**。 預設為&#x200B;**標準**。 將值設定為&#x200B;**標準** （播放所有專案）表示子序列會在父序列的每個週期中完全執行。 另一個可能的值為&#x200B;**播放單一專案**。 此值在每次執行時只顯示一個子序列專案。 例如，第一個回圈上的第一個專案，以及第二個回圈上的第二個專案。

1. 按一下序列中內嵌頻道之&#x200B;**序列**&#x200B;索引標籤中的&#x200B;**持續時間（毫秒）**。

![latest](assets/latest.gif)

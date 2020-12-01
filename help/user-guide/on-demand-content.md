---
title: 隨選內容更新
seo-title: 隨選內容更新
description: '請依本頁瞭解隨選內容更新。  '
seo-description: '請依本頁瞭解隨選內容更新。  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 8492bdd071ae029a68ec4a4983c79ce326cac38b
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 0%

---


# 隨選內容更新{#on-demand}

本節說明管理出版物的隨選內容。

## 管理出版物：將內容更新從作者傳送至發佈至裝置{#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

您可以從AEM Screens發佈和取消發佈內容。 「管理出版物」功能可讓您將內容更新從作者傳送至裝置。 您可以針對整個AEM Screens專案，或僅針對其中一個頻道、位置、裝置、應用程式或排程發佈／取消發佈內容。

### 管理AEM Screens專案的出版物{#managing-publication-for-an-aem-screens-project}

請依照下列步驟，將內容更新從作者傳送至AEM Screens專案的裝置：

1. 導覽至您的AEM Screens專案。
1. 按一下動作列中的「管理出版物」(Manage Publication)**，以發佈專案以發佈例項。**

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. 將開啟&#x200B;**管理出版物**&#x200B;嚮導。 您可以選取&#x200B;**Action**，並排程目前或更新版本的發佈時間。 按一下&#x200B;**下一步**。

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. 選中該框，從&#x200B;**管理出版物**&#x200B;嚮導中選擇整個項目。

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. 從操作欄按一下「包含子項」(**+ Include Children)，取消選中所有選項以發佈項目中的所有模組，然後按一下「添加」(Add)以發佈。******

   >[!NOTE]
   >
   >預設情況下，將選中所有框，您必須手動取消選中這些框才能發佈項目中的所有模組。

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **瞭解包含子項對話框**

   上述步驟顯示如何發佈整個內容。 如果您想要使用其他三種替代方案，您必須勾選該特定選項。
例如，下列影像可讓您僅管理和更新專案中已修改的頁面：
   ![影像](assets/author-publish-manage.png)

   請依照下列說明了解可用選項：

   1. **僅包含直接子項**:此選項僅允許您管理項目結構中子節點的更新。
   1. **僅包含已修改的頁面**:此選項僅允許您管理在項目結構中找到更改的修改後頁面的更新。
   1. **僅包含已發佈的頁面**:此選項僅允許管理先前發佈之頁面的更新。


1. 從&#x200B;**管理出版物精靈按一下** Publish **。**

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >等待幾秒／分鐘，讓內容進入發佈執行個體。
   >
   >
   >    1. 如果專案中沒有變更，而&#x200B;**「更新離線內容」**&#x200B;沒有變更，工作流程將無法運作。
   >    1. 如果作者未完成複製過程（內容仍在上傳到發佈實例），則在管理發布工作流程中按一下&#x200B;**Publish**&#x200B;按鈕後，該工作流將無法運作。


   >[!CAUTION]
   >如果您是作者或內容建立者，想要查看附加至作者例項的裝置中的變更，請從頻道儀表板按一下「更新離線內容&#x200B;**」，或選取專案。**&#x200B;在這種情況下，更新離線內容只會在作者實例中執行。

1. 導覽至專案，然後從動作列按一下「更新離線內容&#x200B;**」。**&#x200B;此動作會將相同的命令轉送至發佈例項，以便離線Zip也能在發佈例項上建立。

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >在您完成管理出版物工作流程後，如果有播放器指向作者例項，您必須觸發作者中的更新離線內容，以便在作者例項上離線建立更新。

   >[!CAUTION]
   >
   >如果您有已註冊至作者伺服器的播放器，您必須在作者實例中觸發更新離線內容。 註冊至發佈例項的播放器不需要更新離線內容。

### 管理渠道{#managing-publication-for-a-channel}的發佈

請依照下列步驟，將內容更新從作者傳送至AEM Screens專案中頻道的裝置：

>[!NOTE]
>
>只有在渠道中有變更時，才要遵循本節。 如果頻道在先前更新離線內容後沒有任何變更，則個別頻道的管理出版工作流程將無法運作。

1. 導覽至您的「畫面」專案，然後選取頻道。
1. 按一下動作列中的「管理出版物」，以發佈頻道以發佈例項。****

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. 將開啟&#x200B;**管理出版物**&#x200B;嚮導。 您可以選取&#x200B;**Action**，並排程目前或更新版本的發佈時間。 按一下&#x200B;**下一步**。

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. 從&#x200B;**管理出版物精靈按一下** Publish **。**

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >等待幾秒／分鐘，讓內容進入發佈執行個體。

1. 在頻道儀表板中觸發&#x200B;**更新離線內容**&#x200B;只會將離線內容推送至製作例項，但不會發佈例項。 步驟1-4是將離線內容推送至發佈例項。

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >您必須先發佈，然後觸發更新離線內容，如前面步驟所概述。

### 頻道和裝置重新指派：{#channel-and-device-re-assignment}

如果您已重新指派裝置，則必須在裝置重新指派至新顯示後，同時發佈初始顯示和新顯示。

同樣地，如果您已重新指派渠道，則必須在將渠道重新指派至新顯示後，同時發佈初始顯示和新顯示。
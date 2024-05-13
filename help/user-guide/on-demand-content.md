---
title: 隨選內容更新
description: 瞭解用於管理出版物的隨選內容更新。
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 9ffdb1eb-a1ba-42ac-a30f-260004e5b165
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---

# 隨選內容更新 {#on-demand}

本節說明用於管理出版物的隨選內容。

## 管理出版物：將內容更新從作者傳送到發佈到裝置 {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

您可以從AEM Screens發佈和取消發佈內容。 「管理出版物」功能可讓您從作者傳送內容更新到發佈到裝置。 您可以為整個AEM Screens專案或僅限其中一個管道、位置、裝置、應用程式或排程發佈/取消發佈內容。

### 管理AEM Screens專案的出版物 {#managing-publication-for-an-aem-screens-project}

請依照下列步驟，針對AEM Screens專案，將內容更新從作者傳送至發佈裝置：

1. 導覽至您的AEM Screens專案。
1. 按一下 **管理發布** ，讓您可以將專案發佈至您的發佈執行個體。

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. 此 **管理發布** 精靈開啟。 您可以按一下 **動作** 以及將發佈時間排程為現在或以後。 按一下「**下一步**」。

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. 核取該方塊，以便您按一下 **`Manage Publication`** 精靈。

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. 按一下 **+包含子項** 並取消勾選所有選項，以便發佈專案中的所有模組，然後按一下 **新增** 以發佈。

   >[!NOTE]
   >
   >依預設，所有方塊都會勾選，您必須手動取消勾選方塊以發佈專案中的所有模組。

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **瞭解包含子系對話方塊**

   上述步驟說明如何發佈整個內容。 如果您想要使用其他三個可用的替代方案，則必須核取該特定選項。
例如，下列影像顯示如何只管理和更新專案中已修改的頁面：
   ![影像](assets/author-publish-manage.png)

   請依照下列說明操作，以瞭解可用的選項：

   1. **僅包含直接子項**：此選項可讓您僅管理專案結構中子節點的更新。
   1. **僅包含已修改的頁面**：此選項可讓您僅管理在專案結構中找到變更之專案已修改頁面的更新。
   1. **僅包含已發佈的頁面**：此選項可讓您僅管理對之前已發佈頁面的更新。


1. 從 **`Manage Publication wizard`**，按一下 **發佈**.

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >請等候幾秒鐘/分鐘，讓內容可到達發佈執行個體。
   >
   >
   >    1. 如果專案沒有任何變更，而且沒有任何變更，工作流程則無法運作 **更新離線內容**.
   >    1. 如果作者在選取「 」後未完成復寫程式（內容仍上傳至發佈執行個體），工作流程將無法運作 **發佈** 管理工作流程中的按鈕。

   >[!CAUTION]
   >作為內容建立者，如果您想檢視附加至製作例項的裝置變更，請按一下 **更新離線內容** 從頻道控制面板中或選取專案。 在此情況下，離線內容的更新只會在Author例項中執行。

1. 導覽至專案並按一下 **更新離線內容** 從動作列移除。 這個動作會將相同的命令轉送給發佈執行個體，因此離線ZIP也會在發佈執行個體上建立。

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >完成管理發布工作流程後，如果播放器指向Author例項，則觸發author中的更新離線內容。 這樣做會在作者執行個體上離線建立更新。

   >[!CAUTION]
   >
   >如果您已將播放器註冊到作者伺服器，則在Author例項中觸發更新離線內容。 已註冊至發佈執行個體的播放器不需要更新離線內容。

### 管理管道的出版物 {#managing-publication-for-a-channel}

請依照下列步驟，針對AEM Screens專案中的管道，從「作者>發佈>裝置」傳送內容更新：

>[!NOTE]
>
>只有在管道發生變更時，才按照本節操作。 如果之前更新離線內容後管道沒有任何變更，則個別管道的管理發布工作流程將無法運作。

1. 導覽至您的AEM Screens專案，然後按一下頻道。
1. 按一下 **管理發布** ，以便將頻道發佈至您的發佈執行個體。

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. 此 **管理發布** 精靈開啟。 您可以按一下 **動作** 以及將發佈時間排程為現在或以後。 按一下「**下一步**」。

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. 按一下 **發佈** 從 **`Manage Publication`** 精靈。

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >請等候幾秒鐘/分鐘，讓內容可到達發佈執行個體。

1. 正在觸發 **更新離線內容** 在管道儀表板中，只會將離線內容推送至作者例項，而不會推送至發佈例項。 步驟1至4是將離線內容推送至發佈例項。

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >先發佈，然後觸發更新離線內容，如先前步驟所概述。

### 頻道與裝置重新指派： {#channel-and-device-re-assignment}

如果您已重新指定裝置，請在裝置重新指定至新顯示後，發佈初始顯示和新顯示。

同樣地，如果您已重新指定管道，一旦管道重新指定給新顯示時，請發佈初始顯示和新顯示。

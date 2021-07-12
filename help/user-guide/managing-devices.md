---
title: 管理裝置
seo-title: 管理裝置
description: 本頁介紹設備分配。
seo-description: 請參照本頁了解設備分配。 「設備」控制台允許您訪問設備管理器，將設備分配給顯示器。
uuid: 889cc11c-60f7-4966-82b5-9ebdd082a3c5
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8dc08e29-a377-4e84-84ee-442470c19019
feature: 製作畫面
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# 管理裝置 {#managing-devices}

本頁介紹設備分配。

「設備」控制台允許您訪問設備管理器，將設備分配給顯示器。

>[!CAUTION]
>
>在分配設備之前，您需要註冊它。 有關詳細資訊，請參閱[設備註冊](device-registration.md)。

## 設備分配 {#device-assignment}

請依照下列步驟將裝置指派給顯示器：

1. 導覽至專案的「裝置」資料夾，例如

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. 選取您的&#x200B;**Devices**&#x200B;資料夾，然後點選/按一下動作列中的&#x200B;**Device Manager**。 將顯示已分配和未分配的設備。

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. 從清單中選擇未分配的設備，然後點選/按一下操作欄中的&#x200B;**分配設備**。

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. 從清單中選擇要將設備指派到的顯示，然後點選/按一下&#x200B;**Assign**。

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. 點選/按一下&#x200B;**完成**&#x200B;以完成指派程式。


   顯示控制面板在&#x200B;**DEVICES**&#x200B;面板中顯示指定的設備。

   ![chlimage_1-37](assets/chlimage_1-37.png)

   按一下(**...**)，以新增裝置設定或更新裝置。****

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>每次將第一個裝置新增至新的Screens專案時，都會建立使用者群組。
>例如，如果專案節點名稱為&#x200B;*we-retail*，則使用者群組名稱為&#x200B;*screens-we-retail-devices*。
>此組將添加為&#x200B;**貢獻者**&#x200B;組的成員，如下圖所示：

![chlimage_1-39](assets/chlimage_1-39.png)

### 後續步驟 {#the-next-steps}

熟悉將管道指派給顯示器後，請參閱下列資源：

* [監視和疑難排解](monitoring-screens.md)

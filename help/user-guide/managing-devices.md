---
title: 管理裝置
description: 瞭解AEM Screens中的裝置指派和管理。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 7%

---

# 管理裝置 {#managing-devices}

此頁面說明裝置指定任務。

裝置主控台可讓您存取裝置管理員，將裝置指派給顯示器。

>[!CAUTION]
>
>指派裝置之前，請先註冊該裝置。 另請參閱 [裝置註冊](device-registration.md).

## 裝置指派 {#device-assignment}

請依照下列步驟，將裝置指定給顯示器：

1. 導覽至專案的「裝置」資料夾，例如

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. 按一下 **裝置** 資料夾並按一下 **裝置管理員** 於動作列中。 已指派和未指派的裝置隨即顯示。

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. 從清單中按一下未指派的裝置，然後按一下 **指派裝置** 於動作列中。

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. 從清單中按一下您要指派裝置的顯示畫面，然後按一下 **指派**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. 按一下 **完成** 以完成指定流程。


   顯示控制面板會在 **裝置** 面板。

   ![chlimage_1-37](assets/chlimage_1-37.png)

   按一下(**...**)的右上角 **裝置** 面板以新增裝置設定或更新裝置。

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>每次將第一個裝置新增到新的Screens專案時，都會建立使用者群組。
>例如，如果專案節點名稱為 *we-retail*，則使用者群組名稱為 *screens-we-retail-devices*.
>此群組已新增為 **貢獻者** 群組，如下圖所示：

![chlimage_1-39](assets/chlimage_1-39.png)

### 後續步驟 {#the-next-steps}

熟悉指定顯示區通道後，請參閱[監視和疑難排解](monitoring-screens.md).

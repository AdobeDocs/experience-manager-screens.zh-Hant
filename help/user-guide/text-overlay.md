---
title: 文字重疊
seo-title: Text Overlay
description: 文本覆蓋功能是AEM Screens提供的一項功能，通過提供覆蓋在影像頂部的標題或描述，您可以在序列通道中建立引人入勝的體驗。 請按照此頁瞭解詳細資訊。
seo-description: Text Overlay is a feature available in AEM Screens that allows you to create a compelling experience in a Sequence Channel by providing a title or a description overlaid on top of an image. Follow this page to learn more.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 2%

---

# 文字重疊 {#text-overlay}

本節介紹以下主題：

* **概觀**
* **使用文本覆蓋**
* **瞭解文本覆蓋屬性**
* **在文本覆蓋中使用ContextHub值**

>[!CAUTION]
>
>的 **文本覆蓋** 只有安裝了6.3功能包AEM 5或6.4功能包AEM 3時，功能才可用。

## 概觀 {#overview}

文本覆蓋功能是AEM Screens提供的一項功能，通過提供覆蓋在影像頂部的標題或描述，您可以在序列通道中建立引人入勝的體驗。

要瞭解如何建立您自己的自定義元件，請參閱 **擴展AEM Screens元件**。

本節僅介紹如何在AEM Screens項目中使用和應用海報元件，並將其用作序列通道中的文本覆蓋。

## 使用文本覆蓋 {#using-text-overlay}

下節介紹在AEM Screens項目中使用文本覆蓋。

**必備條件**

在開始實施此功能之前，請確保已將項目設定為開始實施文本覆蓋的先決條件。 例如，

* 建立AEM Screens項目(在本示例中， **文本覆蓋演示**)

* 建立名為 **文本示例** 在 **頻道** 資料夾

* 將內容添加到 **文本示例** 頻道

下圖顯示 **文本覆蓋演示** 項目 **文本示例** 通道 **頻道** 的子菜單。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

按照以下步驟在AEM Screens頻道中使用文本覆蓋：

1. 導航到 **文本覆蓋演示** —> **頻道** —> **文本示例** 按一下 **編輯** 的子菜單。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 選擇影像並按一下 **配置** （扳手錶徵圖）開啟「屬性」(properties)對話框。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 選擇 **文本覆蓋** 的子菜單。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 瞭解文本覆蓋屬性 {#understanding-text-overlay-properties}

使用「文本覆蓋」屬性，可以將文本添加到「螢幕」項目中的任何元件。 以下部分概述了「文本覆蓋」中可用的屬性：

![text](assets/text.gif)

您可以向文本框添加文本，並添加排版強調，如粗體、斜體和下划線。

**顏色變體** 此選項允許文本為「深色」（黑色文本）或「淺色」（白色文本）。

**調整和定位** 此選項允許用戶水準或垂直對齊文本，或使用細粒度工具對齊文本。

>[!NOTE]
>
>要正確使用細粒度工具，請確保使用(px)作為尾碼（例如200像素）以像素表示的正確位置。 此表達式的結果是從起始點到200像素。

## 在文本覆蓋中使用ContextHub值 {#using-text-overlay-context-hub}

以下部分介紹資料儲存中值的使用情況，例如，文本覆蓋元件中的google工作表。

**必備條件**

為您的AEM Screens項目設定ContextHub配置。

要瞭解如何使用資料儲存設定和管理資料驅動的資產更改，請參閱 [在AEM Screens配置ContextHub](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/configuring-context-hub.html)。

設定項目所需的配置後，請按照以下步驟使用谷歌工作表中的值：

1. 導航到 **文本覆蓋演示** —> **頻道** —> **文本示例** 按一下 **屬性** 按鈕。

1. 選擇 **個性化** 頁籤，以設定ContextHub配置。

   1. 選擇 **上下文中心路徑** 如 **液體** > **設定** > **雲設定** > **預設** > **ContextHub配置** 按一下 **選擇**。

   1. 選擇 **段路徑** 如 **會議** > **螢幕** > **設定** > **寬** > **段** 按一下 **選擇**。

   1. 按一下&#x200B;**「儲存並關閉」**。

      >[!NOTE]
      >
      >使用ContextHub和Segments路徑，在其中您最初保存了上下文中心配置和段。

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. 導航到 **文本覆蓋演示** —> **頻道** —> **文本示例** 按一下 **編輯** 的子菜單。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 將影像和文本覆蓋元件添加到影像中，如所述 [使用文本覆蓋](/help/user-guide/text-overlay.md#using-text-overlay) 的子菜單。

1. 按一下 **配置** （扳手錶徵圖）以開啟 **影像** 對話框。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 導航到 **上下文中心** 的 **影像** 對話框。 按一下 **添加**。

   >[!NOTE]
   >如果尚未設定ContextHub配置，則此選項將為項目禁用。

1. 輸入 **值** 的 **佔位符** 的子菜單。 選擇要從中的Google工作表獲取值的行 **ContextHub變數**。 在這種情況下，從Google工作表的第2行和第1列檢索該值。 現在輸入 **預設值** 如 **20**，如下圖所示。 完成後，按一下複選標籤。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >以下影像顯示了從google工作表中檢索到的值，供您參考：

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 導航到 **文本覆蓋** 的子菜單。 *當前溫度{Value}*，如下圖所示。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 按一下 **預覽** 的子菜單。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)

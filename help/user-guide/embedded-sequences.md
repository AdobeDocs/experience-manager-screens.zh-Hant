---
title: 嵌入序列
seo-title: Embedded Sequences
description: 按照本頁瞭解通道的嵌入序列，這些序列允許用戶在父通道中添加元件，還可以從不同的通道重新使用內容並將其嵌入父通道。
seo-description: Follow this page to learn about embedded sequences for channels that allows the user to add components in the parent channel and also to re-use the content from a different channel and embed it into the parent channel.
uuid: 72a8d4e6-e5ce-4069-bf3b-864d03f61585
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: fc13d713-af30-4a54-8408-920f78fd2b2f
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: cdfaee19-15d9-4bcb-bc85-0b43c59d88d2
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 2%

---

# 嵌入序列 {#embedded-sequences}

使用 ***嵌入序列***，對於頻道，允許用戶在父頻道中添加元件，還可以重新使用來自不同頻道的內容並將其嵌入父頻道。

## 添加嵌入序列 {#adding-embedded-sequences}

您可以選擇將以下元件添加到序列通道：

* 內嵌順序
* 動態內嵌序列

>[!NOTE]
>
>要瞭解在「螢幕」項目中使用其他元件的資訊，請參閱 [將元件添加到通道](adding-components-to-a-channel.md)。

### 添加嵌入序列 {#adding-an-embedded-sequence}

可以將嵌入序列添加到通道。 嵌入序列是包括諸如影像或視頻等資產的另一個渠道。 添加嵌入序列允許用戶通過 ***通道路徑***。

>[!NOTE]
>***通道路徑*** 定義對通道的顯式引用。
>瞭解有關 *通道路徑*，請參閱 [渠道分配](channel-assignment.md) 在創作螢幕中。

按照以下步驟將嵌入序列添加到通道：

1. 選擇要嵌入頁面的通道。 比如說， **We.Retail In-Store** —> **頻道** —> **空閒通道**。

1. 按一下 **編輯** 的子菜單。
1. 按一下左側欄上的元件表徵圖以添加嵌入頁面。 拖放 **嵌入序列** 編輯。
1. 按兩下 **嵌入序列** 元件將通道添加到原始序列通道。
1. 選擇 **通道路徑** 頻道。
1. 選擇 **持續時間（毫秒）** 為您的嵌入式通道 **序列** 頁籤。 預設情況下，持續時間設定為 **-1**&#x200B;即嵌入式通道完全運行。 如果用戶指定持續時間，則子序列將在指定時間被中斷（即斷開）。

1. 設定 **計量播放策略** 至 **正**。

預設情況下，它設定為 **正**。 將值設定為 **正** （播放所有項目）表示子序列將在父序列的每個循環上完全運行。 另一個可能的值是 **播放單個項目** （播放單個項目），並且每次運行時只顯示子項（例如，第一個循環上的第一個項目，第二個循環上的第二個項目，等等）。

>[!IMPORTANT]
>
>必須將通道（在嵌入序列中使用）指定到同一顯示。
>
>在將嵌入序列添加到通道後，按照以下步驟操作：
>
>1. 導航到顯示並從中選擇顯示 **位置** 的子菜單。
>1. 按一下 **儀表板** 的子菜單。
>1. 選擇 **+分配通道** 從 **指定的通道和計畫面板** 開啟 **「通道分配」對話框**。
>
>1. 選擇您（在嵌入序列中使用）的通道的路徑 **通道路徑**。
>1. 確保 **優先順序** 低於主通道。
>
>1. 不能選擇任何 **支援的事件**。
>1. 按一下 **保存** 一次。

>


以下示例顯示嵌入序列(**空閒頻道 — 夜晚**)到現有通道(**空閒通道**)。

![new2](assets/new2.gif)

### 添加動態嵌入序列 {#adding-a-dynamic-embedded-sequence}

可以向通道中添加動態嵌入序列。 動態嵌入序列類似於嵌入序列，但允許用戶遵循層次結構，其中對一個通道所做的更改/更新被傳播到相關的其它通道。 它遵循上下階層，也包含影像或視訊等資產。添加動態序列允許用戶按通道角色添加通道。

>[!NOTE]
>
>***渠道角色*** 定義通道角色定義顯示的上下文。
>
>瞭解有關 *渠道角色*，請參閱 [渠道分配](channel-assignment.md) 在創作螢幕中。

按照以下步驟將嵌入序列添加到通道：

1. 選擇要嵌入動態序列的通道。 比如說， **We.Retail In-Store** —> **頻道** —> **空閒通道**。

1. 按一下 **編輯** 的子菜單。
1. 按一下左側欄上的元件表徵圖以添加動態嵌入序列。 拖放 **動態** **嵌入序列**  編輯。

1. 按兩下 **動態** **嵌入序列** 元件將頁面添加到序列通道。

1. 輸入 **渠道分配角色**。
1. 設定 **計量播放策略** 至 **正**。 預設情況下，它設定為 **正**。 將值設定為 **正** （播放所有項目）表示子序列將在父序列的每個循環上完全運行。 另一個可能的值是 **播放單個項目** （播放單個項目），並且每次運行時只顯示子項（例如，第一個循環上的第一個項目，第二個循環上的第二個項目，等等）。

1. 選擇 **持續時間（毫秒）** 在 **序列** 的子菜單。

![最新](assets/latest.gif)

---
title: 在AEM Screens使用自適應格式副本
description: 本頁介紹如何在AEM Screens使用自適應格式副本。
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: cd26f77b9b41a5854aaa1f936abed3b410533684
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# 在AEM Screens使用自適應格式副本 {#adaptive-renditions}

## 簡介 {#introduction}

自適應格式副本允許設備根據客戶定義的規則自動為設備選擇最佳格式副本。 這些設備將根據這些規則自動下載並播放資產的最合適格式副本，使客戶只能專注於設計 *主* 體驗。

## 目標 {#objective}

作為AEM Screens內容作者，您現在可以配置特定於設備的資產格式副本，以便自動下載和播放，而無需手動建立所有內容變體。
開發人員添加格式副本映射屬性和規則後，您現在就可以將格式副本映射應用於資產，然後包括位於AEM Screens通道中的資產。

>[!IMPORTANT]
>在開始使用「自適應格式副本」之前，建議在AEM Screens渠道中瞭解此功能的「體系結構概述和配置」。 請參閱 [自適應格式副本：體系結構概述和配置](/help/user-guide/adaptive-renditions.md) 的子菜單。

## 在通道中使用自適應格式副本 {#using-adaptive-renditions}

>[!NOTE]
>添加後 [格式副本映射屬性到螢幕項目](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) 和 [格式副本映射規則](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)，作為「內容作者」，您現在可以將格式副本應用於您的資產。

### 將格式副本應用於資產 {#apply-renditions-assets}

按照以下步驟將格式副本應用於您要在「旅遊螢幕」頻道中使用的資產：

1. 導航到 **資產** 檔案AEM夾。

1. 建立更適合標牌顯示的資產版本，例如， `seahorse.jpg`。

1. 選擇格式副本命名模式，例如，`landscape`，類似於 **圖案** 物業 **CRXDE Lite**。 請參閱 [添加格式副本映射規則](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) 的子菜單。

1. 按一下 **添加格式副本** 上載格式副本，如下圖所示。

   ![影像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. 選擇更名的資產檔案。 要添加的格式副本必須包含該模式（在步驟3中定義），例如， `seahorse-landscape.png`。

1. 添加資產後，選擇資產並按一下 **管理發布** 按鈕。

   ![影像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >請參閱 [按需內容更新](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content.html?lang=en) 瞭解有關管理發布和將內容更新從「作者」發佈到設備的詳細資訊。


## 遷移策略 {#migration-strategy}

>[!IMPORTANT]
>對於大型網路，建議逐步執行遷移以降低風險，因為此功能將對清單和檔案儲存格式進行更改。 添加 `sling:configRef` 整個項目涉及讓所有玩家更新到功能包6.5.9。如果您更新了某些玩家，則需要添加 `sling:configRef` 僅到所有玩家都更新到功能包6.5.9的顯示器、位置或渠道資料夾。

下圖描述了大型網路的遷移策略：

![影像](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

要啟用該功能，請至少添加一個映射規則，並確保格式副本映射配置可以在顯示和通道的上下文中解析。 按照以下步驟遷移：

1. 添加 [格式副本映射規則](/help/user-guide/adaptive-renditions.md)。
1. 為新通道建立資料夾，並添加指向格式副本映射配置的引用。
1. 建立新頻道以替換舊頻道並上載格式副本。
1. 重新指配顯示到新頻道。
1. 添加對遷移顯示或指向格式副本映射配置的位置的引用。
1. 對所有剩餘通道和顯示重複步驟3、4和5。

   >[!NOTE]
   >完成遷移後，確保從通道、顯示和位置刪除所有配置引用，並將單個配置引用添加到項目內容節點。

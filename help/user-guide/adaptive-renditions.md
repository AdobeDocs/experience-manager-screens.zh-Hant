---
title: 自適應格式副本體系結構概述和配置
description: 本頁介紹了在AEM ScreensCRXDE Lite中用於自適應格式副本的體系結構概述和配置。
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: e5da55eeb5da3d0ef9f21bd47bfec75d660a6a1e
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 2%

---

# 自適應格式副本：體系結構概述和配置 {#adaptive-renditions}

## 簡介 {#introduction}

自適應格式副本允許設備根據客戶定義的規則自動為設備選擇最佳格式副本。 這些設備將根據這些規則自動下載並播放資產的最合適格式副本，使客戶只能專注於設計 *主* 體驗。

## 目標 {#objective}

作為AEM Screens開發人員，您現在可以配置特定於設備的資產格式副本，以便自動下載和播放，而無需手動建立所有內容變體。 必須先配置自適應格式副本，內容作者才能在AEM Screens頻道中使用此功能。

## 架構概述 {#architectural-overview}

自適應格式副本基於按照特定命名約定命名多個資產格式副本的想法。 播放特定格式副本的決定是通過評估媒體查詢表達式來做出的，這些表達式只能在具有預期功能的設備上解析。

具有關聯的格式副本命名模式的能力定義格式副本映射規則，如下圖所示：縱向或橫向。 計算所有可用表達式後，螢幕播放器將收集與匹配規則對應的命名模式。 這些模式用於在序列回放期間通過查找格式副本名稱中的模式來查找正確的格式副本。

![影像](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## 將格式副本映射屬性添加到螢幕項目 {#rendition-mapping-new}

要啟用「自適應格式副本」功能，應存在以下映射規則，並且「上下文感知」(CA)配置應可用於通道和顯示。

>[!NOTE]
>要瞭解有關內容感知配置的詳細資訊，請參見 [這裡](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)。

按照以下步驟配置設定：

1. 導航到 **CRXDE Lite**。 如果 **格式副本映射** 配置存在 `/conf/screens/sling:configs/rendition-mapping`，如下圖所示。

   >![影像](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >如果安裝了最新的功能包202109，您將看到 **格式副本映射** 預填充節點結構 `/conf/screens/sling:configs/rendition-mapping` CRXDE Lite。 請參閱 [功能包202109發行說明](/help/user-guide/release-notes-fp-202109.md) 獲取有關最新功能包的詳細資訊。
   >對於現有項目，確保螢幕項目具有 **格式副本映射** 關聯的配置。 請參閱 [將格式副本映射添加到現有項目](#rendition-mapping-existing) 的子菜單。

### 將格式副本映射屬性添加到現有項目 {#rendition-mapping-existing}

1. 導航到 **CRXDE Lite**。

1. 通過添加顯式定義格式副本映射關聯 `sling:configRef` 指向屬性 `/conf/screens` 到項目內容節點，如下圖所示。

   ![影像](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## 添加格式副本映射規則 {#add-rendition-mapping-rules}

按照以下步驟在「格式副本映射」下添加節點：

1. 導航到此路徑 `/conf/screens/sling:configs/rendition-mapping` 從 **CRXDE Lite**。

1. 在下面建立節點 **格式副本映射**。 按一下右鍵 **格式副本映射** 按一下 **建立** —> **建立節點**，如下圖所示。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. 輸入 **名稱** 映射規則(如 **規則1** 和節點 **類型** 如 **nt：非結構化** 在 **建立節點** 對話框。 按一下 **確定**。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. 需要添加包含查詢表達式的值的表達式屬性。

   >[!NOTE]
   >請參閱 [使用媒體查詢語法](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) 來瞭解更多資訊。

   按一下 **規則1** 建立的，並輸入 **表達** 在 **名稱** 和 **（方向：橫向）** 在 **值**，如下所示。 按一下 **添加**。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. 添加帶有包含格式副本命名模式的值的pattern屬性。

   >[!NOTE]
   >模式屬性中定義的值將與新資產格式副本匹配，如果表達式的計算結果為true，則將選中該值。

   要添加pattern屬性，請按一下 **規則1** 建立的，並輸入 **圖案** 在 **名稱** 和 **景觀** 在 **值**，如下所示。 按一下 **添加**。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. 按一下 **全部保存** 您將看到在下面建立的節點下的屬性 **格式副本映射**。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node5.png)


## 後續步驟 {#next-steps}

添加格式副本映射屬性和規則後，您就可以將資產配置為使用「自適應格式副本」，還可以在AEM Screens頻道中為大型網路遷移設備以利用此功能。 請參閱 [在AEM Screens使用自適應格式副本](/help/user-guide/using-adaptive-renditions.md) 的子菜單。

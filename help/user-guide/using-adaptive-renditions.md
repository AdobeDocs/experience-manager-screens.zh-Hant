---
title: 在AEM Screens中使用最適化轉譯
description: 瞭解如何在AEM Screens中使用最適化轉譯。
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# 在AEM Screens中使用最適化轉譯 {#adaptive-renditions}

## 簡介 {#introduction}

最適化轉譯可讓裝置根據客戶定義的規則，自動針對裝置按一下最佳轉譯。 裝置會根據這些規則，自動下載並播放最適當的資產轉譯。 它可讓客戶專注於設計&#x200B;*主要*&#x200B;體驗。

## 目標 {#objective}

作為AEM Scrßens內容作者，您現在可以設定要自動下載和播放的特定於裝置的資產轉譯，而不必手動建立所有內容變化。
開發人員新增轉譯對應屬性和規則後，您就可以將轉譯對應套用至資產，然後將其納入AEM Screens管道了。

>[!IMPORTANT]
>開始在AEM Screens頻道中使用最適化轉譯之前，Adobe建議您瞭解此功能的架構概觀和設定。 請參閱[最適化轉譯：架構概觀與設定](/help/user-guide/adaptive-renditions.md)。

## 在頻道中使用最適化轉譯 {#using-adaptive-renditions}

>[!NOTE]
>在您將[轉譯對應屬性新增至Screens專案](/help/user-guide/adaptive-renditions.md#rendition-mapping-new)和[轉譯對應規則](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)後，身為內容作者，您現在已準備好將轉譯套用至您的資產。

### 將轉譯套用至Assets {#apply-renditions-assets}

若要將轉譯套用至您要在「導覽Screens」頻道中使用的資產，請執行下列動作。

1. 導覽至AEM執行個體中的&#x200B;**Assets**&#x200B;資料夾。
1. 建立更適合招牌顯示的資產版本，例如`seahorse.jpg`。
1. 選擇轉譯命名模式，例如`landscape`，類似於&#x200B;**CRXDE Lite**&#x200B;中&#x200B;**模式**&#x200B;屬性中所定義的模式。 如需詳細資訊，請參閱[新增轉譯對應規則](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)。
1. 按一下&#x200B;**新增轉譯**&#x200B;以上傳轉譯，如下圖所示。

   ![影像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. 按一下已重新命名之資產檔案。 您新增的轉譯必須包含模式（在步驟3中定義），例如`seahorse-landscape.png`。
1. 新增資產後，請按一下資產，然後按一下動作列中的&#x200B;**管理出版物**&#x200B;以發佈資產。

   ![影像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >請參閱[隨選內容更新](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content)，深入瞭解如何管理出版物，以及如何將內容更新從作者傳送至Publish至裝置。

## 移轉策略 {#migration-strategy}

>[!IMPORTANT]
>對於大型網路，Adobe建議逐步進行移轉，以降低風險。 原因是因為功能可能會引進資訊清單和檔案儲存格式的變更。 將`sling:configRef`新增至整個專案涉及將所有播放器更新至Feature Pack 6.5.9。如果您更新了某些播放器，請僅將`sling:configRef`新增到所有播放器都已更新至Feature Pack 6.5.9的顯示器、位置或頻道資料夾。

下圖說明大型網路的移轉策略：

![影像](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

若要啟用此功能，請至少新增一個對應規則，並確定轉譯對應組態可在顯示和色版的內容中解析。 請依照下列步驟進行移轉：

1. 新增[轉譯對應規則](/help/user-guide/adaptive-renditions.md)。
1. 為新頻道建立資料夾，並新增指向轉譯對應設定的參考。
1. 建立管道來取代舊管道並上傳轉譯。
1. 重新指定顯示給新管道。
1. 新增對移轉顯示或指向轉譯對應設定的位置的參考。
1. 針對所有其餘的色版和顯示器，重複步驟3、4和5。

   >[!NOTE]
   >完成移轉後，請務必移除頻道、顯示區和位置中的所有設定參照，並將單一設定參照新增至專案內容節點。

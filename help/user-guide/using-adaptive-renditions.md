---
title: 在AEM Screens中使用最適化轉譯
description: 本頁說明如何在AEM Screens中使用最適化轉譯。
source-git-commit: 6d9dab9fd59289aafdb688682fea47589d3ec873
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---


# 在AEM Screens中使用最適化轉譯 {#adaptive-renditions}

## 簡介 {#introduction}

適用性轉譯可讓裝置根據客戶定義的規則，自動為裝置選取最佳轉譯。 這些裝置會根據這些規則自動下載並播放資產的最適當轉譯，讓客戶只能專注於設計&#x200B;*main*&#x200B;體驗。

## 目標 {#objective}

身為AEM Screens內容作者，您現在可以設定要下載和自動播放的裝置專屬資產轉譯，而不需要手動建立所有內容變異。
開發人員新增轉譯對應屬性和規則後，您現在就可以將轉譯對應套用至資產，並隨後將其納入AEM Screens管道。

>[!IMPORTANT]
>開始使用適用性轉譯之前，建議您先在AEM Screens頻道中了解此功能的架構概述和設定。 請參閱[適用性轉譯：架構概述和設定](/help/user-guide/adaptive-renditions.md)以取得詳細資訊。

## 在頻道中使用最適化轉譯 {#using-adaptive-renditions}

>[!NOTE]
>將[轉譯對應屬性新增至Screens Project](/help/user-guide/adaptive-renditions.md#rendition-mapping-new)和[轉譯對應規則](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules)後，您就可以將轉譯套用至資產了。

### 將轉譯套用至資產 {#apply-renditions-assets}

請依照下列步驟，將轉譯套用至您要在導覽畫面頻道中使用的資產：

1. 導覽至AEM例項中的&#x200B;**Assets**&#x200B;資料夾。

1. 建立更適合標牌顯示的資產版本，例如`seahorse.jpg`。

1. 選擇格式副本命名模式，例如`landscape`，類似於&#x200B;**CRXDE Lite**&#x200B;中&#x200B;**pattern**&#x200B;屬性中定義的模式。 如需詳細資訊，請參閱[新增轉譯對應規則](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) 。

1. 按一下&#x200B;**Add Rendition**&#x200B;以上傳轉譯，如下圖所示。

   ![影像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. 選取已重新命名的資產檔案。 您要新增的轉譯必須包含模式（在步驟3中定義），例如`seahorse-landscape.png`。

1. 新增資產後，請選取資產，然後按一下動作列中的&#x200B;**管理出版物**&#x200B;以發佈資產。

   ![影像](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >請參閱[隨選內容更新](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content.html?lang=en)以深入了解如何管理發布，以及如何將內容更新從製作傳送至裝置。


## 移轉策略 {#migration-strategy}

>[!IMPORTANT]
>對於大型網路，建議逐步進行遷移以降低風險，因為該功能將對清單和檔案儲存格式進行更改。 將`sling:configRef`新增至整個專案時，會將所有播放器更新至Feature Pack 6.5.9。若您已更新部分播放器，您只需將`sling:configRef`新增至所有播放器更新至Feature Pack 6.5.9的顯示器、位置或頻道資料夾。

下圖描述了大型網路的遷移策略：

![影像](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

若要啟用功能，請新增至少一個對應規則，並確定可在顯示器和通道的內容中解析轉譯對應設定。 請依照下列步驟進行移轉：

1. 新增[轉譯對應規則](/help/user-guide/adaptive-renditions.md)。
1. 為新頻道建立資料夾，並新增指向轉譯對應設定的參考。
1. 建立新管道取代舊管道並上傳轉譯。
1. 將顯示為新通道。
1. 將參考新增至已移轉的顯示器或指向轉譯對應設定的位置。
1. 對所有剩餘通道和顯示重複步驟3、4和5。

   >[!NOTE]
   >完成移轉後，請務必從頻道、顯示器和位置移除所有設定參考，並將單一參考新增至專案內容節點。


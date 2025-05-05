---
title: 最適化轉譯架構概觀和設定
description: 瞭解AEM Screens最適化轉譯之CRXDE Lite的架構概觀和設定。
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 2%

---

# 最適化轉譯：架構概觀和設定 {#adaptive-renditions}

## 簡介 {#introduction}

最適化轉譯可讓裝置根據客戶定義的規則，自動針對裝置按一下最佳轉譯。 裝置會根據這些規則，自動下載並播放最適當的資產轉譯，讓客戶專注於設計&#x200B;*主要*&#x200B;體驗。

## 目標 {#objective}

身為AEM Screens開發人員，您現在可以設定自動下載和播放裝置專屬的資產轉譯，而不需要手動建立所有內容變數。 先設定最適化轉譯，內容作者才能在AEM Screens頻道中使用此功能。

## 架構概述 {#architectural-overview}

最適化轉譯是根據特定命名慣例命名資產的多重轉譯的構想。 播放特定轉譯的決定是透過評估只能在具有預期功能的裝置上解析的媒體查詢運算式而作出。

具有關聯轉譯命名模式的功能會定義轉譯對應規則，例如直向或橫向，如下圖所示。 計算所有可用運算式後，Screens播放器會收集對應至相符規則的命名模式。 在序列播放期間，會透過在轉譯名稱中尋找模式來尋找正確的轉譯。

![影像](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## 將轉譯對應屬性新增至Screens專案 {#rendition-mapping-new}

若要啟用「最適化轉譯」功能，應存在下列對應規則，且上下文感知(CA)設定應為可解析的管道和顯示。

>[!NOTE]
>若要進一步瞭解內容感知設定，請參閱[這裡](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)。

請依照下列步驟進行設定：

1. 瀏覽至&#x200B;**CRXDE Lite**。 檢查&#x200B;**轉譯對應**&#x200B;組態是否存在`/conf/screens/sling:configs/rendition-mapping`中，如下圖所示。

   >![影像](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >如果您已安裝最新的Feature Pack 202109，則會在CRXDE Lite中看到`/conf/screens/sling:configs/rendition-mapping`中預先填入的&#x200B;**轉譯對應**&#x200B;節點結構。 請參閱Feature Pack 202109[&#128279;](/help/user-guide/release-notes-fp-202109.md)的發行說明，以取得最新Feature Pack的詳細資訊。
   >若為現有專案，請確定Screens專案具有相關聯的&#x200B;**轉譯對應**&#x200B;設定。 如需詳細資訊，請參閱[將轉譯對應新增至現有專案](#rendition-mapping-existing)區段。

### 新增轉譯對應屬性至現有專案 {#rendition-mapping-existing}

1. 瀏覽至&#x200B;**CRXDE Lite**。

1. 將指向`/conf/screens`的`sling:configRef`屬性新增至專案內容節點，以明確定義轉譯對映關聯，如下圖所示。

   ![影像](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## 新增轉譯對應規則 {#add-rendition-mapping-rules}

請依照下列步驟，在「轉譯對應」下新增節點：

1. 從&#x200B;**CRXDE Lite**&#x200B;瀏覽至此路徑`/conf/screens/sling:configs/rendition-mapping`。
1. 在&#x200B;**轉譯對應**&#x200B;下建立節點。 用滑鼠右鍵按一下&#x200B;**轉譯對應**，然後按一下&#x200B;**建立** > **建立節點**，如下圖所示。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. 在&#x200B;**建立節點**&#x200B;對話方塊中，輸入對應規則（例如&#x200B;**規則1**）的&#x200B;**名稱**&#x200B;以及節點&#x200B;**型別**&#x200B;為&#x200B;**`nt:unstructured`**。 按一下&#x200B;**「確定」**。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. 使用包含查詢運算式的值來新增運算式屬性。

   >[!NOTE]
   >請參閱[使用媒體查詢語法](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries)以瞭解更多資訊。

   按一下您建立的&#x200B;**規則1**，然後在&#x200B;**名稱**&#x200B;中輸入&#x200B;**運算式**，在&#x200B;**值**&#x200B;中輸入&#x200B;**(orientation：landscape)**，如下所示。 按一下&#x200B;**新增**。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. 使用包含轉譯命名模式的值來新增pattern屬性。

   >[!NOTE]
   >如果運算式的計算結果為true，則在pattern屬性中定義的值會符合新的資產轉譯，並會選取該值。

   若要新增模式屬性，請按一下您建立的&#x200B;**規則1**，然後在&#x200B;**名稱**&#x200B;中輸入&#x200B;**模式**，在&#x200B;**值**&#x200B;中輸入&#x200B;**橫向**，如下所示。 按一下&#x200B;**新增**。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. 按一下「儲存全部」**&#x200B;**，並注意您在&#x200B;**rendition-mapping**&#x200B;下建立的節點下的屬性。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## 後續步驟 {#next-steps}

新增轉譯對應屬性和規則後，身為內容作者，您可以設定資產。 您可以使用最適化轉譯，也可以移轉大型網路的裝置，以便在AEM Screens管道中使用此功能。 如需詳細資訊，請參閱[在AEM Screens中使用最適化轉譯](/help/user-guide/using-adaptive-renditions.md)。

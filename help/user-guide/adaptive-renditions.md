---
title: AEM Screens中的最適化轉譯
description: 本頁說明AEM Screens中適用性轉譯的架構概述和設定。
index: false
source-git-commit: 3ced907f4611ff7499ca4c013c4b25e1315e3726
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 1%

---


# 適用性轉譯：架構概述和設定 {#adaptive-renditions}

## 簡介 {#introduction}

適用性轉譯可讓裝置根據客戶定義的規則，自動為裝置選取最佳轉譯。 這些裝置會根據這些規則自動下載並播放資產的最適當轉譯，讓客戶只能專注於設計&#x200B;*main*&#x200B;體驗。

## 目標 {#objective}

身為AEM Screens開發人員，您現在可以設定要下載和自動播放的裝置專屬資產轉譯，而不需要手動建立所有內容變異。 您必須先設定「最適化轉譯」，內容作者才能在AEM Screens頻道中使用此功能。

## 架構概述 {#architectural-overview}

最適化轉譯是以擁有多個資產轉譯的構想為基礎，並以特定命名慣例命名。 播放特定轉譯的決定是透過評估媒體查詢運算式，而這些運算式只能在具備預期功能的裝置上解析。

具有關聯的格式副本命名模式的功能定義格式副本映射規則，如直向或橫向，如下圖所示。 計算所有可用的運算式後，Screens播放器將收集與相符規則對應的命名模式。 模式可用來在序列播放期間，透過尋找轉譯名稱中的模式來尋找正確的轉譯。

![影像](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## 將轉譯對應屬性新增至Screens專案 {#rendition-mapping-new}

若要啟用「適用性轉譯」功能，應存在下列對應規則，且「內容感知」(CA)設定應可針對通道和顯示進行解析。

>[!NOTE]
>若要深入了解內容感知設定，請參閱[此處](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)。

請依照下列步驟來設定設定：

1. 導覽至&#x200B;**CRXDE Lite**。 檢查&#x200B;**rendition-mapping**&#x200B;配置是否存在於`/conf/screens/sling:configs/rendition-mapping`中，如下圖所示。

   >![影像](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >若您已安裝最新的Feature Pack 202109，您會看到&#x200B;**rendition-mapping**&#x200B;節點結構已預先填入`/conf/screens/sling:configs/rendition-mapping`的CRXDE Lite中。 請參閱[Feature Pack 202109](/help/user-guide/release-notes-fp-202109.md)發行說明，以取得最新Feature Pack的詳細資訊。
   >針對現有專案，請確定Screens專案有相關聯的&#x200B;**rendition-mapping**&#x200B;設定。 請參閱[新增轉譯對應至現有專案](#rendition-mapping-existing)區段以深入了解。

### 將格式副本映射屬性添加到現有項目 {#rendition-mapping-existing}

1. 導覽至&#x200B;**CRXDE Lite**。

1. 將指向`/conf/screens`的`sling:configRef`屬性添加到項目內容節點，顯式定義格式副本映射關聯，如下圖所示。

   ![影像](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## 設定作者和發佈 {#setup-author-publish}

使用最適化轉譯之前，請在「製作」和「發佈」中考量下列建議：

* 必須手動複製轉譯對應。

* 預設不會複製資產轉譯。 所有相關資產都需要手動複製。

## 新增轉譯對應規則 {#add-rendition-mapping-rules}

請依照下列步驟，在「轉譯對應」下新增節點：

1. 從&#x200B;**CRXDE Lite**&#x200B;導覽至此路徑`/conf/screens/sling:configs/rendition-mapping`。

1. 在&#x200B;**rendition-mapping**&#x200B;下建立節點。 按一下右鍵&#x200B;**rendition-mapping**，然後按一下&#x200B;**Create** —> **Create Node**，如下圖所示。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. 在&#x200B;**建立節點**&#x200B;對話框中，為映射規則（如&#x200B;**rule1**）輸入&#x200B;**名稱**，並將節點&#x200B;**類型**&#x200B;輸入為&#x200B;**nt:unstrucled**。 按一下&#x200B;**OK**。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. 您需要以包含查詢運算式的值新增運算式屬性。

   >[!NOTE]
   >請參閱[使用媒體查詢語法](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)以深入了解。

   按一下您建立的&#x200B;**rule1**，然後在&#x200B;**Name**&#x200B;和&#x200B;**(orientation:landscape)**&#x200B;中輸入&#x200B;**expression**，如下所示。 ****&#x200B;按一下&#x200B;**Add**。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. 使用包含轉譯命名模式的值新增模式屬性。

   >[!NOTE]
   >模式屬性中定義的值將與新資產轉譯相符，且如果運算式評估為true，則會選取該值。

   若要新增模式屬性，請按一下您建立的&#x200B;**rule1**，並在&#x200B;**Name**&#x200B;中輸入&#x200B;**pattern**，並在&#x200B;**Value**&#x200B;中輸入&#x200B;**landscape**，如下所示。 按一下&#x200B;**Add**。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. 按一下&#x200B;**Save All**，您將在&#x200B;**rendition-mapping**&#x200B;下建立的節點下看到屬性。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-node5.png)


## 後續步驟 {#next-steps}

設定及上傳轉譯後，您現在可以以「內容作者」的身分使用「最適化轉譯」，也可以移轉大型網路的裝置，以便在AEM Screens頻道中使用此功能。 如需詳細資訊，請參閱[使用最適化轉譯](/help/user-guide/using-adaptive-renditions.md) 。

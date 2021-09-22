---
title: AEM Screens中的最適化轉譯
description: 本頁說明AEM Screens中適用性轉譯的架構概述和設定。
index: false
source-git-commit: fcc7126ac545c80004d718888b39c6477624cd33
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 1%

---


# 適用性轉譯：架構概述和設定 {#adaptive-renditions}

## 簡介 {#introduction}

適用性轉譯可讓裝置根據客戶定義的規則，自動為裝置選取最佳轉譯。 這些裝置會根據這些規則自動下載並播放資產的最適當轉譯，讓客戶只能專注於設計&#x200B;*main*&#x200B;體驗。

## 目標 {#objective}

身為AEM Screens開發人員，您現在可以設定要下載和自動播放的裝置專屬資產轉譯，而不需要手動建立所有內容變異。 您必須先設定最適化轉譯，內容作者才能在AEM Screens頻道中使用此功能。

因此，如果您部署了各種裝置，使用此功能可讓裝置根據規則自動下載並播放資產的最適當轉譯。

## 架構概述 {#architectural-overview}

最適化轉譯是以擁有多個資產轉譯的構想為基礎，並以特定命名慣例命名。 播放特定轉譯的決定是透過評估媒體查詢運算式，而這些運算式只能在具備預期功能的裝置上解析。 具有關聯的格式副本命名模式的能力定義格式副本映射規則。 計算所有可用的運算式後，Screens播放器將收集與相符規則對應的命名模式。 模式可用來在序列播放期間，透過尋找轉譯名稱中的模式來尋找正確的轉譯。

![影像](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## 使用最適化轉譯設定 {#setup-adaptive-renditions}

若要啟用「適用性轉譯」功能，應該有對應規則，且「內容感知組態」可針對通道和顯示進行解析：

1. 檢查`JCR`中是否存在格式副本映射配置。 所有最新的Feature Pack都已預先填入此節點結構。

   >[!NOTE]
   >所有最新的Feature Pack都已預先填入此節點結構。

   ![影像](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

1. 請確定Screens專案具有與其相關聯的轉譯對應設定。

   * 使用Screens專案精靈建立的每個新專案都會包含指向轉譯對應設定的參考。

      ![影像](/help/user-guide/assets/adaptive-renditions/mapping-rules2.png)

   * 在舊版Screens專案中，必須將指向`/conf/screens`的`sling:configRef`屬性新增至專案內容節點，以明確定義關聯。

      ![影像](/help/user-guide/assets/adaptive-renditions/mapping-rules3.png)



## 設定作者和發佈 {#setup-author-publish}

使用最適化轉譯之前，請在「製作」和「發佈」中考量下列建議：

* 必須手動複製轉譯對應。

* 預設不會複製資產轉譯。 所有相關資產都需要手動複製。

## 新增轉譯對應規則 {#add-rendition-mapping-rules}

1. 要添加映射規則，需要在格式副本映射節點下建立`nt:unstructured`類型的節點。

1. 使用包含查詢運算式的值新增運算式屬性。

   >[!NOTE]
   >請參閱[使用媒體查詢語法](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)以深入了解。

1. 如果將運算式評估為true，請使用包含將選取的轉譯命名模式的值來新增模式屬性。

   ![影像](/help/user-guide/assets/adaptive-renditions/mapping-rules4.png)



## 後續步驟 {#next-steps}

設定及上傳轉譯後，您現在可以在AEM Screens頻道中使用最適化轉譯。 如需詳細資訊，請參閱使用最適化轉譯。

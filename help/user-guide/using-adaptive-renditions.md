---
title: 在AEM Screens中使用最適化轉譯
description: 本頁說明如何在AEM Screens中使用最適化轉譯。
index: false
source-git-commit: 08f47e6542a7832f64d5d0dde9cdd463176f5f5d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 1%

---

# 使用最適化轉譯 {#adaptive-renditions}

## 簡介 {#introduction}

適用性轉譯可讓裝置根據客戶定義的規則，自動為裝置選取最佳轉譯。 這些裝置會根據這些規則自動下載並播放資產的最適當轉譯，讓客戶只能專注於設計&#x200B;*main*&#x200B;體驗。

## 目標 {#objective}

身為AEM Screens內容作者，您現在可以設定要下載和自動播放的裝置專屬資產轉譯，而不需要手動建立所有內容變異。

因此，如果您部署了各種裝置，使用此功能可讓裝置根據規則自動下載並播放資產的最適當轉譯。

>[!IMPORTANT]
>開始使用適用性轉譯之前，建議您先在AEM Screens頻道中了解此功能的架構概述和設定。 請參閱適用性轉譯：架構概述和設定，以取得詳細資訊。

## 移轉策略 {#migration-strategy}

>[!IMPORTANT]
>對於大型網路，建議逐步進行遷移以降低風險，因為該功能將對清單和檔案儲存格式進行更改。

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


## 在AEM Screens頻道中上傳轉譯和使用最適化轉譯 {#upload-renditions}

1. 建立更適合標牌顯示的資產版本，例如`portrait orientation`。

1. 選擇格式副本命名模式，例如`portrait`。

1. 重新命名資產檔案，使其包含模式，例如`my_asset_portrait.png`。

1. 按一下&#x200B;**Add Rendition**&#x200B;以上傳轉譯，如下圖所示。

   ![影像](/help/user-guide/assets/adaptive-renditions/add-rendition.png)
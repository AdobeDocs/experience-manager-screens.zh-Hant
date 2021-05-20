---
title: 離線頻道
seo-title: 離線頻道
description: 'AEM Screens播放器運用ContentSync技術，提供頻道的離線支援。 請依照本頁面了解更多更新處理常式，以及啟用通道的離線設定。  '
seo-description: 'AEM Screens播放器運用ContentSync技術，提供頻道的離線支援。 請依照本頁面了解更多更新處理常式，以及啟用通道的離線設定。  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
feature: 開發螢幕
role: Developer
level: Intermediate
exl-id: 5ad1046f-8b64-490b-9966-ce9008180d54
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 1%

---

# 離線頻道{#offline-channels}

Screens播放器運用&#x200B;***ContentSync***&#x200B;技術，為頻道提供離線支援。

播放器使用本機http伺服器來提供未壓縮的內容。

當通道被配置為運行&#x200B;*online*&#x200B;時，播放器通過訪問AEM伺服器來提供通道資源，但當通道被配置為運行&#x200B;*offline*&#x200B;時，播放器從本地http伺服器提供通道資源。

此程式的工作流程如下：

1. 剖析所需頁面
1. 收集所有相關資產
1. 將所有內容封裝在zip檔案中
1. 下載zip並將其解壓縮到本機
1. 顯示內容的本機副本

## 更新處理程式{#update-handlers}

***ContentSync***&#x200B;使用更新處理常式來剖析和收集特定專案的所有必要頁面和資產。 AEM Screens使用下列更新處理常式：

### 常用選項{#common-options}

* *類型*:要使用的更新處理程式類型
* *路徑*:資源路徑
* *[targetRootDirectory]*:zip檔案中的target資料夾

<table>
 <tbody>
  <tr>
   <td><strong>類型</strong></td> 
   <td><strong>說明</strong></td> 
   <td><strong>選項</strong></td> 
  </tr>
  <tr>
   <td>頻道</td> 
   <td>收集管道</td> 
   <td>擴充功能：收集<br /> [pathSuffix="]的資源擴展：要添加到通道路徑的尾碼<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>收集指定的客戶端庫</td> 
   <td>[extension="]:可以是css或js，僅收集前者，或僅收集後者</td> 
  </tr>
  <tr>
   <td>assetrenditions</td> 
   <td>收集資產轉譯</td> 
   <td>[renditions=[]]:要收集的轉譯清單。 預設為原始格式副本</td> 
  </tr>
  <tr>
   <td>複製</td> 
   <td>從路徑複製指定的結構</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### 測試ContentSync配置{#testing-contentsync-configuration}

請依照下列步驟測試ContentSync配置：

1. 開啟 `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. 在清單中選取您的設定
1. 按一下清除快取
1. 按一下更新快取
1. 按一下「Download Full（下載完整）」
1. 解壓縮zip檔案
1. 在擷取的資料夾中啟動本機伺服器
1. 開啟您的開始頁面並檢查您的應用程式狀態

## 為通道{#enabling-offline-config-for-a-channel}啟用離線配置

請依照下列步驟，啟用管道的離線設定：

1. Inspect頻道內容，並檢查是否從AEM例項（線上）要求它。

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. 導覽至通道控制面板，然後按一下&#x200B;**..**&#x200B;通道資訊&#x200B;**面板中的**&#x200B;以更改屬性。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 導覽至通道屬性，並確認&#x200B;**Channel**&#x200B;標籤下的核取方塊已停用。 按一下&#x200B;**「儲存並關閉」**。

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   在將內容正確部署到設備之前，按一下&#x200B;**更新離線內容**。

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   **PROPERTIES**&#x200B;下的&#x200B;**離線**&#x200B;狀態也會相應更新。

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspect頻道內容，並檢查是否從本機播放器快取要求它。

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>要詳細了解自定義離線資源處理程式的模板以及該特定項目的`pom.xml`中的最低要求，請參閱&#x200B;**開發AEM Screens的自定義元件**&#x200B;中的[自定義處理程式的模板](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers)。

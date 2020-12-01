---
title: 離線渠道
seo-title: 離線渠道
description: 'AEM Screens播放器運用ContentSync技術，提供頻道的離線支援。 請依照本頁進一步瞭解更新處理常式，以及啟用頻道的離線設定。  '
seo-description: 'AEM Screens播放器運用ContentSync技術，提供頻道的離線支援。 請依照本頁進一步瞭解更新處理常式，以及啟用頻道的離線設定。  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 1%

---


# 離線頻道{#offline-channels}

Screens播放器運用&#x200B;***ContentSync***&#x200B;技術，提供頻道的離線支援。

播放器使用本機http伺服器來提供解壓縮的內容。

當頻道設定為執行&#x200B;*online*&#x200B;時，播放器會存取AEM伺服器以提供頻道資源，但當頻道設定為執行&#x200B;*offline*&#x200B;時，播放器會從本機http伺服器提供頻道資源。

流程的工作流如下：

1. 剖析所要的頁面
1. 收集所有相關資產
1. 將所有內容封裝在zip檔案中
1. 下載zip並解壓縮至本機
1. 顯示內容的本機副本

## 更新處理程式{#update-handlers}

***ContentSync***&#x200B;使用更新處理常式來剖析和收集特定專案的所有必要頁面和資產。 AEM Screens使用下列更新處理常式：

### 常用選項{#common-options}

* *類型*:要使用的更新處理常式類型
* *路徑*:資源路徑
* *[targetRootDirectory]*:zip檔案中的目標檔案夾

<table>
 <tbody>
  <tr>
   <td><strong>類型</strong></td> 
   <td><strong>說明</strong></td> 
   <td><strong>選項</strong></td> 
  </tr>
  <tr>
   <td>頻道</td> 
   <td>收集渠道</td> 
   <td>擴充功能：資源的擴展，以收集<br /> [pathSuffix="]:要添加到頻道路徑的尾碼<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>收集指定的用戶端程式庫</td> 
   <td>[extension="]:可以是css或js，只收集前者，或僅收集後者</td> 
  </tr>
  <tr>
   <td>assetrenditions</td> 
   <td>收集資產轉譯</td> 
   <td>[轉譯=[]:要收集的轉譯清單。 預設為原始轉譯</td> 
  </tr>
  <tr>
   <td>複製</td> 
   <td>從路徑複製指定的結構</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### 測試ContentSync配置{#testing-contentsync-configuration}

請依照下列步驟測試ContentSync設定：

1. 開啟 `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. 在清單中選取您的設定
1. 按一下清除快取
1. 按一下「更新快取」
1. 按一下「下載完整版」
1. 解壓縮zip檔案
1. 在解壓縮的資料夾中啟動本地伺服器
1. 開啟您的開始頁面並檢查您的應用程式狀態

## 為渠道{#enabling-offline-config-for-a-channel}啟用離線配置

請依照下列步驟，為頻道啟用離線設定：

1. 檢查頻道內容，並檢查是否從AEM例項（線上）提出要求。

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. 導覽至頻道控制面板，然後按一下&#x200B;**...** CHANNEL INFORMATION **面板中的**&#x200B;以變更屬性。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 導覽至頻道屬性，並確保在&#x200B;**頻道**&#x200B;標籤下停用核取方塊。 按一下&#x200B;**「儲存並關閉」**。

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   在將內容正確部署至裝置之前，請按一下「更新離線內容」。****

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   **PROPERTIES**&#x200B;下的&#x200B;**Offline**&#x200B;狀態也會隨之更新。

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. 檢查頻道內容，並檢查是否從本機播放器快取要求它。

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>若要進一步瞭解自訂離線資源處理常式的範本，以及該特定專案的`pom.xml`最低需求，請參閱&#x200B;**開發AEM Screens**&#x200B;中的[自訂處理常式範本](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers)。
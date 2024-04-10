---
title: 離線頻道
seo-title: Offline Channels
description: AEM Screens播放器運用ContentSync技術，提供管道的離線支援。 請依照本頁瞭解更多有關更新處理常式及啟用管道離線設定的資訊。
seo-description: The AEM Screens player provides offline support for channels by leveraging the ContentSync technology. Follow this page to learn more about update handlers and enabling offline configuration for a channel.
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 5ad1046f-8b64-490b-9966-ce9008180d54
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 2%

---

# 離線頻道 {#offline-channels}

Screens播放器會利用 ***ContentSync*** 技術。

播放器會使用本機http伺服器來提供解壓縮的內容。

當通道設定為執行時 *線上*，播放器會存取AEM伺服器來提供管道資源，但若將管道設定為執行 *離線*，播放器會從本機http伺服器提供管道資源。

處理的工作流程如下：

1. 剖析所需頁面
1. 收集所有相關資產
1. 將所有內容封裝在zip檔案中
1. 下載壓縮檔並在本機解壓縮
1. 顯示內容的本機復本

## 更新處理常式 {#update-handlers}

此 ***ContentSync*** 使用更新處理常式，剖析及收集特定專案的所有必要頁面和資產。 AEM Screens會使用以下更新處理常式：

### 常用選項 {#common-options}

* *type*：要使用的更新處理常式型別
* *路徑*：資源的路徑
* *[targetRootDirectory]*：zip檔案中的目標資料夾

<table>
 <tbody>
  <tr>
   <td><strong>類型</strong></td> 
   <td><strong>說明</strong></td> 
   <td><strong>選項</strong></td> 
  </tr>
  <tr>
   <td>管道</td> 
   <td>收集頻道</td> 
   <td>擴充功能：要收集的資源的擴充功能<br /> [pathSuffix="]：要新增至管道路徑的尾碼<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>收集指定的使用者端程式庫</td> 
   <td>[extension="]：可以是css或js，以僅收集前者，或僅收集後者</td> 
  </tr>
  <tr>
   <td>assetrendations</td> 
   <td>收集資產轉譯</td> 
   <td>[renditions=[]]：要收集的轉譯清單。 預設為原始轉譯</td> 
  </tr>
  <tr>
   <td>複製</td> 
   <td>從路徑複製指定的結構</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### 測試ContentSync設定 {#testing-contentsync-configuration}

請依照下列步驟測試ContentSync設定：

1. 開啟 `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. 在清單中選取您的設定
1. 按一下清除快取
1. 按一下更新快取
1. 按一下「下載完整部分」
1. 解壓縮zip檔案
1. 在擷取的資料夾中啟動本機伺服器
1. 開啟您的開始頁面並檢查您的應用程式狀態

## 啟用頻道的離線設定 {#enabling-offline-config-for-a-channel}

請依照下列步驟，啟用頻道的離線設定：

1. Inspect頻道內容，並檢查是否從AEM例項（線上）請求。

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. 導覽至頻道控制面板，然後按一下 **...** 在 **頻道資訊** 面板以變更屬性。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 導覽至管道屬性，並確認下方的核取方塊為停用狀態。 **頻道** 標籤。 按一下&#x200B;**「儲存並關閉」**。

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   在將內容正確部署到裝置之前，請按一下 **更新離線內容**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   此 **離線** 狀態在 **屬性** 也會據此進行更新。

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspect頻道內容，並檢查是否從本機播放器快取要求。

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>若要進一步瞭解自訂離線資源處理常式的範本，以及中的最低需求 `pom.xml` 有關特定專案，請參閱 [自訂處理常式的範本](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) 在 **為AEM Screens開發自訂元件**.

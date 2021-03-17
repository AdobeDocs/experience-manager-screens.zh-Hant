---
title: Adobe Analytics與AEM Screens整合
seo-title: Adobe Analytics與AEM Screens整合
description: 請依本頁瞭解AEM Screens與Adobe Analytics的現成整合，並提供您播放證明。
seo-description: 請依本頁瞭解AEM Screens與Adobe Analytics的現成整合，並提供您播放證明。
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
translation-type: tm+mt
source-git-commit: 052ceaf3f3fa321ea0df3e40ecf6296222db71e7
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 0%

---


# Adobe Analytics與AEM Screens整合{#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>只有在您安裝了最低版本的6.AEM4.2 Feature Pack 2或AEM6.3.3 Feature Pack 4時，才能使用本AEM Screens功能。

>[!NOTE]
>
>若要存取其中一個功能套件，您必須聯絡Adobe支援並要求存取權。 一旦您擁有權限，就可從「套件共用」下載。

本節涵蓋下列主題：

* **概覽**
* **架構細節**
* **配置屬性**

## 概覽 {#overview}

***ScreensAEM運用了Adobe Analytics，因此您可以取得市場上獨一無二的成果——跨通道分析，協助將位置顯示的內容與其他資料來源建立關聯。*** 

AEM Screens提供與Adobe Analytics的現成可用整合，並提供您遊戲的證明。

本節介紹將AEM Screens項目與Adobe Analytics連接時涉及的以下功能：

* 允許依裝置提供播放報告證明
* 允許依資產提供播放證明報告
* 確保所有播放器事件都已擷取並加上時間戳記
* 如果播放未連線至網路，請確保所有播放器事件都儲存在本機
* 可建立回饋回圈，以追蹤隨時間變化的播放事件
* 允許系統根據內容作者定義的成功准則修改內容和版面

Adobe Analytics與AEM Screens的整合因此執行了以下&#x200B;*目標*:

* 實現數位標牌實作的投資報酬率
* 將Analytics整合為基礎，以便日後能夠收集和分析使用資訊

## 體系結構詳細資訊{#architectural-details}

AEM Screens客戶希望瞭解何時顯示哪些內容，以及顯示的時間（匯總）。 這是標牌解決方案的常用功能。 AEM Screens不會建立自己的分析，而是利用Adobe Analytics，因此我們可以取得市場上獨一無二的成果——跨通道分析，協助將位置顯示的內容與其他資料來源建立關聯。

以下架構圖說明Adobe Analytics與AEM Screens的整合：

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## 在AEM Screens啟用Adobe Analytics{#enabling-adobe-analytics-in-aem-screens}

可從OSGi控制台配置Adobe Analytics設定。

導覽至&#x200B;**Adobe Experience ManagerWeb控制台配置**&#x200B;以配置AEM Screens的Adobe Analytics，如下圖所示：

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## 螢幕分析：啟用流程{#screens-analytics-enablement-flow}

>[!CAUTION]
>
>在設定屬性之前，請連絡您的Adobe關係管理員以建立票證，以取得&#x200B;**Analytics API金鑰**&#x200B;和&#x200B;**Analytics專案**，以便與AEM Screens搭配使用。

![]()

### 配置屬性{#configuring-the-properties}

>[!CAUTION]
>
>在設定屬性之前，請連絡您的Adobe關係管理員以建立票證，以取得&#x200B;**Analytics API金鑰**&#x200B;和&#x200B;**Analytics專案**，以便與AEM Screens搭配使用。

下表重點說明了為AEM Screens配置Adobe Analytics的屬性及其說明：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><strong>Analytics URL</strong></td>
   <td>從播放器張貼分析資料的URL。 <br>
   針對開發／階段</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em> For Production</em> - https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Analytics API金鑰</strong></td>
   <td>API金鑰，以驗證至Adobe Analytics伺服器（由帳戶管理員提供）。</td>
  </tr>
  <tr>
   <td><strong>Analytics專案</strong></td>
   <td>AEM Screens專案已在您的分析上設定，以接收資料（由帳戶管理員提供）。</td>
  </tr>
  <tr>
   <td><strong>環境</strong></td>
   <td><p>舞台或生產環境（選擇舞台或生產）。</p></td>
  </tr>
  <tr>
   <td><strong>Analytics傳送頻率</strong></td>
   <td>從播放器傳送分析資料的頻率（以分鐘為單位）。 預設為15分鐘。</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>依預設，**Analytics傳送頻率**&#x200B;為15分鐘。

#### 在AEM Screens使用Adobe Analytics服務{#using-adobe-analytics-service-in-aem-screens}

此案例會透過來自韌體和儀器畫面核心元件中分析服務的REST呼叫來叫用Analytics API，以明確建立和傳送特定使用案例的事件，同時允許擴充性，讓任何自訂訊息都可從自訂開發的頻道傳送至Analytics。

Analytics事件會離線儲存在indexedDB中，稍後會將其分塊並傳送至雲端。

>[!NOTE]
>
>要進一步瞭解&#x200B;***Sequencing***&#x200B;和&#x200B;***事件標準資料模型***，請參閱&#x200B;**[為AEM Screens配置Adobe Analytics](configuring-adobe-analytics-aem-screens.md)**。


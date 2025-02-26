---
title: Adobe Analytics與AEM Screens整合
description: 瞭解AEM Screens與Adobe Analytics立即可用的整合，並為您提供播放證明。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 92c8c42b-7c1e-4d4a-8662-18c99666e9c6
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# Adobe Analytics與AEM Screens整合 {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>只有您已安裝AEM 6.4.2 Feature Pack 2或AEM 6.3.3 Feature Pack 4的最低版本，才能使用此AEM Screens功能。 若為AEM Screens Cloud Service客戶，請聯絡您的Adobe關係管理員，以在Screens Cloud中啟用Adobe Analytics。

>[!NOTE]
>
>若要存取其中任一個Feature Pack，請聯絡Adobe支援並要求存取權。 您可以使用您的Adobe ID，從[軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載AEM Screens的最新Feature Pack。

本節涵蓋下列主題：

* **概觀**
* **架構詳細資料**
* **設定屬性**

## 概觀 {#overview}

***AEM Screens***&#x200B;使用Adobe Analytics，您可以透過它達成市場上獨一無二的功能 — 跨管道分析，協助將位置中顯示的內容與其他資料來源建立關聯。

AEM Screens提供與Adobe Analytics的現成整合，並為您提供播放證明。

本節說明以下與Adobe Analytics連線AEM Screens專案相關的功能：

* 允許依裝置提供播放報表的證明
* 允許依資產播放報告的證明
* 確保擷取所有播放器事件並加上時間戳記
* 如果播放未連線至網路，請確定所有播放器事件都儲存在本機
* 可以建立回饋迴路，以追蹤一段時間內的播放事件
* 可讓系統根據內容作者定義的成功標準編輯內容和版面

Adobe Analytics與AEM Screens的整合因此會強制下列&#x200B;*目標*：

* 實現數位招牌實作的投資報酬率
* 整合Analytics，作為日後啟用收集和分析使用資訊的基礎

## 架構詳細資料 {#architectural-details}

AEM Screens客戶想要瞭解內容在何時顯示，以及顯示時間（彙總）。 此必要性是招牌解決方案的常見功能。 AEM Screens使用Adobe Analytics，而非建立個別的分析應用程式。 此組合可讓我們達成市場上獨一無二的目標 — 跨管道分析，協助將位置中顯示的內容與其他資料來源建立關聯。

下列架構圖表說明Adobe Analytics與AEM Screens的整合：

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## 在AEM Screens中啟用Adobe Analytics {#enabling-adobe-analytics-in-aem-screens}

Adobe Analytics設定可從OSGi主控台進行設定。

導覽至&#x200B;**Adobe Experience Manager Web主控台組態**，以便為AEM Screens設定Adobe Analytics。

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Screens Analytics：啟用流程 {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>設定屬性之前，請連絡您的Adobe關係管理員以建立票證，取得&#x200B;**Analytics API金鑰**&#x200B;和&#x200B;**Analytics專案**&#x200B;以搭配AEM Screens使用。

### 設定屬性 {#configuring-the-properties}

>[!CAUTION]
>
>設定屬性之前，請連絡您的Adobe關係管理員以建立票證，取得&#x200B;**Analytics API金鑰**&#x200B;和&#x200B;**Analytics專案**&#x200B;以搭配AEM Screens使用。

下錶針對為AEM Screens設定Adobe Analytics的屬性及其說明提供重點說明：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><strong>Analytics URL</strong></td>
   <td>從播放器發佈分析資料的URL。 <br>
   用於開發/階段</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>用於生產</em> - https://cc-api-data.adobe.io/ingest/<br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Analytics API金鑰</strong></td>
   <td>用於向Adobe Analytics伺服器驗證的API金鑰（由帳戶管理員提供）。</td>
  </tr>
  <tr>
   <td><strong>分析專案</strong></td>
   <td>在您的Analytics上設定的AEM Screens專案，用於接收資料（由帳戶管理員提供）。</td>
  </tr>
  <tr>
   <td><strong>環境</strong></td>
   <td><p>中繼或生產環境（選擇中繼或生產）。</p></td>
  </tr>
  <tr>
   <td><strong>Analytics傳送頻率</strong></td>
   <td>從播放器傳送分析資料的頻率（分鐘）。 預設為15分鐘。</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>依預設，**Analytics傳送頻率**&#x200B;為15分鐘。

#### 在AEM Screens中使用Adobe Analytics服務 {#using-adobe-analytics-service-in-aem-screens}

此情境會透過韌體中Analytics服務的REST呼叫叫用Analytics API。 它也會檢測AEM Screens核心元件，以建立和傳送特定使用案例的特定事件。 具備上述所有功能，且可擴充，讓任何自訂訊息可從自訂開發的頻道傳送至Analytics。

Analytics事件會離線儲存在indexedDB中，並在稍後加入區塊並傳送至雲端。

>[!NOTE]
>
>若要進一步瞭解&#x200B;***排序***&#x200B;和事件&#x200B;***的***&#x200B;標準資料模型，請參閱&#x200B;**[為AEM Screens設定Adobe Analytics](configuring-adobe-analytics-aem-screens.md)**。

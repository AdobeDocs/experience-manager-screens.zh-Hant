---
title: Adobe Analytics融入AEM Screens
seo-title: Adobe Analytics Integration with AEM Screens
description: 請按照本頁瞭解AEM Screens與Adobe Analytics的開箱整合，並為您提供一個播放證明。
seo-description: Follow this page to learn about out of the box integration of AEM Screens with Adobe Analytics and provides you with a proof of play.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 92c8c42b-7c1e-4d4a-8662-18c99666e9c6
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 1%

---

# Adobe Analytics融入AEM Screens {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>只有安裝了最低版本的AEM6.4.2功能包2或AEM6.3.3功能包4，此AEM Screens功能才可用。

>[!NOTE]
>
>要訪問這些功能包中的任何一個，必須聯繫Adobe支援並請求訪問。 您可以從以下網站下載AEM Screens的最新功能包： [軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 用你的Adobe ID。

本節介紹以下主題：

* **概觀**
* **體系結構詳細資訊**
* **配置屬性**

## 概觀 {#overview}

***AEM Screens*** 利用Adobe Analytics，並借助它，您可以實現市場上的獨特功能 — 跨渠道分析，幫助將位置顯示的內容與其他資料源關聯起來。

AEM Screens提供了與Adobe Analytics的開箱整合，並為您提供了遊戲的證明。

本節介紹將AEM Screens項目與Adobe Analytics連接時涉及的以下功能：

* 允許按設備進行播放報告的驗證
* 允許按資產進行播放報告的證明
* 確保捕獲所有玩家事件並加上時間戳
* 確保在播放未連接到網路時所有播放器事件都儲存在本地
* 允許建立反饋循環，以跟蹤隨時間推移的播放事件
* 允許系統根據內容作者定義的成功標準修改內容和佈局

Adobe Analytics與AEM Screens的融合因此執行了以下 *目標*:

* 通過數字標牌實施實現ROI
* 將Analytics作為基礎，以便將來能夠收集和分析使用資訊

## 體系結構詳細資訊 {#architectural-details}

AEM Screens的客戶希望瞭解何時顯示的內容以及顯示時間（聚合）。 這是標牌解決方案的通用功能。 AEM Screens不會構建自己的分析，而是利用Adobe Analytics，從而我們可以實現市場上獨一無二的東西 — 跨渠道分析，幫助將位置顯示的內容與其他資料源關聯起來。

下面的體系結構圖說明了Adobe Analytics與AEM Screens的整合：

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## 使Adobe Analytics在AEM Screens {#enabling-adobe-analytics-in-aem-screens}

可以從OSGi控制台配置Adobe Analytics設定。

導航到 **Adobe Experience ManagerWeb控制台配置** 為AEM Screens配置Adobe Analytics，如下圖所示：

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## 螢幕分析：啟用流程 {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>在配置屬性之前，請與Adobe關係管理器聯繫以建立票證以獲取 **分析API密鑰** 和 **分析項目** 用在AEM Screens。

![]()

### 配置屬性 {#configuring-the-properties}

>[!CAUTION]
>
>在配置屬性之前，請與Adobe關係管理器聯繫以建立票證以獲取 **分析API密鑰** 和 **分析項目** 用在AEM Screens。

下表重點介紹了為AEM Screens配置Adobe Analytics的屬性及其說明：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><strong>分析URL</strong></td>
   <td>從播放器發佈分析資料的URL。 <br>
   用於發展/階段</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>用於生產</em> - https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong>分析API密鑰</strong></td>
   <td>用於驗證到Adobe Analytics伺服器（由帳戶管理器提供）的API密鑰。</td>
  </tr>
  <tr>
   <td><strong>分析項目</strong></td>
   <td>AEM Screens項目在分析上配置以接收資料（由客戶經理提供）。</td>
  </tr>
  <tr>
   <td><strong>環境</strong></td>
   <td><p>階段或生產環境（選擇階段或生產）。</p></td>
  </tr>
  <tr>
   <td><strong>分析發送頻率</strong></td>
   <td>從玩家發送分析資料的頻率（以分鐘為單位）。 預設情況下，它設定為15分鐘。</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>預設情況下， **分析發送頻率** 15分鐘。

#### 在AEM Screens使用Adobe Analytics服務 {#using-adobe-analytics-service-in-aem-screens}

此方案通過韌體和儀器螢幕核心元件中的分析服務的REST調用調用分析API，以顯式建立和發送特定用例的事件，同時允許擴展性，在可擴充性中，任何自定義消息都可以從自定義開發的通道發送到分析。

分析事件離線儲存在indexedDB中，稍後分組併發送到雲。

>[!NOTE]
>
>瞭解有關 ***測序*** 和 ***事件的標準資料模型***，請參閱 **[為Adobe Analytics配置AEM Screens](configuring-adobe-analytics-aem-screens.md)**。

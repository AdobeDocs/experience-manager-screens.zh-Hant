---
title: Adobe Analytics與AEM Screens整合
seo-title: Adobe Analytics與AEM Screens整合
description: 請依照本頁面了解AEM Screens與Adobe Analytics的現成整合，並提供播放證明。
seo-description: 請依照本頁面了解AEM Screens與Adobe Analytics的現成整合，並提供播放證明。
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
feature: 管理畫面
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%

---


# Adobe Analytics與AEM Screens的整合{#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>只有在您已安裝最低版本的AEM 6.4.2 Feature Pack 2或AEM 6.3.3 Feature Pack 4時，才能使用此AEM Screens功能。

>[!NOTE]
>
>若要存取其中一個Feature Pack，您必須聯絡Adobe支援並要求存取權。 您可以使用Adobe ID，從[Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載AEM Screens的最新Feature Pack。

本節涵蓋下列主題：

* **概覽**
* **架構詳細資訊**
* **設定屬性**

## 概覽 {#overview}

***AEM*** Screens可運用Adobe Analytics，並透過它，您可取得市場上獨一無二的成果 — 跨管道分析，有助於將顯示於位置的內容與其他資料來源產生關聯。

AEM Screens提供與Adobe Analytics的立即可用整合，並提供您播放的證明。

本節說明連結AEM Screens專案與Adobe Analytics時涉及的下列功能：

* 允許依裝置校樣播放報告
* 允許依資產提供播放報告校樣
* 確保擷取所有播放器事件並加上時間戳記
* 如果播放未連線至網路，請確保所有播放器事件都儲存在本機
* 允許建立可隨時間追蹤播放事件的意見回圈
* 允許系統根據內容作者定義的成功標準修改內容和佈局

Adobe Analytics與AEM Screens的整合因此強制執行下列&#x200B;*目標*:

* 從數位看板實作實現投資報酬率
* 將Analytics整合為未來收集和分析使用資訊的支援基礎

## 架構詳細資訊{#architectural-details}

AEM Screens客戶想要了解何時顯示哪些內容，以及顯示的時間（匯總）。 這是標牌解決方案的通用功能。 AEM Screens將不會自行建立分析，而是運用Adobe Analytics，並借此達成市場上獨一無二的目標 — 跨管道分析，將顯示於位置的內容與其他資料來源產生關聯。

下列架構圖表說明Adobe Analytics與AEM Screens的整合：

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## 在AEM Screens中啟用Adobe Analytics {#enabling-adobe-analytics-in-aem-screens}

可從OSGi主控台設定Adobe Analytics設定。

導覽至&#x200B;**Adobe Experience Manager Web主控台設定**&#x200B;以設定AEM Screens適用的Adobe Analytics，如下圖所示：

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Screens Analytics:啟用流程{#screens-analytics-enablement-flow}

>[!CAUTION]
>
>設定屬性之前，請連絡您的Adobe關係管理員以建立票證，以取得&#x200B;**Analytics API金鑰**&#x200B;和&#x200B;**Analytics專案**&#x200B;以便與AEM Screens搭配使用。

![]()

### 配置屬性{#configuring-the-properties}

>[!CAUTION]
>
>設定屬性之前，請連絡您的Adobe關係管理員以建立票證，以取得&#x200B;**Analytics API金鑰**&#x200B;和&#x200B;**Analytics專案**&#x200B;以便與AEM Screens搭配使用。

下表反白顯示為AEM Screens設定Adobe Analytics所需的屬性及其說明：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><strong>Analytics URL</strong></td>
   <td>從播放器張貼分析資料的URL。 <br>
   針對開發/預備</em>  - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>適用於生產</em>  - https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Analytics API密鑰</strong></td>
   <td>驗證Adobe Analytics伺服器的API金鑰（由帳戶管理員提供）。</td>
  </tr>
  <tr>
   <td><strong>Analytics專案</strong></td>
   <td>在您的analytics上設定的AEM Screens專案，用以接收資料（由帳戶管理員提供）。</td>
  </tr>
  <tr>
   <td><strong>環境</strong></td>
   <td><p>預備或生產環境（選擇預備或生產）。</p></td>
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

#### 在AEM Screens中使用Adobe Analytics服務{#using-adobe-analytics-service-in-aem-screens}

此情境會透過韌體中分析服務的REST呼叫叫用Analytics API，並透過儀器螢幕 — 核心元件，明確建立並傳送特定使用案例的特定事件，同時允許擴充性，讓任何自訂訊息都可從自訂開發通道傳送至Analytics。

Analytics事件會以離線方式儲存在indexedDB中，之後會分塊並傳送至雲端。

>[!NOTE]
>
>若要進一步了解&#x200B;***Secunding***&#x200B;和&#x200B;***事件標準資料模型***，請參閱&#x200B;**[為AEM Screens設定Adobe Analytics](configuring-adobe-analytics-aem-screens.md)**。


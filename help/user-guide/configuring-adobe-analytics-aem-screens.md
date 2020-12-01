---
title: 使用AEM畫面設定Adobe Analytics
seo-title: 使用AEM畫面設定Adobe Analytics
description: '請依照本節內容，進一步瞭解使用離線Adobe Analytics排序和傳送自訂事件的相關資訊 '
seo-description: '請依照本節內容，進一步瞭解使用離線Adobe Analytics排序和傳送自訂事件的相關資訊 '
uuid: e685e553-c05b-4db4-8fa5-9ef45268b094
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: 3cec9266-4032-46b9-9c75-16da64bfea7d
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 8%

---


# 使用AEM Screens {#configuring-adobe-analytics-with-aem-screens}設定Adobe Analytics

>[!CAUTION]
>
>只有在您已安裝AEM 6.4.2 Feature Pack 2和AEM 6.3.3 Feature Pack 4時，才能使用此AEM Screens功能。
>
>若要存取其中一個功能套件，您必須聯絡Adobe支援並要求存取權。 一旦您擁有權限，就可從「套件共用」下載。

本節涵蓋下列主題：

* **Adobe Analytics與AEM畫面的排序**
* **使用離線Adobe Analytics傳送自訂事件**

## 在Adobe Analytics中搭配AEM Screens {#sequencing-in-adobe-analytics-with-aem-screens}排序

***排序程式***&#x200B;從啟動Adobe Analytics服務的資料儲存服務開始。 渠道內容會以薪資傳送Adobe Analytics事件，即資料測試擷取至Windows I/O並觸發持續事件。 這些事件將保存到索引資料庫中，並進一步放入對象儲存中。 管理員根據調度設定，從對象儲存中剪下資料，並進一步在塊儲存中傳輸資料。 它嘗試在連線時傳送最大資料量。

### 序列圖{#sequencing-diagram}

下列順序圖說明Adobe Analytics與AEM畫面的整合：

![analytics_chunking](assets/analytics_chunking.png)

## 使用離線Adobe Analytics {#sending-custom-events-using-offline-adobe-analytics}傳送自訂事件

下表摘要了事件的標準資料模型。 它會列出所有傳送至Adobe Analytics的欄位：

<table>
 <tbody>
  <tr>
   <td><strong>章節</strong></td> 
   <td><strong>屬性標籤</strong></td> 
   <td><strong>屬性名稱／索引鍵</strong></td> 
   <td><strong>必要</strong></td> 
   <td><strong>資料類型</strong></td> 
   <td><strong>屬性類型</strong><br /> </td> 
   <td><strong>說明</strong></td> 
  </tr>
  <tr>
   <td><strong><em>核心／活動</em></strong></td> 
   <td>事件GUID</td> 
   <td>event.guid</td> 
   <td>recommended</td> 
   <td>字串</td> 
   <td>UUID</td> 
   <td>識別事件例項的唯一ID</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件的收集日期時間</td> 
   <td>event.coll_dts</td> 
   <td>可選</td> 
   <td>字串</td> 
   <td>時間戳記- UTC</td> 
   <td>收集日期時間</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件的日期時間（開始）</td> 
   <td>event.dts_start</td> 
   <td>recommended</td> 
   <td>字串</td> 
   <td>時間戳記- UTC</td> 
   <td>事件開始日期時間，如果您未指定此時間，則事件時間會假設為伺服器收到該時間的時間</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件的日期時間（結束）</td> 
   <td>event.dts_end</td> 
   <td>可選</td> 
   <td>字串</td> 
   <td>時間戳記- UTC</td> 
   <td>事件完成日期時間</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>工作流程</td> 
   <td>event.workflow</td> 
   <td>recommended</td> 
   <td>字串</td> 
   <td> </td> 
   <td>工作流程名稱（畫面）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>主要DMe類別</td> 
   <td>event.category</td> 
   <td>必要</td> 
   <td>字串</td> 
   <td> </td> 
   <td>主要類別（案頭、行動、網路、程式、SDK、服務、生態系統）-事件類型分組- <strong>我們傳送播放器</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>子類別</td> 
   <td>event.subcategory</td> 
   <td>recommended</td> 
   <td>字串</td> 
   <td> </td> 
   <td>子類別——工作流程的區段或畫面的區域等。 （最新檔案、CC檔案、行動裝置創作等）。</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件／動作類型</td> 
   <td>event.type</td> 
   <td>必要</td> 
   <td>字串</td> 
   <td> </td> 
   <td>事件類型（演算、點選、夾捏、縮放）-主要使用者動作</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>子類型</td> 
   <td>event.subtype</td> 
   <td>recommended</td> 
   <td>字串</td> 
   <td> </td> 
   <td>事件子類型（建立、更新、刪除、發佈等） -使用者動作的其他詳細資訊</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>離線</td> 
   <td>event.offline</td> 
   <td>可選</td> 
   <td>布林值</td> 
   <td> </td> 
   <td>在離線／線上動作時產生事件(true/false)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>使用者代理</td> 
   <td>event.user_agent</td> 
   <td>建議（Web屬性）</td> 
   <td>字串</td> 
   <td> </td> 
   <td>使用者代理</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>語言／地區</td> 
   <td>event.language</td> 
   <td>recommended</td> 
   <td>字串</td> 
   <td> </td> 
   <td>用戶區域設定是基於RFC 3066的語言標籤約定（例如en-US、fr-FR或es-ES）的字串</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>裝置GUID</td> 
   <td>event.device_guid</td> 
   <td>可選</td> 
   <td>字串<br /> </td> 
   <td>UUID</td> 
   <td>識別裝置GUID（例如，機器ID或IP位址的雜湊+子網掩碼+網路ID+使用者代理）-我們會在這裡傳送註冊時產生的播放器使用者名稱。</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>計數</td> 
   <td>event.count</td> 
   <td>可選</td> 
   <td>數字</td> 
   <td> </td> 
   <td>發生事件的次數——此處我們傳送視訊持續時間</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>值</td> 
   <td>event.value</td> 
   <td>可選</td> 
   <td>字串</td> 
   <td> </td> 
   <td>事件的值（例如開／關設定）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>頁面名稱</td> 
   <td>event.pagename</td> 
   <td>AA的必要</td> 
   <td>字串</td> 
   <td> </td> 
   <td>自訂頁面名稱的Adobe Analytics支援</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>可選</td> 
   <td>字串</td> 
   <td> </td> 
   <td>Web屬性或行動架構的URL —— 必須包含完全限定的URL</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>錯誤代碼</td> 
   <td>event.error_code</td> 
   <td> </td> 
   <td>字串</td> 
   <td> </td> 
   <td>失敗代碼</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>錯誤類型</td> 
   <td>event.error_type</td> 
   <td> </td> 
   <td>字串</td> 
   <td> </td> 
   <td>故障類型</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>錯誤說明</td> 
   <td>event.error_description</td> 
   <td> </td> 
   <td>字串</td> 
   <td> </td> 
   <td>失敗說明<br /> </td> 
  </tr>
  <tr>
   <td><strong><em>來源／來源產品</em></strong></td> 
   <td>名稱</td> 
   <td>source.name</td> 
   <td>必要</td> 
   <td>字串</td> 
   <td> </td> 
   <td>應用程式名稱（AEM畫面）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>版本</td> 
   <td>source.version</td> 
   <td>必要</td> 
   <td>字串</td> 
   <td> </td> 
   <td>韌體版本</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>平台</td> 
   <td>source.platform</td> 
   <td>必要</td> 
   <td>字串</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>裝置</td> 
   <td>source.device</td> 
   <td>必要的例外</td> 
   <td>字串</td> 
   <td> </td> 
   <td>播放器名稱</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>作業系統版本</td> 
   <td>source.os_version</td> 
   <td>必要的例外</td> 
   <td>字串</td> 
   <td> </td> 
   <td>O/S版本</td> 
  </tr>
  <tr>
   <td><strong><em>內容</em></strong></td> 
   <td>動作</td> 
   <td>content.action</td> 
   <td>必要</td> 
   <td>字串</td> 
   <td> </td> 
   <td>資產的URL，包括實際播放的轉譯</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Mime類型</td> 
   <td>content.mimetype</td> 
   <td>可選</td> 
   <td>字串</td> 
   <td> </td> 
   <td>內容的MIME類型</td> 
  </tr>
  <tr>
   <td><strong><em>交易</em></strong></td> 
   <td>交易編號</td> 
   <td>trn.number</td> 
   <td>必要</td> 
   <td>字串</td> 
   <td>UUID</td> 
   <td>最好符合UUID v4的唯一ID</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>產品說明</td> 
   <td>trn.product</td> 
   <td>必要</td> 
   <td>字串</td> 
   <td> </td> 
   <td>資產的URL（排除轉譯）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>數量</td> 
   <td>trn.quantity</td> 
   <td>必要</td> 
   <td>字串</td> 
   <td> </td> 
   <td>播放的持續時間</td> 
  </tr>
 </tbody>
</table>


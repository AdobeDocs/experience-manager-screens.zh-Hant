---
title: 配置Adobe Analytics與AEM Screens
seo-title: Configuring Adobe Analytics with AEM Screens
description: 請按照本部分瞭解有關使用離線Adobe Analytics排序和發送自定義事件的詳細資訊
seo-description: Follow this section to learn more about sequencing and sending custom events using Offline Adobe Analytics
uuid: e685e553-c05b-4db4-8fa5-9ef45268b094
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: 3cec9266-4032-46b9-9c75-16da64bfea7d
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 4ecc1fb1-2437-449a-a085-66b2a85f4053
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 9%

---

# 配置Adobe Analytics與AEM Screens {#configuring-adobe-analytics-with-aem-screens}

>[!CAUTION]
>
>只有安裝了功能包2和功能包4,AEM才能使用此AEM Screens功AEM能。
>
>要訪問這些功能包中的任何一個，必須聯繫Adobe支援並請求訪問。 擁有權限後，您可以從包共用下載它。

本節介紹以下主題：

* **Adobe Analytics與AEM Screens測序**
* **使用離線Adobe Analytics發送自定義事件**

## Adobe Analytics與AEM Screens測序 {#sequencing-in-adobe-analytics-with-aem-screens}

的 ***排序過程*** 從激活Adobe Analytics服務的資料儲存服務開始。 渠道內容發送帶工資單的Adobe Analytics事件，即資料test捕獲到Windows I/O並觸發暫停事件。 這些事件被保存到索引資料庫中，並進一步放入對象儲存中。 管理員根據調度設定，從對象儲存中裁切資料，並進一步在塊儲存中傳輸資料。 它嘗試在連接時發送最大數量的資料。

### 排序圖 {#sequencing-diagram}

下面的序列圖解釋了Adobe Analytics與AEM Screens的整合：

![analytics_chung](assets/analytics_chunking.png)

## 使用離線Adobe Analytics發送自定義事件 {#sending-custom-events-using-offline-adobe-analytics}

下表匯總了事件的標準資料模型。 它列出了發送到Adobe Analytics的所有欄位：

<table>
 <tbody>
  <tr>
   <td><strong>章節</strong></td> 
   <td><strong>屬性標籤</strong></td> 
   <td><strong>屬性名稱/鍵</strong></td> 
   <td><strong>必要</strong></td> 
   <td><strong>資料類型</strong></td> 
   <td><strong>屬性類型</strong><br /> </td> 
   <td><strong>說明</strong></td> 
  </tr>
  <tr>
   <td><strong><em>核心/事件</em></strong></td> 
   <td>事件GUID</td> 
   <td>event.guid</td> 
   <td>建議</td> 
   <td>字串</td> 
   <td>UUID</td> 
   <td>標識事件實例的唯一ID</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件收集的日期時間</td> 
   <td>event.coll_dts</td> 
   <td>可選</td> 
   <td>字串</td> 
   <td>時間戳 — UTC</td> 
   <td>收集日期時間</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件的日期時間（開始）</td> 
   <td>event.dts_start</td> 
   <td>建議</td> 
   <td>字串</td> 
   <td>時間戳 — UTC</td> 
   <td>事件開始日期時間，如果不指定此時間，則事件時間將假定為伺服器接收該時間的時間</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件的日期時間（結束）</td> 
   <td>event.dts_end</td> 
   <td>可選</td> 
   <td>字串</td> 
   <td>時間戳 — UTC</td> 
   <td>事件完成日期時間</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>工作流程</td> 
   <td>event.workflow</td> 
   <td>建議</td> 
   <td>字串</td> 
   <td> </td> 
   <td>工作流名稱（螢幕）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>主要DMe類別</td> 
   <td>event.category</td> 
   <td>要求</td> 
   <td>字串</td> 
   <td> </td> 
   <td>主類別（案頭、移動、WEB、進程、SDK、服務、生態系統） — 事件類型分組 —  <strong>我們發送播放器</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>子類別</td> 
   <td>event.subcategory</td> 
   <td>建議</td> 
   <td>字串</td> 
   <td> </td> 
   <td>子類別 — 工作流的部分或螢幕的區域等。 （最近的檔案、CC檔案、移動建立等。）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>事件/操作類型</td> 
   <td>event.type</td> 
   <td>要求</td> 
   <td>字串</td> 
   <td> </td> 
   <td>事件類型（呈現、按一下、收縮、縮放） — 主要用戶操作</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>子類型</td> 
   <td>event.subtype</td> 
   <td>建議</td> 
   <td>字串</td> 
   <td> </td> 
   <td>事件子類型（建立、更新、刪除、發佈等）  — 用戶操作的其他詳細資訊</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>離線</td> 
   <td>event.offline</td> 
   <td>可選</td> 
   <td>布林值</td> 
   <td> </td> 
   <td>操作離線/聯機時生成事件(true/false)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>用戶代理</td> 
   <td>event.user_agent</td> 
   <td>建議（Web屬性）</td> 
   <td>字串</td> 
   <td> </td> 
   <td>用戶代理</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>語言/區域設定</td> 
   <td>event.language</td> 
   <td>建議</td> 
   <td>字串</td> 
   <td> </td> 
   <td>用戶區域設定是基於RFC 3066的語言標籤約定（例如，en-US、fr-FR或es-ES）的字串</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>設備GUID</td> 
   <td>event.device_guid</td> 
   <td>可選</td> 
   <td>字串<br /> </td> 
   <td>UUID</td> 
   <td>標識設備GUID（例如，電腦ID或IP地址的哈希+子網掩碼+網路ID+用戶代理） — 在此，我們將發送註冊時生成的播放器的用戶名。</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>計數</td> 
   <td>event.count</td> 
   <td>可選</td> 
   <td>數字</td> 
   <td> </td> 
   <td>發生事件的次數 — 此處我們發送視頻持續時間</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>值</td> 
   <td>event.value</td> 
   <td>可選</td> 
   <td>字串</td> 
   <td> </td> 
   <td>事件的值（例如，設定開啟/關閉）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>頁名</td> 
   <td>event.pagename</td> 
   <td>AA所需</td> 
   <td>字串</td> 
   <td> </td> 
   <td>Adobe Analytics對自定義頁面名稱的支援</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>可選</td> 
   <td>字串</td> 
   <td> </td> 
   <td>Web屬性或移動架構的URL — 必須包括完全限定的URL</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>錯誤代碼</td> 
   <td>event.error_code</td> 
   <td> </td> 
   <td>字串</td> 
   <td> </td> 
   <td>故障代碼</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>錯誤類型</td> 
   <td>event.error_type</td> 
   <td> </td> 
   <td>字串</td> 
   <td> </td> 
   <td>失敗類型</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>錯誤描述</td> 
   <td>event.error_description</td> 
   <td> </td> 
   <td>字串</td> 
   <td> </td> 
   <td>失敗說明<br /> </td> 
  </tr>
  <tr>
   <td><strong><em>來源/來源產品</em></strong></td> 
   <td>名稱</td> 
   <td>source.name</td> 
   <td>要求</td> 
   <td>字串</td> 
   <td> </td> 
   <td>應用名稱(AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>版本</td> 
   <td>source.version</td> 
   <td>要求</td> 
   <td>字串</td> 
   <td> </td> 
   <td>韌體版本</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Platform</td> 
   <td>source.platform</td> 
   <td>要求</td> 
   <td>字串</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>裝置</td> 
   <td>source.device</td> 
   <td>必需的例外</td> 
   <td>字串</td> 
   <td> </td> 
   <td>播放器名稱</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>作業系統版本</td> 
   <td>source.os_version</td> 
   <td>必需的例外</td> 
   <td>字串</td> 
   <td> </td> 
   <td>O/S版本</td> 
  </tr>
  <tr>
   <td><strong><em>內容</em></strong></td> 
   <td>動作</td> 
   <td>content.action</td> 
   <td>要求</td> 
   <td>字串</td> 
   <td> </td> 
   <td>資產的URL，包括實際播放的格式副本</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>MIME類型</td> 
   <td>content.mimetype</td> 
   <td>可選</td> 
   <td>字串</td> 
   <td> </td> 
   <td>內容的Mime類型</td> 
  </tr>
  <tr>
   <td><strong><em>交易記錄</em></strong></td> 
   <td>交易記錄編號</td> 
   <td>trn.number</td> 
   <td>要求</td> 
   <td>字串</td> 
   <td>UUID</td> 
   <td>優選附加到UUID v4的唯一ID</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>產品說明</td> 
   <td>trn.product</td> 
   <td>要求</td> 
   <td>字串</td> 
   <td> </td> 
   <td>資產的URL（不包括格式副本）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>數量</td> 
   <td>trn.quantity</td> 
   <td>要求</td> 
   <td>字串</td> 
   <td> </td> 
   <td>播放的持續時間</td> 
  </tr>
 </tbody>
</table>

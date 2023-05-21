---
title: 將元件添加到通道
seo-title: Adding Components to a Channel
description: 按照本頁瞭解有關將元件添加到AEM Screens項目中的渠道的詳細資訊。
seo-description: Follow this page to learn more about adding components to channels in an AEM Screens project.
uuid: 205d0edd-a696-47d0-a859-5f44d48c5e4a
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: bfbdd6eb-4921-4c2d-a179-1cac4583d568
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 56dbe098-05db-4fc3-977f-e50a0a312d64
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1443'
ht-degree: 7%

---

# 將元件添加到通道{#adding-components-to-a-channel}

構成部分是(Adobe Experience Manager)AEM經驗的基本要素。 您可以使用多個元件並將其添加到您的渠道，在AEM Screens項目中。

## AEM Screens元件 {#components-in-aem-screens}

AEM Screens提AEM供可用於螢幕項目的不同元件。

### 查看AEM Screens元件 {#viewing-aem-screens-components}

無論何時建立AEM Screens項目，您都會看到可添加到項目的預設元件清單。

要查看「螢幕」項目的預設元件，請執行以下步驟：

1. 選擇頻道。 比如說， **We.Retail在商店** —> **頻道** —> **空閒通道**。

1. 按一下 **編輯** 的子例AEM程。
1. 按一下 **+** 表徵圖。
1. 預設情況下，AEM Screens項目中包含的所有元件都會顯示，如下圖所示。

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### 添加新元件 {#adding-a-new-component}

提AEM供了許多其他元件。 您始終可以將其他元件（預設情況下不包括）添加到項目中，因為這些元件與AEM Screens相容。

以下示例顯示了將Livefyre元件添加到AEM Screens項目中：

1. 選擇要添加新元件的通道。 比如說， **We.Retail在商店** —> **頻道** —> **空閒通道**。

1. 按一下 **編輯** 的子菜單。
1. 選擇 **設計** 的子菜單。
1. 在右側選擇整個設計編輯器，然後按一下設定符號以開啟 **ParSys設計** 對話框。
1. 您可以選擇要導入到AEM Screens項目的元件。 以下示例顯示了 **利韋費雷** 是AEM Screens項目的組成部分。

![添加元件](assets/adding_components.gif)

>[!NOTE]
>
>同樣，您可以將與AEM Screens相容的任何其他新元件添加到項目中。

## 瞭解AEM螢幕元件 {#understanding-aem-screen-components}

以下部分說明了可以在項目中使用的AEM Screens元件。

>[!NOTE]
>
>要查看任何元件的屬性，請選擇該元件，然後按一下錘表徵圖以開啟/查看屬性。

### 應用程式 {#application}

的 **應用程式** 元件允許您將應用程式添加到通道。

應用程式元件具有以下屬性：

| **屬性** | **說明** |
|---|---|
| ***應用程式路徑*** | 選擇應用程式所在的絕對路徑。 |
| ***持續時間 (毫秒)*** | 選擇應用程式的持續時間。 預設情況下，持續時間設定為–1，這意味著元素將永遠運行（即單頁應用程式）。 設定持續時間值>0，顯示指定持續時間的元素，然後移到下一個持續時間。 |

以下示例說明如何嵌入應用程式元件及其屬性的預覽：

![添加_元件應用程式](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>請參閱上面的示例，查看下面每個元件的屬性。

### 頻道 {#channel}

的 **頻道** 元件允許您將整個通道添加到項目。

通道元件具有以下屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><strong><em>頻道路徑</em></strong></td>
   <td>選擇應用程式所在的此絕對路徑。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持續時間 (毫秒)</em></strong></td>
   <td>選擇頻道的整個持續時間。 將持續時間設定為–1表示嵌入式通道將在特定通道中運行其全長。</td>
  </tr>
 </tbody>
</table>

### 內嵌頁面 {#embedded-page}

安 **嵌入式頁** 允許您向項目添加嵌入頁面。 例如，它可以是Web應用程式或產品目錄。

「嵌入」頁具有以下屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><strong><em>頁面路徑<br /> </em></strong></td>
   <td>選擇此通道所在的絕對路徑。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持續時間 (毫秒)</em></strong></td>
   <td>選擇頻道的整個持續時間。 將持續時間設定為–1表示嵌入式通道將在特定通道中運行其全長。</td>
  </tr>
 </tbody>
</table>

### 內嵌順序 {#embedded-sequence}

>[!NOTE]
>
>請參閱 [嵌入序列](embedded-sequences.md) 在「創作螢幕」部分中，詳細瞭解嵌入序列。

嵌入序列允許您在現有通道內添加嵌入序列通道（與其他資產一起）。

嵌入式序列具有以下頁屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td>頻道路徑</td>
   <td>選擇要包括在通道中的序列的絕對路徑。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持續時間 (毫秒)</em></strong></td>
   <td>選擇頻道的整個持續時間。 將持續時間設定為–1表示嵌入式通道將在特定通道中運行其全長。</td>
  </tr>
  <tr>
   <td><strong><em>策略</em></strong></td>
   <td>將其設定為 <strong>原始</strong> 或 <strong>單</strong>。 將值設定為 <strong>原始</strong> 表示子序列將在父序列的每個循環上完全運行。 另一個可能的值是 <strong>單</strong> 並且每次運行時只顯示一個子項（例如，第一個循環上的第一個項，第二個循環上的第二個項，等等）。</td>
  </tr>
 </tbody>
</table>

### 動態內嵌序列 {#dynamic-embedded-sequence}

動態嵌入序列允許添加與上述類似的序列，但通道角色除外。

請參閱 [嵌入序列](embedded-sequences.md) 在「創作螢幕」部分中，詳細瞭解嵌入序列。

動態嵌入序列具有以下屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><strong><em>頻道指定任務角色</em></strong><br /> </td>
   <td>輸入渠道角色。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持續時間 (毫秒)</em></strong></td>
   <td>選擇頻道的整個持續時間。 將持續時間設定為–1表示嵌入式通道將在特定通道中運行其全長。</td>
  </tr>
  <tr>
   <td><strong><em>策略</em></strong></td>
   <td>將其設定為 <strong>原始</strong> 或 <strong>單</strong>。 將值設定為 <strong>原始</strong> 表示子序列將在父序列的每個循環上完全運行。 另一個可能的值是 <strong>單</strong> 並且每次運行時只顯示一個子項（例如，第一個循環上的第一個項，第二個循環上的第二個項，等等）。</td>
  </tr>
 </tbody>
</table>

### 體驗片段 {#experience-fragment}

體驗片段允許您將體驗片段（由一個或多個元件組成的元件，包括可在頁面中引用的內容和佈局）添加到您的AEM Screens頻道。 將元件拖放到編輯器AEM，然後選擇體驗片段。

要瞭解有關如何建立體驗片段並將其用於AEM Screens項目的更多資訊，請參閱 [使用經驗片段](experience-fragments-in-screens.md)。

![exp](assets/exp.gif)

| **屬性** | **說明** |
|---|---|
| **體驗片段** |
| ***體驗片段*** | 選擇體驗片段。 |
| ***持續時間*** | 選擇在通道中播放的體驗片段的整個持續時間。 |
| **離線設定** |
| ***用戶端資源庫*** | Javascript和CSS檔案。 |
| ***靜態檔案*** | 可以作為離線配置添加到體驗片段的靜態檔案。 |

>[!NOTE]
>
>的 **客戶端庫** 和 **靜態檔案** 從此元件添加的內容將是已配置的 **客戶端庫** 以及從體驗片段添加的靜態檔案 **屬性**。

### 影像 {#image}

「影像」允許您將影像添加到頻道。

影像資源有三個頁籤，即 **影像**。 **輔助功能**, **序列**:

| **屬性** | **說明** |
|---|---|
| **影像** |
| ***影像資產*** | 選擇影像資產。 |
| ***標題*** | 影像的標題。 |
| ***連結至*** | 添加到映像的連結。 |
| ***說明*** | 映像的簡要說明。 |
| ***大小*** | 影像大小。 |
| **協助工具** |
| ***替代文字*** | 影像的替代文本。 |
| **順序** |
| ***持續時間*** | 預設情況下，持續時間設定為 *8000毫秒*。 如果要更改影像的播放持續時間，請更新 **持續時間** 的子菜單。 |

### 切換 {#transition}

「過渡」元件允許您向「螢幕」項目添加過渡。

下圖顯示了到編輯器的過渡元件（通過拖放添加）。

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

選擇過渡表徵圖，然後按一下 **配置** （扳手錶徵圖）以開啟 **過渡** 對話框。 此對話框包括三個頁籤：

* **切換**
* **順序**
* **啟用**

>[!NOTE]
>
>預設情況下，序列設定為600毫秒。 可以使用 **序列** 頁籤。

![過渡](assets/transition.gif)

過渡元件具有以下屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><strong>切換</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>類型</em></strong></td>
   <td><p>元素之前和之後的過渡類型。 過渡 <strong>類型</strong> 包括以下選項：</p>
    <ul>
     <li><strong>普通</strong></li>
     <li><strong>淡化</strong></li>
     <li><strong>從右邊滑入</strong></li>
     <li><strong>從左邊滑入</strong></li>
     <li><strong>從頂端滑入</strong></li>
     <li><strong>從底部滑入</strong></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>順序</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>持續時間</em></strong></td>
   <td>選擇過渡的整個持續時間。 預設情況下，它設定為600毫秒。</td>
  </tr>
  <tr>
   <td><strong>啟用</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>活動自</em></strong></td>
   <td>描述何時轉換可處於活動狀態的時間戳。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>活動到</em></strong></td>
   <td>描述到轉換可以處於活動狀態為止的時間戳。</td>
  </tr>
  <tr>
   <td><strong><em>計劃</em></strong></td>
   <td>添加預定義的計畫。</td>
  </tr>
 </tbody>
</table>

### 影片 {#video}

「視頻」元件允許您向「螢幕」項目添加視頻。

視頻元件具有以下屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><em><strong>視訊資產</strong></em></td>
   <td>選擇視頻連結。</td>
  </tr>
  <tr>
   <td><em><strong>持續時間</strong></em></td>
   <td>選擇視頻的持續時間。 預設情況下，持續時間設定為–1，這意味著元素將永遠運行。 設定持續時間值&gt;0，顯示指定持續時間的元素，然後移到下一個持續時間。<br /> </td>
  </tr>
  <tr>
   <td><em><strong>轉譯</strong></em></td>
   <td><p>如果視頻長寬比不適合螢幕，則可以將渲染調整為 <strong>含</strong> 或 <strong>蓋</strong>。</p> <p><em>包含</em> 表示顯示完整視頻，並用黑色邊框填充缺失區域。</p> <p><em>封面</em> 表示視頻覆蓋了整個視區，但有些溢出的部分是隱藏的。</p> </td>
  </tr>
  <tr>
   <td><em><strong>大小</strong></em></td>
   <td>視頻大小。</td>
  </tr>
 </tbody>
</table>

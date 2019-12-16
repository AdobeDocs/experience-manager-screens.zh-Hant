---
title: 新增元件至渠道
seo-title: 新增元件至渠道
description: 請依照本頁面進一步瞭解如何在AEM Screens專案中新增元件至頻道。
seo-description: 請依照本頁面進一步瞭解如何在AEM Screens專案中新增元件至頻道。
uuid: 205d0edd-a696-47d0-a859-5f44d48c5e4a
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: bfbdd6eb-4921-4c2d-a179-1cac4583d568
docset: aem65
translation-type: tm+mt
source-git-commit: cec2a2f8b056bf713e56a9fab08d88e29263820b

---


# 新增元件至渠道{#adding-components-to-a-channel}

元件是AEM(Adobe Experience Manager)體驗的基本元素。 您可以在AEM Screens專案中使用多個元件，並將它新增至您的頻道。

## AEM畫面中的元件 {#components-in-aem-screens}

AEM Screens提供可用於「畫面」專案的不同AEM元件。

### 檢視AEM Screens元件 {#viewing-aem-screens-components}

每當您建立AEM Screens專案時，就會看到可新增至專案的預設元件清單。

若要檢視您的「畫面」專案的預設元件，請遵循下列步驟：

1. 選取渠道。 例如， **We.Retail In Store** —&gt; **Channels** —&gt; **Idle Channel**。

1. 按一 **下動作列** 中的「編輯」，以開啟AEM編輯器。
1. 按一下 **側列的** +圖示以開啟元件。
1. 依預設，AEM Screens專案中包含的所有元件都會顯示出來，如下圖所示。

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### 添加新元件 {#adding-a-new-component}

AEM提供許多其他元件。 您隨時都可以將其他元件（預設未包含）新增至專案，因為這些元件與AEM Screens相容。

下列範例顯示將Livefyre元件新增至AEM Screens專案：

1. 選取您要新增元件的渠道。 例如， **We.Retail In Store** —&gt; **Channels** —&gt; **Idle Channel**。

1. 從動 **作列按一下** 「編輯」以開啟編輯器。
1. 選擇 **設計** 模式。
1. 選擇右側的整個設計編輯器，然後按一下設定符號以開啟「 **ParSys設計」(ParSys Design** )對話框。
1. 您可以選取要匯入至AEM Screens專案的元件。 下列範例說明 **將Livefyre元件新增至** AEM Screens專案。

![adding_components](assets/adding_components.gif)

>[!NOTE]
>
>同樣地，您也可以將任何數目與AEM Screens相容的其他新元件新增至專案。

## 瞭解AEM Screen Components {#understanding-aem-screen-components}

下節將說明您可在專案中使用的AEM Screens元件。

>[!NOTE]
>
>要查看任何元件的屬性，請選擇該元件並按一下槌子表徵圖以開啟／查看屬性。

### 應用程式 {#application}

「應 **用程式** 」元件可讓您將應用程式新增至渠道。

應用程式元件具有以下屬性：

| **屬性** | **說明** |
|---|---|
| ***應用程式路徑*** | 選擇應用程式所在的絕對路徑。 |
| ***持續時間 (毫秒)*** | 選擇應用程式的持續時間。 依預設，持續時間會設為-1，這表示元素會永遠執行（即單頁應用程式）。 設定持續時間值&gt;0時，會顯示指定持續時間的元素，然後移至下一個時間。 |

以下示例說明如何嵌入應用程式元件及其屬性的預覽：

![添加元件應用程式](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>請參閱上述範例，檢視下列各元件的屬性。

### 頻道 {#channel}

Channel **元件** 可讓您將整個渠道新增至專案。

Channel元件具有以下屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><strong><em>頻道路徑</em></strong></td>
   <td>選擇此應用程式所在的絕對路徑。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持續時間 (毫秒)</em></strong></td>
   <td>選取渠道的整段期間。 將持續時間設為-1表示嵌入的通道將在特定通道中運行其全長。</td>
  </tr>
 </tbody>
</table>

### 內嵌頁面 {#embedded-page}

「內 **嵌頁面** 」可讓您將內嵌頁面新增至專案。 例如，它可以是Web應用程式或產品目錄。

「嵌入」頁具有以下屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><strong><em>頁面路徑<br /> </em></strong></td>
   <td>選擇此通道存在的絕對路徑。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持續時間 (毫秒)</em></strong></td>
   <td>選取渠道的整段期間。 將持續時間設為-1表示嵌入的通道將在特定通道中運行其全長。</td>
  </tr>
 </tbody>
</table>

### 內嵌順序 {#embedded-sequence}

>[!NOTE]
>
>請參閱「 [編寫畫面](embedded-sequences.md) 」區段下的內嵌序列，以詳細瞭解內嵌序列。

內嵌序列可讓您在現有頻道內新增內嵌序列頻道（與其他資產一起）。

嵌入序列具有以下頁屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td>頻道路徑</td>
   <td>選取要包含在渠道中的序列的絕對路徑。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持續時間 (毫秒)</em></strong></td>
   <td>選取渠道的整段期間。 將持續時間設為-1表示嵌入的通道將在特定通道中運行其全長。</td>
  </tr>
  <tr>
   <td><strong><em>策略</em></strong></td>
   <td>設為原 <strong>始</strong> 或 <strong>單一</strong>。 將值設為原 <strong>始</strong> ，表示子序列將在父序列的每個循環上完全運行。 另一個可能的值是 <strong>單</strong> ，且每個執行只會顯示一個子系的項目（例如，第一個循環上的第一個項目、第二個循環上的第二個項目等）。</td>
  </tr>
 </tbody>
</table>

### 動態內嵌序列 {#dynamic-embedded-sequence}

動態嵌入序列允許添加與上述類似的序列，但通道角色除外。

請參閱「 [編寫畫面](embedded-sequences.md) 」區段下的內嵌序列，以詳細瞭解內嵌序列。

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
   <td>選取渠道的整段期間。 將持續時間設為-1表示嵌入的通道將在特定通道中運行其全長。</td>
  </tr>
  <tr>
   <td><strong><em>策略</em></strong></td>
   <td>設為原 <strong>始</strong> 或 <strong>單一</strong>。 將值設為原 <strong>始</strong> ，表示子序列將在父序列的每個循環上完全運行。 另一個可能的值是 <strong>單</strong> ，且每個執行只會顯示一個子系的項目（例如，第一個循環上的第一個項目、第二個循環上的第二個項目等）。</td>
  </tr>
 </tbody>
</table>

### 體驗片段 {#experience-fragment}

「體驗片段」可讓您將體驗片段（由一或多個元件組成的群組，包括可在頁面內參照的內容和版面）新增至AEM Screens頻道。 將元件拖放至AEM編輯器，並選取體驗片段。

若要進一步瞭解如何建立體驗片段並將其運用在AEM Screens專案中，請參閱「使用 [體驗片段」](experience-fragments-in-screens.md)。

![exp](assets/exp.gif)

| **屬性** | **說明** |
|---|---|
| **體驗片段** |
| ***體驗片段*** | 選取體驗片段。 |
| ***持續時間*** | 選取在頻道中播放的體驗片段的整個持續時間。 |
| **離線設定** |
| ***用戶端資源庫*** | Javascript和CSS檔案。 |
| ***靜態檔案*** | 靜態檔案，您可將其新增為離線設定至體驗片段。 |

>[!NOTE]
>
>您 **從此元件添加的客戶端****Libaries和靜態檔案除了已配置的** Client端Libaries和從體驗片段的屬性添加的靜態檔案外 ********，還包括。

### 影像 {#image}

「影像」可讓您將影像新增至頻道。

影像資產有三個標籤， **即** Image **、** Accessibility **和** Sequence:

| **屬性** | **說明** |
|---|---|
| **影像** |
| ***影像資產*** | 選取影像資產。 |
| ***標題*** | 影像的標題。 |
| ***連結至*** | 新增影像的連結。 |
| ***說明*** | 影像的簡短說明。 |
| ***大小*** | 影像大小。 |
| **協助工具** |
| ***替代文字*** | 影像的替代文字。 |
| **順序** |
| ***持續時間*** | 預設情況下，持續時間設 *置為8000毫秒*。 如果要更改影像的播放持續時間，請更新「持續時 **間** 」欄位。 |

### 切換 {#transition}

「轉場」元件可讓您將轉場加入您的「畫面」專案。

下圖顯示轉場元件（透過拖放方式新增）至編輯器。

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

選取轉場圖示，然後按一下「 **設定** （扳手圖示）」以開啟「 **Transition** 」對話方塊。 此對話方塊包含三個標籤：

* **切換**
* **順序**
* **啟動**

>[!NOTE]
>
>依預設，序列設定為600毫秒。 您可以使用「序列」( **Sequence** )頁籤將過渡序列更新為其它值。

![過渡](assets/transition.gif)

轉場元件具有以下屬性：

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
   <td><p>元素之前和之後之間的過渡類型。 過渡類 <strong>型</strong> (Trination Type)包含下列選項：</p>
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
   <td>選擇過渡的整個持續時間。 預設為600毫秒。</td>
  </tr>
  <tr>
   <td><strong>啟動</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>活動自</em></strong></td>
   <td>說明轉換何時可啟動的時間戳記。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>活動到</em></strong></td>
   <td>在轉場可開始時說明的時間戳記。</td>
  </tr>
  <tr>
   <td><strong><em>排程</em></strong></td>
   <td>新增預先定義的排程。</td>
  </tr>
 </tbody>
</table>

### Video {#video}

「視訊」元件可讓您將視訊新增至您的「畫面」專案。

視訊元件具有下列屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><em><strong>視訊資產</strong></em></td>
   <td>選取視訊的連結。</td>
  </tr>
  <tr>
   <td><em><strong>持續時間</strong></em></td>
   <td>選擇視訊的持續時間。 依預設，持續時間會設為-1，表示元素會永遠執行。 設定持續時間值&gt;0時，會顯示指定持續時間的元素，然後移至下一個時間。<br /> </td>
  </tr>
  <tr>
   <td><em><strong>演算</strong></em></td>
   <td><p>如果視訊外觀比例不符合螢幕大小，您可將演算調整為包含 <strong>或</strong><strong>封面</strong>。</p> <p><em>Contain</em> （包含）：表示顯示完整視訊，且遺失區域以黑色邊框填入。</p> <p><em>封面</em> ：指影片會覆蓋整個視訊區，但溢位於側邊的部分會隱藏。</p> </td>
  </tr>
  <tr>
   <td><em><strong>大小</strong></em></td>
   <td>視訊大小。</td>
  </tr>
 </tbody>
</table>


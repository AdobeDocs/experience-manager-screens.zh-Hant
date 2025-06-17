---
title: 新增元件至管道
description: 進一步瞭解如何在AEM Screens專案中新增元件至管道。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 56dbe098-05db-4fc3-977f-e50a0a312d64
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 5%

---

# 新增元件至管道{#adding-components-to-a-channel}

元件是AEM (Adobe Experience Manager)體驗的基本元素。 您可以在AEM Screens專案中使用數個元件，並將其新增至您的頻道。

## AEM Screens中的元件 {#components-in-aem-screens}

AEM Screens提供可在Screens專案中使用的不同AEM元件。

### 檢視AEM Screens元件 {#viewing-aem-screens-components}

建立AEM Screens專案時，您會看到可新增至專案的預設元件清單。

若要檢視Screens專案的預設元件，請遵循下列步驟：

1. 按一下通道。 例如，**`We.Retail In Store`** > **頻道** > **閒置頻道**。

1. 按一下動作列中的&#x200B;**編輯**。
1. 在AEM編輯器中，按一下側邊欄中的&#x200B;**+**&#x200B;圖示。
1. AEM Screens專案中預設包含的所有元件都會顯示，如下圖所示。

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### 新增元件 {#adding-a-new-component}

AEM提供數種其他元件。 您一律可以新增其他元件（預設不包含）至專案，前提是這些元件與AEM Screens相容。

下列範例說明如何將Livefyre元件新增至AEM Screens專案：

1. 按一下您要新增元件的管道。 例如，**`We.Retail In Store`** > **頻道** > **閒置頻道**。

1. 按一下動作列中的&#x200B;**編輯**。
1. 按一下&#x200B;**設計**&#x200B;模式。
1. 按一下右側的整個設計編輯器，然後按一下設定符號，這樣您就可以開啟&#x200B;**Parsys Design**&#x200B;對話方塊。
1. 您可以按一下要匯入至AEM Screens專案的元件。 下列範例顯示將&#x200B;**Livefyre**&#x200B;元件新增至AEM Screens專案。

![正在新增_元件](assets/adding_components.gif)

>[!NOTE]
>
>同樣地，您可以將與AEM Screens相容的任何其他新元件新增至專案。

## 瞭解AEM畫面元件 {#understanding-aem-screen-components}

下節將說明您可在專案中使用的AEM Screens元件。

>[!NOTE]
>
>若要檢視任何元件的屬性，請按一下元件，然後按一下槌子圖示以開啟/檢視屬性。

### 應用程式 {#application}

**Application**&#x200B;元件可讓您新增應用程式至您的頻道。

應用程式元件具有下列屬性：

| **屬性** | **說明** |
|---|---|
| ***應用程式路徑*** | 按一下應用程式所在的絕對路徑。 |
| ***持續時間（毫秒）*** | 按一下應用程式的持續時間。 根據預設，持續時間設為–1，表示元素會永遠執行（即單頁應用程式）。 設定持續時間值>0，顯示指定持續時間的元素，然後移至下一個專案。 |

下列範例說明如何內嵌應用程式元件及其屬性的預覽：

![正在新增_componentsapplication](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>請參閱上述範例，檢視下列每個元件的屬性。

### 管道 {#channel}

**頻道**&#x200B;元件可讓您將整個頻道新增到專案。

Channel元件具有以下屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><strong><em>頻道路徑</em></strong></td>
   <td>選取應用程式所在的絕對路徑。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持續時間（毫秒）</em></strong></td>
   <td>選取管道的整個期間。 將持續時間設為–1表示內嵌頻道在特定頻道中執行其完整長度。</td>
  </tr>
 </tbody>
</table>

### 嵌入頁面 {#embedded-page}

**內嵌頁面**&#x200B;可讓您新增內嵌頁面至專案。 例如，它可以是網頁應用程式或產品目錄。

內嵌頁面具有下列屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><strong><em>頁面路徑<br /> </em></strong></td>
   <td>選取此管道存在的絕對路徑。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持續時間（毫秒）</em></strong></td>
   <td>選取管道的整個期間。 將持續時間設為–1表示內嵌頻道在特定頻道中執行其完整長度。</td>
  </tr>
 </tbody>
</table>

### 嵌入順序 {#embedded-sequence}

>[!NOTE]
>
>若要深入瞭解內嵌順序，請參閱「編寫Screens」一節中的[內嵌順序](embedded-sequences.md)。

內嵌序列可讓您在現有管道中新增內嵌序列管道（包含其他資產）。

內嵌序列具有下列頁面屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td>頻道路徑</td>
   <td>選取您要包含在管道中的序列的絕對路徑。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持續時間（毫秒）</em></strong></td>
   <td>選取管道的整個期間。 將持續時間設為–1表示內嵌頻道在特定頻道中執行其完整長度。</td>
  </tr>
  <tr>
   <td><strong><em>策略</em></strong></td>
   <td>設定為<strong>原始</strong>或<strong>單一</strong>。 將值設定為<strong>原始</strong>表示子序號會在父序號的每個週期完全執行。 其他可能的值為<strong>single</strong>。 這樣的值在每次執行時只會顯示一個子序列專案。 例如，第一個回圈上的第一個專案，以及第二個回圈上的第二個專案。</td>
  </tr>
 </tbody>
</table>

### 動態嵌入序列 {#dynamic-embedded-sequence}

動態內嵌序列可讓您新增與上述類似的序列，但頻道角色除外。

若要深入瞭解內嵌序列，請參閱「編寫Screens」一節中的[內嵌序列](embedded-sequences.md)。

動態內嵌序列具有以下屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><strong><em>頻道指派角色</em></strong><br /> </td>
   <td>輸入頻道角色。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>持續時間（毫秒）</em></strong></td>
   <td>選取管道的整個期間。 將持續時間設為–1表示內嵌頻道在特定頻道中執行其完整長度。</td>
  </tr>
  <tr>
   <td><strong><em>策略</em></strong></td>
   <td>設定為<strong>原始</strong>或<strong>單一</strong>。 將值設定為<strong>原始</strong>表示子序號會在父序號的每個週期完全執行。 其他可能的值為<strong>single</strong>。 這樣的值在每次執行時只會顯示子序列的一個專案。 例如，第一個回圈上的第一個專案，以及第二個回圈上的第二個專案。</td>
  </tr>
 </tbody>
</table>

### 體驗片段 {#experience-fragment}

體驗片段可讓您將體驗片段（一或多個元件的群組，包括可在頁面中參考的內容和版面）新增到您的AEM Screens頻道。 將元件拖放至AEM編輯器並按一下體驗片段。

若要深入瞭解如何建立體驗片段並將其套用至AEM Screens專案，請參閱[使用體驗片段](experience-fragments-in-screens.md)。

![費用](assets/exp.gif)

| **屬性** | **說明** |
|---|---|
| **體驗片段** |
| ***體驗片段*** | 選取體驗片段。 |
| ***持續時間*** | 選取在頻道中播放的體驗片段的整個期間。 |
| **離線設定** |
| ***使用者端資料庫*** | JavaScript和CSS檔案。 |
| ***靜態檔案*** | 您可以新增為體驗片段的離線設定的靜態檔案。 |

>[!NOTE]
>
>您從此元件新增的&#x200B;**使用者端資料庫**&#x200B;和&#x200B;**靜態檔案**&#x200B;除了已設定的&#x200B;**使用者端資料庫**&#x200B;和從體驗片段的&#x200B;**屬性**&#x200B;新增的靜態檔案之外。

### 影像 {#image}

影像可讓您將影像新增至色版。

影像資產有三個索引標籤，即&#x200B;**影像**、**協助工具**&#x200B;和&#x200B;**序列**：

| **屬性** | **說明** |
|---|---|
| **影像** |
| ***影像資產*** | 按一下影像資產。 |
| ***標題*** | 影像標題。 |
| ***連結至*** | 新增影像的連結。 |
| ***說明*** | 影像的簡短說明。 |
| ***大小*** | 影像的大小。 |
| **協助工具** |
| ***替代文字*** | 影像的替代文字。 |
| **序列** |
| ***持續時間*** | 根據預設，持續時間設定為&#x200B;*8000毫秒*。 若要變更影像的播放持續時間，請更新&#x200B;**持續時間**&#x200B;欄位。 |

### 切換 {#transition}

轉變元件可讓您將轉變新增到您的Screens專案。

下圖顯示編輯器中的轉變元件（透過拖放方式新增）。

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

按一下轉變圖示並按一下&#x200B;**設定** （扳手圖示）以開啟&#x200B;**轉變**&#x200B;對話方塊。 此對話方塊包含三個索引標籤：

* **轉變**
* **序列**
* **啟用**

>[!NOTE]
>
>依預設，順序會設為600毫秒。 您可以使用&#x200B;**順序**&#x200B;索引標籤，將轉變順序更新為其他值。

![轉變](assets/transition.gif)

轉場元件具有下列屬性：

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
   <td><p>元素之前和之後之間的轉變型別。 轉換<strong>型別</strong>包含下列選項：</p>
    <ul>
     <li><strong>一般</strong></li>
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
   <td>選取轉變的整個期間。 預設為600毫秒。</td>
  </tr>
  <tr>
   <td><strong>啟用</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>啟用開始日期</em></strong></td>
   <td>說明轉換何時可以作用中的時間戳記。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>啟用結束日期</em></strong></td>
   <td>時間戳記會提供說明，直到轉變可以啟動為止。</td>
  </tr>
  <tr>
   <td><strong><em>排程</em></strong></td>
   <td>新增預先定義的排程。</td>
  </tr>
 </tbody>
</table>

### 影片 {#video}

視訊元件可讓您將視訊新增至您的Screens專案。

視訊元件具有下列屬性：

<table>
 <tbody>
  <tr>
   <td><strong>屬性</strong></td>
   <td><strong>說明</strong></td>
  </tr>
  <tr>
   <td><em><strong>視訊資產</strong></em></td>
   <td>按一下視訊的連結。</td>
  </tr>
  <tr>
   <td><em><strong>持續時間</strong></em></td>
   <td>選取視訊的持續時間。 根據預設，持續時間設為–1，表示元素會永遠執行。 設定持續時間值&gt;0，顯示指定持續時間的專案，然後移至下一個專案。<br /> </td>
  </tr>
  <tr>
   <td><em><strong>轉譯</strong></em></td>
   <td><p>如果視訊外觀比例不符合熒幕，您可以將演算調整為<strong>包含</strong>或<strong>封面</strong>。</p> <p><em>包含</em>表示已顯示完整視訊，而遺漏的區域已填入黑色邊框。</p> <p><em>封面</em>表示視訊涵蓋整個檢視區，但兩側溢位的部分會隱藏。</p> </td>
  </tr>
  <tr>
   <td><em><strong>大小</strong></em></td>
   <td>視訊的大小。</td>
  </tr>
 </tbody>
</table>

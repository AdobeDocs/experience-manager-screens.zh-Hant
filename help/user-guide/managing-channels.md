---
title: 建立和管理渠道
seo-title: 管理頻道
description: 請依照本頁來瞭解如何建立和管理渠道。 此外，也說明頻道儀表板以及編輯頻道內容。
seo-description: 請依照本頁來瞭解如何建立和管理渠道。 此外，也說明頻道儀表板以及編輯頻道內容。
translation-type: tm+mt
source-git-commit: 6c2c7e4f757666160b79018d1195a79b99a4202d
workflow-type: tm+mt
source-wordcount: '1326'
ht-degree: 2%

---


# 建立和管理通道{#creating-and-managing-channels}

頻道會顯示一系列內容（影像和視訊），也會顯示網站或單頁應用程式。

此頁面顯示如何建立和管理AEM畫面的頻道。

**先決條件**:

* [設定和部署畫面](configuring-screens-introduction.md)
* [建立和管理畫面專案](creating-a-screens-project.md)

## 建立新通道{#creating-a-new-channel}

在您為AEM Screens建立專案後，請依照下列步驟為專案建立新的頻道：

1. 依序選取Adobe Experience Manager連結（左上）和「畫面」。 或者，您也可以直接導覽至`https://localhost:4502/screens.html/content/screens`。

1. 導覽至您的「畫面」專案，並選取「頻道」**資料夾。**

1. 從操作欄按一下&#x200B;**建立**。

   ![demochannel](assets/create-channel1.png)

1. 從&#x200B;**建立**&#x200B;嚮導中選擇&#x200B;**序列通道**&#x200B;模板，然後按一下&#x200B;**下一步**。

   ![demochannel](assets/create-channel2.png)

1. 將標題輸入為&#x200B;**ScreensChannel**，然後按一下&#x200B;**Create**。

   ![demochannel](assets/create-project4.png)

1. 現在會將序列頻道新增至您的&#x200B;**頻道**&#x200B;資料夾。

### 通道類型{#channel-types}

使用精靈時可使用下列範本選項，例如：

| **範本選項** | **說明** |
|---|---|
| 頻道資料夾 | 允許建立資料夾以儲存渠道的集合。 |
| 順序頻道 | 允許建立依序播放元件的頻道（在投影片中逐一播放）。 |
| 應用程式頻道 | 可讓您在Screens播放器中展示您的自訂網頁應用程式。 |
| 1x1 拆分畫面頻道 | 允許在單個區域中查看元件。 |
| 1x2 拆分畫面頻道 | 允許在兩個區域中檢視資產（水準分割）。 |
| 2X1分割螢幕頻道 | 允許在兩個區域（垂直分割）中檢視資產。 |
| 2x2 拆分畫面頻道 | 允許在四個區域中檢視資產（在矩陣中水準和垂直分割）。 |
| 2 至 3 拆分畫面頻道 | 允許在兩個區域（水準分割）中檢視資產，其中一個區域比另一個區域大。 |
| 左或右L列分割螢幕色版 | 可讓內容作者在適當大小的區域中檢視不同類型的資產。 |

>[!NOTE]
>
>「分割畫面」頻道會將顯示畫面分割為多個區域，讓您可以同時並排播放多個體驗。 體驗可以是靜態資產／文字或內嵌的序列。

>[!IMPORTANT]
>
> 在您建立內容並新增至頻道後，下一步是建立位置，然後建立顯示。 此外，您還需要將該頻道指派給顯示器。 請參閱本節結尾的下列資源，以進一步瞭解。

## 使用通道{#working-with-channels}

您可以編輯、檢視屬性和控制面板、複製、預覽和刪除渠道。


![screen_shot_2019-07-24at103723am](assets/screen_shot_2019-07-24at103723am.png)

### 新增／編輯內容至頻道{#adding-editing-content-to-a-channel}

若要新增或編輯頻道中的內容，請遵循下列步驟：

1. 選取您要編輯的渠道（如上圖所示）。
1. 按一下動作列左上角的「編輯」**，以編輯頻道屬性。**&#x200B;編輯器隨即開啟，可讓您將資產／元件新增至您要發佈的渠道。

>[!NOTE]
>您可以新增元件至渠道。 有關詳細資訊，請參閱&#x200B;**[將元件添加到通道](adding-components-to-a-channel.md)**。

![demchannel1](assets/demochannel1.gif)

**上傳影片至頻道**

請依照下列步驟，將影片上傳至您的頻道：

1. 選取您要上傳視訊的頻道。
1. 按一下操作欄中的&#x200B;**編輯**&#x200B;以開啟編輯器。
1. 在「資產」下方選取「**視訊**」，並拖放必要的視訊。

>[!NOTE]
>如果您在頻道中上傳視訊時遇到問題，請參閱「疑難排解視訊」[。](troubleshoot-videos.md)

### 查看屬性{#viewing-properties}

若要檢視或編輯渠道的屬性，請遵循下列步驟：

1. 按一下您要編輯的渠道。
1. 按一下操作欄中的&#x200B;**屬性**&#x200B;以檢視／編輯通道屬性。 下列標籤可讓您變更選項。

![屬性](assets/properties.gif)

### 檢視控制面板{#viewing-dashboard}

若要檢視渠道的控制面板，請遵循下列步驟：

1. 選取您要編輯的渠道。
1. 按一下動作列中的&#x200B;**控制面板**&#x200B;以檢視控制面板。 **頻道資訊**、**指派顯示**&#x200B;和&#x200B;**待定啟動**&#x200B;面板隨即開啟，如下圖所示：

![控制面板](assets/dashboard.gif)

### 頻道資訊 {#channel-information}

「頻道資訊」面板會說明頻道屬性以及頻道的預覽。 此外，它還提供有關頻道是離線還是線上的資訊。

按一下(**...**)，以檢視屬性、編輯內容或更新頻道的快取（離線內容）。****

![screen_shot_2017-12-20at82048am](assets/screen_shot_2017-12-20at82048am.png)

#### 檢視資訊清單{#view-manifest}

您可從渠道控制面板檢視資訊清單。

>[!IMPORTANT]
>此選項僅適用於AEM 6.4 Feature Pack 8或AEM 6.5 Feature Pack 4。

請依照下列步驟，從頻道控制面板啟用此選項：

1. **將渠道設為離線**
   1. 選擇通道並從操作欄中選擇&#x200B;**屬性**
   1. 導覽至「**頻道**」標籤，並確定您已取消勾選「開發人員模式」（強制頻道連線）**選項**
   1. 按一下&#x200B;**保存並關閉**
1. **更新離線內容**
   1. 選擇通道並從操作欄中選擇&#x200B;**儀表板**
   1. 導航至&#x200B;**CHANNEL INFORMATION**&#x200B;面板，然後按一下&#x200B;*...*
   1. 按一下「更新離線內容&#x200B;**」**

您應該會在「頻道」控制面板的「頻道資訊」面板中看到「檢視資訊清單」**選項。******

![影像1](assets/channel-one.png)


### 線上和離線頻道{#online-and-offline-channels}

>[!NOTE]
>依預設，當您建立渠道時，會是「離線」。

當您建立渠道時，可將其定義為線上或離線渠道。

***線上頻道***&#x200B;將在即時環境中顯示更新內容，而&#x200B;***離線頻道***&#x200B;則顯示快取內容。

請依照下列步驟，讓渠道上線：

1. 以&#x200B;**TestProject** —> **Channels** —> **TestChannel**&#x200B;的形式導覽至渠道。

   選取渠道。

   ![screen_shot_2019-08-01at31406pm](assets/screen_shot_2019-08-01at31406pm.png)

   按一下動作列中的&#x200B;**儀表板**，以檢視播放器的狀態。 **CHANNEL INFORMATION**&#x200B;面板提供有關頻道是線上還是離線的資訊。

   ![screen_shot_2019-08-01at31458pm](assets/screen_shot_2019-08-01at31458pm.png)

1. 按一下操作欄中的&#x200B;**屬性** ，然後導航到&#x200B;**渠道**&#x200B;頁籤，如下所示：

   ![screen_shot_2019-08-01at31542pm](assets/screen_shot_2019-08-01at31542pm.png)

1. 檢查&#x200B;**開發人員** **模式（強制頻道連線）**，將頻道設為線上。

   按一下「儲存並關閉」以儲存您的選項。****

   ![screen_shot_2019-08-01at31658pm](assets/screen_shot_2019-08-01at31658pm.png)

   導覽回頻道控制面板，現在&#x200B;**頻道資訊**&#x200B;面板會顯示播放器的線上狀態。

   ![screen_shot_2019-08-01at31821pm](assets/screen_shot_2019-08-01at31821pm.png)

>[!NOTE]
>如果您想要再次將渠道設為離線，請從&#x200B;**屬性**&#x200B;標籤取消勾選「開發人員模式」選項(如步驟(3)所示)，然後從&#x200B;**渠道資訊**&#x200B;面板按一下&#x200B;**更新離線內容**，如下圖所示。

![dashboard2](assets/dashboard2.gif)

#### 從「裝置儀表板{#automatic-versus-manual-updates-from-the-device-dashboard}」自動更新與手動更新

下表摘要了與裝置控制面板的自動和手動更新相關的事件。

<table>
 <tbody>
  <tr>
   <td><strong>事件</strong></td>
   <td><strong>裝置自動更新</strong></td>
   <td><strong>裝置手動更新</strong></td>
  </tr>
  <tr>
   <td>線上通路的變更</td>
   <td>自動更新內容</td>
   <td><p>在「裝置：推播設定」</p> <p>或,</p> <p>在<strong><i>裝置上更新的內容：重新啟動</i></strong></p> </td>
  </tr>
  <tr>
   <td>離線頻道中的變更，但不會觸發頻道的「推播內容」（無離線封裝重新建立）</td>
   <td>無內容更新</td>
   <td>無內容更新</td>
  </tr>
  <tr>
   <td>離線頻道和頻道「推播內容」的變更會觸發（新的離線套件）</td>
   <td>自動更新內容</td>
   <td><p>在<strong><i>裝置上更新的內容：推播設定</i></strong></p> <p>或,</p> <p>在<strong><i>裝置上更新的內容：重新啟動</i></strong></p> </td>
  </tr>
  <tr>
   <td><p>設定中的變更</p>
    <ul>
     <li>顯示（強制頻道）</li>
     <li>裝置</li>
     <li>頻道指派（新頻道、已移除頻道）</li>
     <li>頻道指派（角色、事件、排程）</li>
    </ul> </td>
   <td>自動更新設定</td>
   <td><p><strong><i>裝置上的組態已更新：推播設定</i></strong></p> <p>或,</p> <p><strong><i>裝置上的組態已更新：重新啟動</i></strong></p> </td>
  </tr>
 </tbody>
</table>

### 指派的顯示 {#assigned-displays}

指派的顯示面板會顯示與頻道相關的顯示。 它提供已分配顯示的快照以及解析度。

關聯的顯示將列在&#x200B;**「已分配顯示」面板中，如下所示：**

![chlimage_1-27](assets/chlimage_1-27.png)

>[!NOTE]
>要瞭解如何在位置中建立顯示，請參閱：
>
>* [建立和管理位置](managing-locations.md)
>* [建立和管理顯示](managing-displays.md)

>



此外，按一下&#x200B;**ASSIGNED DISPLAYS**&#x200B;面板中的顯示，查看顯示資訊，如下所示：

![chlimage_1-28](assets/chlimage_1-28.png)

### 後續步驟{#the-next-steps}

在您的頻道中建立頻道並新增／編輯內容後，下一步是瞭解如何建立位置和顯示。 此外，接著指派頻道給該顯示器。

如需後續步驟，請參閱下列資源：

* [建立和管理渠道](managing-channels.md)
* [建立和管理位置](managing-locations.md)
* [建立和管理顯示](managing-displays.md)


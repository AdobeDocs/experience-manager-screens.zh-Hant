---
title: 資產層級啟用
description: 瞭解如何在播放器的當地時區中，於排程的時間範圍內啟用頻道中的特定資產。
feature: Authoring Screens, Asset Level Activation
role: Admin, Developer
level: Intermediate
exl-id: a2f5b2cc-6797-4397-b49c-72175a2d2ef7
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '1460'
ht-degree: 1%

---

# 資產層級啟用 {#asset-level-scheduling}

本頁面說明在管道中使用的資產的資產層級啟用。

本節將涵蓋下列主題：

* 概觀
* 啟用時間
* 單一事件播放
* 處理資產中的週期性
   * 日時段分割
   * 周劃分
   * MonthParting
   * 零件組合
* 多資產啟用
* 通用開始時間的全域覆寫

<!-- REFERS TO ARCHIVED VERSIONS THAT ADOBE NO LONGER SUPPORTS>
>[!CAUTION]
>
>This AEM Screens functionality is only available if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, you must contact Adobe Support and request access. When you have permission, you can download it from Package Share. -->

## 概觀 {#overview}

***資產層級啟用*** 可讓您在播放器的當地時區中，針對排程時間範圍啟用頻道中的特定資產。 這適用於影像、影片、轉變、頁面和內嵌頻道（動態或靜態）。

*例如*，而您只想在星期一和星期三的快樂時數（下午2點至下午5點）顯示特殊促銷活動。

使用此功能，您不僅可以指定開始和結束日期及時間，還可以指定週期模式。

## 啟用時間 {#single-event-playback}

資產層級啟動是透過設定 **啟用** 索引標籤來存取資產的屬性。

請依照下列步驟執行資產層次排程：

1. 選取任一管道，然後選取「 」 **編輯** 從動作列移除。

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >詳細瞭解如何
   >
   >* 建立專案，請參閱 [建立新專案](creating-a-screens-project.md).
   >* 建立內容並新增至管道，請參閱 [管理管道](managing-channels.md).

1. 選取 **編輯** 因此您可以開啟管道編輯器，並選取您要套用排程的資產。

   ![影像](/help/user-guide/assets/asset-activation/asset-level2.png)

1. 選取資產，然後選取左上方 **設定** （扳手圖示）。

   選取 **啟用** 標籤。

   ![影像](/help/user-guide/assets/asset-activation/asset-level3.png)

1. 您可以使用以下專案指定日期選擇器的日期 **啟用開始日期** 和 **啟用結束日期** 欄位。

   如果您選取 **啟用開始日期** 和 **啟用結束日期** 日期與時間，資產只會分別顯示該開始日期/時間與結束日期/時間之間的顯示和回圈。

   ![影像](/help/user-guide/assets/asset-activation/asset-level3.png)

## 處理資產中的週期性 {#handling-recurrence-in-assets}

您也可以根據需求，排程資產以每日、每週或每月的特定間隔重複傳送。

假設您只想在星期五下午1:00至晚上10:00顯示影像。 您可以使用 **啟用** 索引標籤來設定資產的所需循環間隔。

### 日時段分割 {#day-parting}

1. 選取資產並選取 **設定** （扳手圖示）以開啟「屬性」對話方塊。

1. 輸入開始日期/時間和結束/日期時間後，您可以使用運算式或自然文字版本來指定週期性排程。

   >[!NOTE]
   >您可以略過或包含 **啟用開始日期** 和 **啟用結束日期** 欄位，並根據您的需求將運算式新增至「排程」欄位。

1. 將運算式輸入 **排程** 而且您的資產會以特定的日期和時間間隔顯示。

#### 日期分界運算式範例 {#example-one}

下表總結列出一些範例運算式，您可以在將頻道指派給顯示畫面時將其新增到排程。

| **運算式** | **解譯** |
|---|---|
| 上午8:00之前 | 頻道中的資產會在每天上午8:00之前播放 |
| 下午2:00以後 | 頻道中的資產會在每天下午2:00之後播放 |
| 下午 00:15 過後和 下午 00:45 之前 | 頻道中的資產會在每天下午12:15之後播放30分鐘 |
| 12:15之前以及12:45之後 | 頻道中的資產會在每天中午12:15之前播放，也會在下午12:45之後播放。 |

>[!NOTE]
>
>您也可以使用 _軍事時間_ 表示法(14:00)，而非 *上午./P.M。* （下午2:00）。

### 周劃分 {#week-parting}

1. 選取資產，然後選取 **設定** （扳手圖示）。

1. 輸入開始日期/時間和結束/日期時間後，您可以使用運算式或自然文字版本來指定週期性排程。

   >[!NOTE]
   >您可以略過或包含 **啟用開始日期** 和 **啟用結束日期** 欄位，並根據您的需求將運算式新增至「排程」欄位。

1. 將運算式輸入 **排程** 而您的資產則會以特定的日期和時間間隔顯示。

#### WeekParting的運算式範例 {#example-two}

下表總結列出一些範例運算式，您可以在將頻道指派給顯示畫面時將其新增到排程。

| **運算式** | **解譯** |
|---|---|
| `Mon,Wed,Fri` | 資產會在週一、週三和週五的頻道中播放 |
| `Mon-Thu` | 資產會在從星期一到星期四的管道中播放 |

>[!NOTE]
>
>您也可以使用 _完整_ 表示法(`Monday,Wednesday,Friday`)而非 _短手_ (`Mon,Wed,Fri`)。


### MonthParting {#month-parting}

1. 選取資產，然後選取 **設定** （扳手圖示）。

1. 輸入開始日期/時間和結束/日期時間後，您可以使用運算式或自然文字版本來指定週期性排程。

   >[!NOTE]
   >您可以略過或包含 **啟用開始日期** 和 **啟用結束日期** 欄位，並根據您的需求將運算式新增至「排程」欄位。

1. 將運算式輸入 **排程** 而您的資產則會以特定的日期和時間間隔顯示。

#### MonthParting的運算式範例 {#example-three}

下表總結列出一些範例運算式，您可以在將頻道指派給顯示畫面時將其新增到排程。

| **運算式** | **解譯** |
|---|---|
| `on February,May,August,November` | 資產會在2月、5月、8月和11月於頻道播放 |
| `on February-July` | 資產會從2月到7月底在頻道中播放 |

>[!NOTE]
>在定義一週的天數與月份時，您既可以使用短手記號與全名記號，例如，週一/週一，以及一月/一月。

### 零件組合 {#combined-parting}

1. 選取資產，然後選取 **設定** （扳手圖示）。

1. 輸入開始日期/時間和結束/日期時間後，您可以使用運算式或自然文字版本來指定週期性排程。

   >[!NOTE]
   >您可以略過或包含 **啟用開始日期** 和 **啟用結束日期** 欄位，並根據您的需求將運算式新增至「排程」欄位。

1. 將運算式輸入 **排程** 而您的資產則會以特定的日期和時間間隔顯示。

#### 分割組合的運算式範例 {#example-four}

下表總結列出一些範例運算式，您可以在將頻道指派給顯示畫面時將其新增到排程。

| **運算式** | **解譯** |
|---|---|
| `after 6:00 and before 18:00 on Mon,Wed of Jan-Mar` | 從1月到3月底，星期一和星期三上午6點至下午6點在頻道中播放資產 |
| `on the 1st day of January after 2:00 P.M. also on the 2nd day of January also on the 3rd day of January before 3:00 A.M.` | 頻道中的資產在1月1日下午2:00之後開始播放，並持續播放1月2日的一整天，直到1月3日凌晨3:00 |
| `on the 1-2 days of January after 2:00 P.M. also on the 2-3 days of January before 3:00 A.M.` | 頻道中的資產在1月1日下午2:00之後開始播放程式，繼續播放至1月2日凌晨3:00，然後在1月2日下午2:00重新開始播放，並繼續播放至1月3日凌晨3:00 |

>[!NOTE]
>在定義一週的天數與月份時，您既可以使用短手記號與全名記號，例如，週一/週一，以及一月/一月。 此外，您也可以使用 _軍事時間_ 表示法(14:00)，而非 *上午./P.M。*（下午2:00）。


## 多資產啟用 {#multi-asset-scheduling}

<!--
>[!CAUTION]
>
>The **Multi-asset Activation** feature is only available if you have installed AEM 6.3 Feature Pack 5 or AEM 6.4 Feature Pack 3. -->

***多資產啟用*** 可讓使用者選取多個資產，並將播放排程套用至所有選取的資產。

### 先決條件 {#prerequisites}

若要針對您的資產使用多資產層級啟用，請建立具有序列頻道的AEM Screens專案。 例如，下列使用案例會示範功能的實作：

* 建立標題為的AEM Screens專案 **MultiAssetDemo**.
* 建立標題為 **MultiAssetChannel** 和新增內容至頻道，如下圖所示。

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

請依照下列步驟選取多個資產，並排程在AEM Screens專案中顯示這些資產：

1. 選取 **MultiAssetChannel**，然後選取 **編輯** 從動作列移除。

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. 從編輯器選取多個資產，然後選取「 」 **編輯啟用** （左上角圖示）。

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. 選取日期和時間 **啟用開始日期** 和 **啟用結束日期** 從 **元件啟用** 對話方塊。 選取完排程後，選取核取記號圖示。

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. 選取重新整理以檢查套用了多資產排程的資產。

   >[!NOTE]
   >
   >排程圖示會顯示在具有多資產啟用的資產的右上角。

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

## 通用開始時間的全域覆寫 {#global-override-scheduling}

***通用開始時間的全域覆寫***，此設定可讓內容作者根據特定時間定義影像或視訊資產的播放。 不會使用任何個別播放器的時間/時區設定。

一般而言，播放是由任何指定播放器的本機時間所決定，但透過全域覆寫，特定的通用開始時間可用於起始資產的播放。

這可讓內容作者將特定資產的播放指定為發生在特定日期/時間，而不論任何具有指派內容的播放器上的本機時鐘為何。

通用開始時間的全域覆寫可透過設定 **啟用** 索引標籤來存取資產的屬性。 請依照下列步驟，執行資產排程的「全域覆寫」：

1. 選取任一管道，然後選取「 」 **編輯** 以新增或編輯頻道中的內容。

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

1. 選取&#x200B;**編輯**。
1. 在管道編輯器中，選取您要套用其排程的資產。

   ![screen_shot_2018-12-21at70550am](/help/user-guide/assets/asset-activation/Asset-level4.png)

1. 針對全域覆寫，請在 **時區覆寫** 區段。 如果您沒有在此區域輸入任何內容，則套用的時區是播放器的時區。



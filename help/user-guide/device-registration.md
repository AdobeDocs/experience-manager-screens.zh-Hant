---
title: 裝置註冊
description: 瞭解AEM Screens專案中的裝置註冊程式。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens, Device Registration
role: Admin
level: Intermediate
exl-id: b2d3a2cd-263f-4142-80da-29ce54cbf391
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---

# 裝置註冊 {#device-registration}

以下頁面說明AEM Screens專案中的裝置註冊程式。

## 註冊裝置 {#registering-a-device}

裝置註冊程式會在兩部不同的電腦上完成：

* 要註冊的實際裝置，例如您的招牌顯示器
* 用來註冊裝置的AEM伺服器

>[!NOTE]
>
>下載最新的Windows Player之後(*.exe*)，從 [AEM 6.4播放器下載](https://download.macromedia.com/screens/) 請依照播放器上的步驟完成隨選安裝：
>
>1. 長按左上角以開啟「管理」面板。
>1. 瀏覽至 **設定** 從左側動作功能表，然後輸入AEM執行個體的位置地址。 **伺服器** 並按一下 **儲存**.
>1. 選取 **註冊** 左側動作選單的連結，以及完成裝置註冊程式的下列步驟。
>

![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. 在裝置上啟動AEM Screens Player。 畫面會顯示註冊UI。

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. 在AEM中，導覽至 **裝置** 資料夾。

   >[!NOTE]
   >
   >若要取得在AEM儀表板中建立畫面專案的詳細資訊，請參閱 [建立和管理Screens專案](creating-a-screens-project.md).

1. 點選/按一下 **裝置管理員** 按鈕。

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. 點選/按一下 **裝置註冊** 按鈕。

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. 選取所需的裝置（與步驟1相同），然後點選/按一下 **註冊裝置**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. 在AEM中，等候裝置傳送其註冊代碼。

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. 在您的裝置中，檢查 **註冊代碼**.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. 如果 **註冊代碼** 兩台機器上的內容相同，請點選/按一下 **驗證** AEM按鈕，如步驟(6)所示。
1. 為裝置設定所要的名稱，然後按一下 **註冊**.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. 點選/按一下 **完成** 以完成註冊程式。

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >此 **註冊新專案** 可讓您註冊新裝置。
   >
   >此 **指派顯示區** 可讓您直接將裝置新增至顯示器。

   如果您按一下 **完成**，將裝置指派給顯示器。

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >若要進一步瞭解如何建立和管理Screens專案的顯示器，請參閱 [建立和管理顯示器](managing-displays.md).

### 將裝置指派給顯示器 {#assigning-device-to-a-display}

如果您尚未將裝置指派給顯示區，請依照下列步驟，將裝置指派給AEM Screens專案中的顯示區：

1. 選取裝置並按一下 **指派裝置** 從動作列移除。

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. 選取顯示的路徑 **顯示器/裝置設定路徑**.

   ![screen_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. 按一下 **指派** 當您選取路徑時。

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. 按一下 **完成** 成功指派裝置後，如下圖所示。

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   您也可以按一下以檢視顯示控制面板 **完成**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## 從「裝置管理員」搜尋裝置 {#search-device}

將裝置註冊到播放器後，您就可以從「裝置管理員」UI檢視所有裝置。

1. 例如，從您的AEM Screens專案導覽至「裝置管理員UI」 。 **DemoScreens** > **裝置**.

1. 選取 **裝置** 資料夾並按一下 **裝置管理員** 從動作列移除。

   ![影像](/help/user-guide/assets/device-manager/device-manager-1.png)

1. 已註冊裝置的清單隨即顯示。

1. 如果您的註冊裝置清單很長，現在可以使用動作列的搜尋圖示進行搜尋

   ![影像](/help/user-guide/assets/device-manager/device-manager-2.png)

   或，

   按一下 `/` （正斜線）以叫用搜尋功能。

   ![影像](/help/user-guide/assets/device-manager/device-manager-3.png)


### 搜尋功能的限制 {#limitations}

* 使用者可以搜尋中現有的任何單字 *裝置ID* 或 *裝置名稱*.

  >[!NOTE]
  >建議您以多個字詞來建立裝置名稱，例如 *波士頓商店大廳* 而不是單一的 *BostonStoreLobby*.

* 如果您建立裝置名稱，例如 *波士頓商店大廳*，會搜尋任何單字 *波士頓*， *儲存*，或 *大廳*. 但是，如果裝置名稱為 *BostonStoreLobby*，然後搜尋 *波士頓* 未顯示任何結果。

* 萬用字元， `*` 支援搜尋。 如果您想要尋找所有名稱開頭為的裝置 *波士頓*，您可以使用 *波士頓**.

* 如果裝置名稱為 *BostonStoreLobby* 並搜尋 *波士頓* 不會傳回結果，然後使用 *波士頓**會在您的搜尋條件中傳回結果。

## 裝置註冊的限制 {#limitations-on-device-registration}

系統範圍的使用者密碼限制可能會導致裝置註冊失敗。 裝置註冊會使用隨機產生的密碼來建立裝置使用者。

如果密碼受 *AuthorizableActionProvider* 設定，建立裝置使用者可能會失敗。

>[!NOTE]
>
>目前產生的隨機密碼由36個ASCII字元組成，範圍介於33到122之間（幾乎包含所有特殊字元）。

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### 其他資源 {#additional-resources}

若要瞭解AEM Screens Player，請參閱 [AEM Screens Player](working-with-screens-player.md).

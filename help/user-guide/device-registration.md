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
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '721'
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
>從[AEM 6.4 Player下載](https://download.macromedia.com/screens/)頁面下載最新的Windows Player (*.exe*)之後，請依照播放器上的步驟完成隨選安裝：
>
>1. 長按左上角以開啟「管理」面板。
>1. 從左側動作功能表瀏覽至&#x200B;**設定**，並在&#x200B;**伺服器**&#x200B;中輸入AEM執行個體的位置位址，然後按一下&#x200B;**儲存**。
>1. 按一下左側動作功能表的&#x200B;**註冊**&#x200B;連結，然後依照下列步驟完成裝置註冊程式。
>

![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. 在裝置上啟動AEM Screens Player。 畫面會顯示註冊UI。

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. 在AEM中，導覽至您專案的&#x200B;**裝置**&#x200B;資料夾。

   >[!NOTE]
   >
   >若要取得有關在AEM儀表板中建立Screens專案的詳細資訊，請參閱[建立和管理Screens專案](creating-a-screens-project.md)。

1. 按一下動作列中的&#x200B;**裝置管理員**&#x200B;按鈕。

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. 按一下右上角的&#x200B;**裝置註冊**&#x200B;按鈕。

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. 按一下所需的裝置（與步驟1相同），然後按一下&#x200B;**註冊裝置**。

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. 在AEM中，等候裝置傳送其註冊代碼。

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. 在您的裝置中，檢查&#x200B;**註冊代碼**。

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. 如果兩部電腦上的&#x200B;**註冊代碼**&#x200B;相同，請按一下AEM中的&#x200B;**驗證**&#x200B;按鈕，如步驟(6)所示。
1. 設定想要的裝置名稱，然後按一下&#x200B;**註冊**。

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. 按一下&#x200B;**完成**&#x200B;以完成註冊程式。

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >**註冊新裝置**&#x200B;可讓您註冊新裝置。
   >
   >**指派顯示區**&#x200B;可讓您直接將裝置新增至顯示區。

   如果您按一下&#x200B;**完成**，請將裝置指派給顯示器。

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >若要進一步瞭解如何建立和管理Screens專案的顯示器，請參閱[建立和管理顯示器](managing-displays.md)。

### 將裝置指派給顯示器 {#assigning-device-to-a-display}

如果您尚未將裝置指派給顯示區，請依照下列步驟，將裝置指派給AEM Screens專案中的顯示區：

1. 按一下裝置，然後按一下動作列中的&#x200B;**指派裝置**。

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. 按一下&#x200B;**顯示/裝置設定路徑**&#x200B;中的顯示路徑。

   ![screen_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. 按一下路徑時，請按一下&#x200B;**指派**。

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. 裝置指派成功後，按一下&#x200B;**完成**，如下圖所示。

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   您也可以選取&#x200B;**完成**&#x200B;來檢視顯示儀表板。

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## 從「裝置管理員」搜尋裝置 {#search-device}

將裝置註冊到播放器後，您就可以從「裝置管理員」UI檢視所有裝置。

1. 從您的AEM Screens專案導覽至裝置管理員UI，例如&#x200B;**DemoScreens** > **裝置**。

1. 按一下&#x200B;**裝置**&#x200B;資料夾，然後從動作列按一下&#x200B;**裝置管理員**。

   ![影像](/help/user-guide/assets/device-manager/device-manager-1.png)

1. 已註冊裝置的清單隨即顯示。

1. 如果您的註冊裝置清單很長，現在可以使用動作列的搜尋圖示進行搜尋

   ![影像](/help/user-guide/assets/device-manager/device-manager-2.png)

   或，

   選取`/` （正斜線）以叫用搜尋功能。

   ![影像](/help/user-guide/assets/device-manager/device-manager-3.png)


### 搜尋功能的限制 {#limitations}

* 使用者可以搜尋&#x200B;*裝置識別碼*&#x200B;或&#x200B;*裝置名稱*&#x200B;中的任何文字。

  >[!NOTE]
  >建議您以多個單字（例如&#x200B;*`Boston Store Lobby`*）來建立裝置名稱，而非以單一&#x200B;*`BostonStoreLobby`*&#x200B;來建立。

* 如果您已建立&#x200B;*`Boston Store Lobby`*&#x200B;之類的裝置名稱，它會搜尋任何單字&#x200B;*`boston`*、*`store`*&#x200B;或&#x200B;*`lobby`*。 但是，如果裝置名稱為&#x200B;*`BostonStoreLobby`*，則搜尋&#x200B;*`boston`*&#x200B;不會顯示任何結果。

* 萬用字元`*`支援搜尋。 如果您想要尋找名稱以&#x200B;*`boston`*&#x200B;開頭的所有裝置，可以使用*`boston`**。

* 如果裝置名稱為&#x200B;*`BostonStoreLobby`*&#x200B;且搜尋&#x200B;*`boston`*&#x200B;未傳回結果，則在搜尋條件中使用&#x200B;*`boston`**會傳回結果。

## 裝置註冊的限制 {#limitations-on-device-registration}

系統範圍的使用者密碼限制可能會導致裝置註冊失敗。 裝置註冊會使用隨機產生的密碼來建立裝置使用者。

如果&#x200B;*AuthorizableActionProvider*&#x200B;設定限制密碼，建立裝置使用者可能會失敗。

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

若要深入瞭解AEM Screens Player，請參閱[AEM Screens Player](working-with-screens-player.md)。

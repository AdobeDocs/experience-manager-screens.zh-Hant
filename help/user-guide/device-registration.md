---
title: 裝置註冊
seo-title: 裝置註冊
description: 本頁面說明AEM Screens專案中的裝置註冊程式。
seo-description: 本頁面說明AEM Screens專案中的裝置註冊程式。
uuid: 5365e506-1641-4a0c-b34d-c39da02f700b
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 523084f6-bd71-4daf-95b7-fc4c481f76dc
docset: aem65
translation-type: tm+mt
source-git-commit: 6731c984122083ff340eda690452729c0b846fb5
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 1%

---


# 裝置註冊 {#device-registration}

下頁說明AEM Screens專案中的裝置註冊程式。

## 註冊設備{#registering-a-device}

裝置註冊程式是在2部不同的電腦上完成：

* 要註冊的實際設備，例如您的標牌展示
* 用於註冊您裝置的AEM伺服器

>[!NOTE]
>
>在您從[AEM 6.4 Player下載](https://download.macromedia.com/screens/)頁面下載最新的Windows Player(*.exe*)後，請依照播放器上的步驟完成臨機安裝：
>
>1. 長按左上角以開啟管理面板。
>1. 從左側動作功能表導覽至「設定」**Configuration**，然後在&#x200B;**Server**&#x200B;中輸入AEM例項的位置位址，然後按一下「儲存」**。**
>1. 按一下左側操作菜單中的&#x200B;**註冊**&#x200B;連結和以下步驟以完成設備註冊過程。

>



![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. 在您的裝置上啟動AEM Screens Player。 會顯示註冊UI。

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. 在AEM中，導覽至專案的&#x200B;**Devices**&#x200B;資料夾。

   >[!NOTE]
   >
   >若要取得有關在AEM儀表板中建立新畫面專案的詳細資訊，請參閱[建立和管理畫面專案](creating-a-screens-project.md)。

1. 點選／按一下動作列中的&#x200B;**「裝置管理員**」按鈕。

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. 點選／按一下右上角的&#x200B;**裝置註冊**&#x200B;按鈕。

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. 選擇所需的設備（與步驟1相同），然後點選／按一下「Register Device（註冊設備）」**。**

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. 在AEM中，請等候裝置傳送其註冊代碼。

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. 在您的裝置中，檢查&#x200B;**註冊代碼**。

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. 如果兩部電腦的&#x200B;**註冊代碼**&#x200B;都相同，請點選／按一下AEM中的&#x200B;**驗證**&#x200B;按鈕，如步驟(6)所示。
1. 設定所要的裝置名稱，然後按一下「註冊&#x200B;**」。**

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. 點選／按一下「完成&#x200B;**」以完成註冊程式。**

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >**註冊新**&#x200B;允許您註冊新設備。
   >
   >**指派顯示**&#x200B;可讓您直接將裝置新增至顯示器。

   如果按一下&#x200B;**完成**，則需要將設備分配給顯示器。

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >若要進一步瞭解如何建立和管理螢幕專案的顯示，請參閱[建立和管理顯示](managing-displays.md)。

### 將設備分配給顯示器{#assigning-device-to-a-display}

如果您尚未將裝置指派給顯示器，請依照下列步驟，將裝置指派給AEM Screens專案中的顯示器：

1. 選擇設備，然後從操作欄中按一下「分配設備」。****

   ![screen_shot_2018-11-26at11026am](assets/screen_shot_2018-11-26at111026am.png)

1. 在&#x200B;**顯示／設備配置路徑**&#x200B;中選擇顯示路徑。

   ![screen_shot_2018-11-26at11252am](assets/screen_shot_2018-11-26at111252am.png)

1. 選擇路徑時，按一下&#x200B;**Assign**。

   ![screen_shot_2018-11-26at11722am](assets/screen_shot_2018-11-26at111722am.png)

1. 成功分配設備後，按一下&#x200B;**完成** ，如下圖所示。

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   此外，您還可以按一下「完成&#x200B;**」來檢視顯示控制面板。**

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

### 從設備管理器{#search-device}搜索設備

在您將裝置註冊到播放器後，您就可以從「裝置管理員」UI檢視所有裝置。

1. 從您的AEM Screens專案導覽至「裝置管理員UI」，例如&#x200B;**DemoScreens** —> **Devices**。

1. 選擇&#x200B;**Devices**&#x200B;資料夾，然後從操作欄按一下&#x200B;**Device Manager**。

   ![影像](/help/user-guide/assets/device-manager/device-manager-1.png)

1. 將顯示已註冊設備的清單。

1. 如果您有一長串已註冊的裝置清單，現在可以使用動作列中的搜尋圖示來搜尋

   ![影像](/help/user-guide/assets/device-manager/device-manager-2.png)

   或,

   按一下`/`（正斜線）以叫用搜尋功能。

   ![影像](/help/user-guide/assets/device-manager/device-manager-3.png)


#### 搜尋功能限制{#limitations}

* 用戶將能夠搜索&#x200B;*設備ID*&#x200B;或&#x200B;*設備名稱*&#x200B;中存在的任何字。

   >[!NOTE]
   >建議您以多個字詞建立裝置名稱，例如&#x200B;*Boston Store Lobby*，而非單一&#x200B;*BostonStoreLobby*。

* 如果您建立裝置名稱，例如&#x200B;*Boston Store Lobby*，它允許搜尋任何字詞&#x200B;*boston*、*store*&#x200B;或&#x200B;*lobby*，但若裝置名稱稱為&#x200B;*BostonStoreLobby*&#x200B;搜尋&#x200B;*boston*&#x200B;將不顯示結果。

* 萬用字元，`*`支援搜尋。 如果您想要尋找所有名稱為&#x200B;*boston*&#x200B;的裝置，則可使用&#x200B;*boston**。

* 如果裝置名稱為&#x200B;*BostonStoreLobby*，而搜尋&#x200B;*boston*&#x200B;將不會傳回結果，而是在搜尋准則中使用&#x200B;*boston**來傳回結果。

## 設備註冊限制{#limitations-on-device-registration}

系統範圍的用戶密碼限制可能導致設備註冊失敗。 設備註冊使用隨機生成的口令來建立設備用戶。

如果密碼受&#x200B;*AuthorizableActionProvider*&#x200B;組態的限制，建立裝置使用者可能會失敗。

>[!NOTE]
>
>目前產生的隨機密碼由36個ASCII字元組成，範圍從33到122個（幾乎包含所有特殊字元）。

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### 其他資源 {#additional-resources}

若要瞭解AEM Screens Player，請參閱[AEM Screens Player](working-with-screens-player.md)。

---
title: 裝置註冊
seo-title: Device Registration
description: 本頁介紹AEM Screens項目中的設備註冊過程。
seo-description: This page describes the device registration process in an AEM Screens project.
uuid: 5365e506-1641-4a0c-b34d-c39da02f700b
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 523084f6-bd71-4daf-95b7-fc4c481f76dc
docset: aem65
feature: Administering Screens, Device Registration
role: Admin
level: Intermediate
exl-id: b2d3a2cd-263f-4142-80da-29ce54cbf391
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 1%

---

# 裝置註冊 {#device-registration}

下頁介紹了AEM Screens項目中的設備註冊過程。

## 註冊設備 {#registering-a-device}

設備註冊過程在兩台獨立的電腦上完成：

* 要註冊的實際設備，例如標牌顯示
* 用AEM於註冊設備的伺服器

>[!NOTE]
>
>下載最新的Windows Player(*.exe*) [6AEM.4播放器下載](https://download.macromedia.com/screens/) 頁，按照播放器上的步驟完成即席安裝：
>
>1. 長按左上角以開啟管理面板。
>1. 導航到 **配置** 從左側操作菜單中，輸入實例的位AEM置地址 **伺服器** 按一下 **保存**。
>1. 按一下 **註冊** 從左側操作菜單和下面的步驟連結，以完成設備註冊過程。

>


![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. 在你的設備上，啟動AEM Screens播放器。 將顯示註冊UI。

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. 在AEM中，導航到 **設備** 資料夾。

   >[!NOTE]
   >
   >要獲取有關在儀表板中為螢幕建立新項目的詳細信AEM息，請參閱 [建立和管理螢幕項目](creating-a-screens-project.md)。

1. 點擊/按一下 **設備管理器** 按鈕。

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. 點擊/按一下 **設備註冊** 按鈕。

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. 選擇所需設備（與步驟1相同），然後點擊/按一下 **寄存器設備**。

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. 在AEM中，等待設備發送其註冊代碼。

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. 在設備中，檢查 **註冊代碼**。

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. 如果 **註冊代碼** 在兩台電腦上都相同，點擊/按一下 **驗證** 按鈕，AEM如步驟(6)所示。
1. 設定設備所需的名稱，然後按一下 **註冊**。

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. 點擊/按一下 **完成** 完成註冊過程。

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >的 **註冊新建** 允許您註冊新設備。
   >
   >的 **分配顯示** 允許您直接將設備添加到顯示器。

   如果按一下 **完成**，您需要將設備指定給顯示器。

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >要瞭解有關為螢幕項目建立和管理顯示器的詳細資訊，請參閱 [建立和管理顯示](managing-displays.md)。

### 將設備分配給顯示器 {#assigning-device-to-a-display}

如果尚未將設備分配給顯示器，請按照以下步驟將設備分配給您的AEM Screens項目中的顯示器：

1. 選擇設備並按一下 **分配設備** 按鈕。

   ![screen_shot_2018-11-26at11026am](assets/screen_shot_2018-11-26at111026am.png)

1. 選擇中顯示的路徑 **顯示/設備配置路徑**。

   ![screen_shot_2018-11-26at11252am](assets/screen_shot_2018-11-26at111252am.png)

1. 按一下 **分配** 的子菜單。

   ![screen_shot_2018-11-26at11722am](assets/screen_shot_2018-11-26at111722am.png)

1. 按一下 **完成** 成功分配設備後，如下圖所示。

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   此外，您還可以在按一下 **完成**。

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## 從設備管理器中搜索設備 {#search-device}

將設備註冊到播放器後，您可以從設備管理器UI中查看所有設備。

1. 例如，從您的AEM Screens項目導航到「設備管理器」UI **演示螢幕** —> **設備**。

1. 選擇 **設備** 資料夾，然後按一下 **設備管理器** 按鈕。

   ![影像](/help/user-guide/assets/device-manager/device-manager-1.png)

1. 將顯示已註冊設備的清單。

1. 如果您有一個已註冊設備的長清單，則現在可以使用操作欄中的搜索表徵圖進行搜索

   ![影像](/help/user-guide/assets/device-manager/device-manager-2.png)

   或,

   按一下 `/` （正斜線）調用搜索功能。

   ![影像](/help/user-guide/assets/device-manager/device-manager-3.png)


### 搜索功能的限制 {#limitations}

* 用戶將能夠搜索 *設備ID* 或 *設備名稱*。

   >[!NOTE]
   >建議您用多個單詞建立設備名稱，如 *波士頓商店大堂* 而不是一個 *波士頓商店大堂*。

* 如果建立設備名稱，如 *波士頓商店大堂*，它允許搜索任何單詞 *波士頓*。 *商店* 或 *大廳* 但如果設備名稱為 *波士頓商店大堂* 搜索 *波士頓* 不會顯示結果。

* 野牌， `*` 支援搜索。 以防萬一，您要查找所有名稱以 *波士頓*，您可以使用 *波士頓**。

* 如果設備名稱為 *波士頓商店大堂* 和搜索 *波士頓* 將不返回結果，而是使用 *波士頓**在搜索條件中將返回結果。

## 設備註冊限制 {#limitations-on-device-registration}

系統範圍的用戶密碼限制可能會導致設備註冊失敗。 設備註冊使用隨機生成的口令來建立設備用戶。

如果密碼受 *可授權的ActionProvider* 配置，建立設備用戶可能失敗。

>[!NOTE]
>
>當前生成的隨機密碼由36個ASCII字元組成，範圍從33到122（幾乎包括所有特殊字元）。

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### 其他資源 {#additional-resources}

要瞭解AEM Screens玩家，請參閱 [AEM Screens選手](working-with-screens-player.md)。

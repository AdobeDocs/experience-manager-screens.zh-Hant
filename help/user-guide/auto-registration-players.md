---
title: 玩家自動註冊
seo-title: Auto Registration of Players
description: 按照本頁瞭解AMS/On-Prem螢幕的玩家自動註冊。
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# 玩家自動註冊 {#auto-registration}

手動批量註冊數千個玩家會變得非常繁瑣，並增加時間和成本。 為簡化此過程，批量註冊功能允許您指定可通過配置檔案或移動設備管理(MDM)解決方案AEM配置到播放器中的預共用密鑰。

## 實現玩家自動註冊 {#bulk-registering-implementation}

按照以下步驟實施玩家自動註冊：

1. 登錄到實AEM例並選擇螢幕AEM項目並按一下 **屬性** 按鈕。
1. 選擇 **高級** 頁籤 **設備註冊** 的子菜單。

1. 在中指定自動註冊代碼 **批量註冊代碼** 欄位和中的可選預設顯示 **預設顯示分配** 分配給自動註冊的播放器。
   >[!NOTE]
   >輸入您選擇的代碼，並根據需要選擇預設顯示。

   ![影像](/help/user-guide/assets/auto-registration/auto-register1.png)
1. 使用MDM或配置JSON檔案為玩家設定相應的伺服器URL和註冊代碼。

   >[!NOTE]
   >有關詳細資訊，請參閱作業系統(OS)的特定播放器的實施頁。 您還可以使用管理員UI輸入註冊代碼。

1. 如果 `registrationKey` 屬性與中配置的屬AEM性匹配，播放器將自動註冊自身，如果配置了預設顯示，則內容將下載並播放。

   ![影像](/help/user-guide/assets/auto-registration/auto-register2.png)

## 安全最佳做法 {#security-best-practices}

請按照以下部分來考慮一些安全方面的最佳做法：

* 要確保註冊代碼不受損壞，請在啟動批量注AEM冊之前配置該代碼，並在完成後清除該欄位並保存AEM在中。

* 可以配置路徑 `/bin/screens/registration` 只能從已知IP範圍訪問。

* 請考慮使用MDM為播放器配置。

* 始終使用 `HTTPS` 不 `HTTP` 與玩家通信AEM。

   >[!NOTE]
   >預設顯示分配當前僅適用於批量註冊，而不適用於沒有註冊代碼的手動註冊。

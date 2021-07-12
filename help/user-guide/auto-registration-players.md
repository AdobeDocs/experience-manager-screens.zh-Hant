---
title: 播放器自動註冊
seo-title: 播放器自動註冊
description: 請詳閱本頁，了解使用AMS/內部螢幕自動註冊播放器。
feature: 管理螢幕、播放器
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# 播放器自動註冊 {#auto-registration}

手動大量註冊數千個播放器可能會變得非常麻煩，並增加時間和成本。 為簡化此過程，批量註冊功能允許您在AEM中指定預共用密鑰，該密鑰可以通過配置檔案或移動設備管理(MDM)解決方案被配置到播放器中。

## 實作播放器的自動註冊 {#bulk-registering-implementation}

請依照下列步驟，實作播放器的自動註冊：

1. 登入您的AEM例項，並選取您的AEM Screens專案，然後從動作列按一下「屬性&#x200B;****」。
1. 選擇&#x200B;**Advanced**&#x200B;頁簽以查看&#x200B;**Device registration**&#x200B;部分。

1. 在&#x200B;**批量註冊代碼**&#x200B;欄位中指定自動註冊代碼，並在&#x200B;**預設顯示分配**&#x200B;中指定可選預設顯示，以分配給自動註冊的播放器。
   >[!NOTE]
   >輸入您選擇的程式碼，並視需要選取預設顯示。

   ![影像](/help/user-guide/assets/auto-registration/auto-register1.png)
1. 使用MDM或配置JSON檔案，將您的播放器配置為適當的伺服器URL和註冊代碼。

   >[!NOTE]
   >如需詳細資訊，請參閱作業系統(OS)之特定播放器的實作頁面。 您也可以使用管理員UI來輸入註冊代碼。

1. 如果`registrationKey`屬性符合AEM中設定的屬性，播放器會自動註冊本身，而如果已設定預設顯示，該內容將下載並播放。

   ![影像](/help/user-guide/assets/auto-registration/auto-register2.png)

## 安全性最佳實務 {#security-best-practices}

請依照下節，考慮安全性的幾項最佳實務：

* 若要確保註冊代碼不會受損，請在開始大量註冊前於AEM中設定程式碼，並在完成後，請清除該欄位並儲存至AEM。

* 您可以將路徑`/bin/screens/registration`設定為僅可從已知IP範圍存取。

* 請考慮使用MDM來為播放器配置配置。

* 使用`HTTPS`而非`HTTP`來與AEM進行播放器通訊。

   >[!NOTE]
   >預設顯示分配當前僅適用於批量註冊，而不適用於沒有註冊代碼的手動註冊。

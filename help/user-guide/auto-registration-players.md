---
title: 播放器的自動註冊
seo-title: 播放器的自動註冊
description: 請依照本頁瞭解使用AMS/預備畫面自動註冊播放器。
feature: Administering Screens, Players
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# 播放器自動註冊{#auto-registration}

大量手動註冊數千個播放器會變得十分麻煩，並增加時間和成本。 為簡化此程式，批量註冊功能允許您指定預共用密鑰，該密鑰可AEM通過配置檔案或移動設備管理(MDM)解決方案設定到播放器中。

## 實作播放器的自動註冊{#bulk-registering-implementation}

請依照下列步驟來實作播放器的自動註冊：

1. 登入您AEM的例項並選AEM取您的畫面專案，然後從動作列按一下「屬性&#x200B;****」。
1. 選擇&#x200B;**Advanced**&#x200B;標籤以查看&#x200B;**Device registration**&#x200B;部分。

1. 在&#x200B;**大量註冊代碼**&#x200B;欄位中指定自動註冊代碼，並在&#x200B;**預設顯示指派**&#x200B;中指定選用的預設顯示，以指派給自動註冊的播放器。
   >[!NOTE]
   >輸入您選擇的程式碼，並視需要選取預設顯示畫面。

   ![影像](/help/user-guide/assets/auto-registration/auto-register1.png)
1. 使用MDM或設定JSON檔案，為您的播放器布建適當的伺服器URL和註冊碼。

   >[!NOTE]
   >如需詳細資訊，請參閱您作業系統(OS)之特定播放器的實施頁面。 您也可以使用管理員UI輸入註冊代碼。

1. 如果`registrationKey`屬性符合中設定的屬性AEM，則播放器會自動註冊自己，如果設定了預設顯示，則會下載並播放該內容。

   ![影像](/help/user-guide/assets/auto-registration/auto-register2.png)

## 安全性最佳實踐{#security-best-practices}

請遵循下節，以考慮安全性的一些最佳做法：

* 為確保註冊代碼不受影響，請在啟動大量註冊之AEM前和完成時，在中配置代碼，請清除該欄位並保存AEM。

* 您可以將路徑`/bin/screens/registration`設定為只能從已知IP範圍存取。

* 考慮使用MDM為播放器配置配置。

* 使用`HTTPS`而非`HTTP`來與播放器通訊AEM。

   >[!NOTE]
   >預設顯示指派目前僅適用於大量註冊，而非無註冊代碼的手動註冊。
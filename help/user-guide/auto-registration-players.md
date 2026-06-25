---
title: 自動註冊播放器
description: 請依照本頁面的說明進行，以便瞭解如何使用AMS/內部部署Screens自動註冊播放器。
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
TQID: https://experienceleague.adobe.com/uvCRS49L6CQbah4AKFwRdhGN-pvKnTWtNMN8CnFojIQ
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 388
ht-degree: 0%

---

# 自動註冊播放器 {#auto-registration}

>[!IMPORTANT]
>此內容對AEM內部部署/AMS （AEM 6.5LTS和AEM 6.5）有效。 如需AEM as a Cloud Service Screens內容，請參閱[AEM as a Cloud Service指南](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)。

手動大量註冊數千個播放器可能會變得繁瑣並增加時間和成本。 為簡化此程式，大量註冊功能可讓您在AEM中指定預先共用金鑰，可透過設定檔案或行動裝置管理(MDM)解決方案將其布建至播放器。

## 實作播放器自動註冊 {#bulk-registering-implementation}

請依照下列步驟實作播放器的自動註冊：

1. 登入您的AEM執行個體，然後按一下您的AEM Screens專案，再按一下動作列中的&#x200B;**屬性**。
1. 按一下&#x200B;**進階**&#x200B;標籤，以便檢視&#x200B;**裝置註冊**&#x200B;區段。

1. 在&#x200B;**大量註冊代碼**&#x200B;欄位中指定自動註冊代碼。 然後在&#x200B;**預設顯示指派**&#x200B;中選取預設顯示，以指派給自動註冊的播放器。

   >[!NOTE]
   >輸入您選擇的程式碼，並視需要按一下預設顯示。

   ![影像](/help/user-guide/assets/auto-registration/auto-register1.png)
1. 使用MDM或設定JSON檔案為播放器布建適當的伺服器URL和註冊代碼。

   >[!NOTE]
   >如需詳細資訊，請參閱作業系統(OS)專用播放器的實作頁面。 您也可以使用管理員UI來輸入註冊代碼。

1. 如果`registrationKey`屬性符合AEM中設定的屬性，播放器會自動註冊本身，而且如果設定了預設顯示，則會下載並播放該內容。

   ![影像](/help/user-guide/assets/auto-registration/auto-register2.png)

## 安全性最佳實務 {#security-best-practices}

請參考以下章節，以考量安全性的一些最佳實務：

* 確保註冊代碼不會受損 — 在開始大量註冊之前，先在AEM中設定代碼，完成後，清除該欄位，並儲存在AEM中。

* 您可以設定路徑`/bin/screens/registration`，使其只能從已知的IP範圍存取（如果可能）。

* 考慮使用MDM以設定布建播放器。

* 永遠使用`HTTPS`而非`HTTP`與AEM進行播放器通訊。

  >[!NOTE]
  >預設顯示指派目前僅適用於大量註冊。 當註冊代碼不可用時，它無法用於手動註冊。

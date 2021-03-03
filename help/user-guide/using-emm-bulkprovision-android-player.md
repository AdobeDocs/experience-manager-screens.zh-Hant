---
title: 使用MDM或EMM大量布建Android Player
seo-title: 使用EMM或MDM大量布建Android Player
description: 請依照本頁瞭解使用EMM或MDM大量布建Android Player的相關資訊
translation-type: tm+mt
source-git-commit: 5f8938bfd092197391aefcd2d730d47fa06c214d
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# 使用企業行動管理{#bulk-provisioning}大量布建Android Player

當大量部署Android播放器時，手動註冊每個播放器將變得很麻煩AEM。 強烈建議您使用EMM（企業行動力管理）解決方案，例如VMWare Airwatch、MobileIron或Samsung Knox，以遠端布建及管理您的部署。 AEM ScreensAndroid播放器支援業界標準EMM Appconfig，允許遠端布建。

## 使用企業行動管理{#implementation}實作Android Player的大量布建

請依照下列步驟，在Android Player中允許大量布建：

1. 請確定您的Android裝置支援Google Play服務。
1. 使用您最愛的支援Appconfig的EMM解決方案註冊您的Android播放器裝置。
1. 登入您的EMM主控台，從Google Play拉出AEM Screens播放器應用程式。
1. 選擇受管理的配置（或相關選項）。
1. 您現在應該會看到可設定的播放器選項清單（例如伺服器和大量註冊碼）。
1. 配置這些參數，並將策略保存並部署到設備。

   >[!NOTE]
   >設備應接收應用程式以及配置，並指向具有選定配置AEM的正確伺服器。 如果您選擇設定大量註冊代碼，並維持其與中設定的相同AEM，則播放器應能自動註冊自己。 如果您已設定預設顯示，它也可以下載並顯示某些預設內容（稍後可視您的方便而變更）。

此外，您應洽詢您的EMM廠商有關AppConfig支援的資訊。 最常用的例如[VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、[Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)、[SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)、[Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)、[IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)和[Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)支援此業界標準。



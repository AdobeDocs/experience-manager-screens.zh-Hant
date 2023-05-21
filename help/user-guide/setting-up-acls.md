---
title: 設定ACL
seo-title: Setting up ACLs
description: 按照本頁瞭解如何使用ACL分離項目，以便每個個人或團隊處理其自己的項目。
seo-description: Follow this page to learn how to segregate projects using ACLs so that each individual or team handles their own project.
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 2%

---

# 設定ACL {#setting-up-acls}

下節介紹如何使用ACL分離項目，以便每個個人或團隊處理其自己的項目。

作為AEM管理員，您需要確保項目的團隊成員不會干擾其他項目，並且每個用戶都根據項目要求分配特定角色。

## 設定權限 {#setting-up-permissions}

以下步驟概括了為項目設定ACL的過程：

1. 登錄AEM並導航至 **工具** > **安全**。

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. 按一下 **組** 並輸入ID（例如，Acme）。

   或者，使用此連結， `http://localhost:4502/libs/granite/security/content/groupadmin.html`。

   隨後，按一下 **保存**。

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. 選擇 **撰稿人** 並按兩下它。

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. 添加 **埃克** （您建立的項目） **將成員添加到組**。 按一下「**儲存**」。

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >如果希望項目團隊成員註冊玩家（涉及為每個玩家建立用戶），請查找組用戶管理員並將ACME組添加到用戶管理員

1. 添加將在 **埃克** 項目到 **埃克** 組。

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. 設定組的權限 **埃克** 使用 `(http://localhost:4502/useradmin)`。

   選擇組 **埃克** 並按一下 **權限**。

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### 權限 {#permissions}

下表匯總了具有項目級別權限的路徑：

| **路徑** | **權限** | **說明** |
|---|---|---|
| `/apps/<project>` | 讀取 | 提供對項目檔案（如果適用）的訪問 |
| `/content/dam/<project>` | 全部 | 提供在DAM中儲存項目資產（如影像或視頻）的權限 |
| `/content/screens/<project>` | 全部 | 刪除對/content/screens下所有其他項目的訪問 |
| `/content/screens/svc` | 讀取 | 提供對註冊服務的訪問 |
| `/libs/screens` | 讀取 | 提供對DCC的訪問 |
| `/var/contentsync/content/screens/` | 全部 | 允許更新項目的離線內容 |

>[!NOTE]
>
>在某些情況下，您可以將作者功能（如管理資產和建立渠道）與管理功能（如註冊玩家）分開。 在這種情況下，建立兩個組並將作者組添加到參與者，將管理組添加到參與者和用戶管理員。

### 建立組 {#creating-groups}

建立新項目還應建立分配了基本權限集的預設用戶組。 您應將權限擴展到我們對AEM Screens具有的典型角色。

例如，您可以建立以下項目特定組：

* 螢幕項目管理員
* 螢幕項目操作員（註冊玩家，並管理位置和設備）
* 螢幕項目用戶（處理頻道、計畫和頻道分配）

下表匯總了具有AEM Screens項目說明和權限的組：

<table>
 <tbody>
  <tr>
   <td><strong>組名稱</strong></td>
   <td><strong>說明</strong></td>
   <td><strong>權限</strong></td>
  </tr>
  <tr>
   <td>螢幕管理員<br /> <em>螢幕管理員</em></td>
   <td>對AEM Screens權能的管理級訪問</td>
   <td>
    <ul>
     <li>參與者成員</li>
     <li>OF用戶 — 管理員成員</li>
     <li>所有/內容/螢幕</li>
     <li>所有/內容/資料庫</li>
     <li>所有/內容/體驗片段</li>
     <li>所有/etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>螢幕用戶<br /> <em>螢幕用戶</em></td>
   <td>建立和更新渠道和計畫並分配給AEM Screens的地點</td>
   <td>
    <ul>
     <li>參與者成員</li>
     <li>&lt;project&gt; /內容/螢幕</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience片段</li>
    </ul> </td>
  </tr>
  <tr>
   <td>螢幕運算子<br /> <em>螢幕運算子</em></td>
   <td>在AEM Screens建立和更新位置結構和註冊玩家</td>
   <td>
    <ul>
     <li>參與者成員</li>
     <li>jcr：所有/home/users/screens</li>
     <li>jcr：所有/home/groups/screens</li>
     <li>&lt;project&gt; /內容/螢幕</li>
    </ul> </td>
  </tr>
  <tr>
   <td>螢幕播放器<br /> <em>螢幕&lt;project&gt; — 設備</em></td>
   <td>自動將所有玩家和所有玩家/設備分組為參與者的成員。</td>
   <td><p> 參與者成員</p> </td>
  </tr>
 </tbody>
</table>

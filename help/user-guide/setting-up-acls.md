---
title: 設定ACL
seo-title: 設定ACL
description: 請參照本頁面，了解如何使用ACL分隔專案，讓每個人或團隊都能處理各自的專案。
seo-description: 請參照本頁面，了解如何使用ACL分隔專案，讓每個人或團隊都能處理各自的專案。
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
feature: 管理畫面
role: Administrator
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 1%

---

# 設定ACL {#setting-up-acls}

以下章節說明如何使用ACL分隔專案，讓每個人或團隊都能處理各自的專案。

身為AEM管理員，您必須確保專案的團隊成員不會干預其他專案，且每位使用者都會根據專案需求獲得特定角色。

## 設定權限{#setting-up-permissions}

以下步驟概述為項目設定ACL的過程：

1. 登入AEM並導覽至&#x200B;**工具** > **安全性**。

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. 按一下「**群組**」並輸入ID（例如Acme）。

   或者，使用此連結`http://localhost:4502/libs/granite/security/content/groupadmin.html`。

   隨後，按一下&#x200B;**Save**。

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. 從清單中選擇&#x200B;**貢獻者**，然後按兩下。

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. 將&#x200B;**Acme**（您建立的專案）新增至&#x200B;**新增成員至群組**。 按一下「**儲存**」。

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >如果您希望項目團隊成員註冊玩家（包括為每個玩家建立用戶），請找到組用戶管理員，然後將ACME組添加給用戶管理員

1. 將將&#x200B;**Acme**&#x200B;專案的所有使用者新增至&#x200B;**Acme**&#x200B;群組。

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. 使用此`(http://localhost:4502/useradmin)`設定群組&#x200B;**Acme**&#x200B;的權限。

   選取群組&#x200B;**Acme**，然後按一下&#x200B;**permissions**。

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### 權限 {#permissions}

下表匯總了具有項目級別權限的路徑：

| **路徑** | **權限** | **說明** |
|---|---|---|
| `/apps/<project>` | 讀取 | 提供對項目檔案的訪問（如果適用） |
| `/content/dam/<project>` | 全部 | 提供在DAM中儲存影像或視訊等專案資產的存取權 |
| `/content/screens/<project>` | 全部 | 移除/content/screens底下所有其他專案的存取權 |
| `/content/screens/svc` | 讀取 | 提供對註冊服務的訪問 |
| `/libs/screens` | 讀取 | 提供DCC的存取權 |
| `/var/contentsync/content/screens/` | 全部 | 允許更新專案的離線內容 |

>[!NOTE]
>
>在某些情況下，您可以將製作功能（例如管理資產和建立管道）與管理功能（例如註冊播放器）區隔開來。 在這種情況下，請建立兩個群組，並將作者群組新增至貢獻者，並將管理員群組新增至貢獻者和使用者管理員。

### 建立組{#creating-groups}

建立新專案也應建立預設使用者群組，並指派基本權限集。 您應將權限延伸至我們對AEM Screens的典型角色。

例如，您可以建立下列專案特定群組：

* Screens專案管理員
* Screens專案運算子（註冊播放器，以及管理位置和裝置）
* Screens專案使用者（處理管道、排程和管道指派）

下表摘要具有AEM Screens專案說明和權限的群組：

<table>
 <tbody>
  <tr>
   <td><strong>群組名稱</strong></td>
   <td><strong>說明</strong></td>
   <td><strong>權限</strong></td>
  </tr>
  <tr>
   <td>Screens Admins<br /> <em>screens-admins</em></td>
   <td>AEM Screens功能的管理員層級存取</td>
   <td>
    <ul>
     <li>貢獻者成員</li>
     <li>用戶管理員成員</li>
     <li>所有/content/screens</li>
     <li>所有/content/dam</li>
     <li>所有/content/experience-fragments</li>
     <li>所有/etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens Users<br /> <em>screens-users</em></td>
   <td>建立和更新管道和排程，並指派至AEM Screens中的位置</td>
   <td>
    <ul>
     <li>貢獻者成員</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens運算子<br /> <em>screens-operators</em></td>
   <td>在AEM Screens中建立和更新位置結構及註冊播放器</td>
   <td>
    <ul>
     <li>貢獻者成員</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>螢幕播放器<br /> <em>screens-&lt;project&gt;-devices</em></td>
   <td>自動將所有播放器和所有播放器/裝置分組為貢獻者的成員。</td>
   <td><p> 貢獻者成員</p> </td>
  </tr>
 </tbody>
</table>

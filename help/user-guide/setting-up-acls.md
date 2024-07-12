---
title: 設定ACL
description: 瞭解如何使用ACL來分隔專案，以便每個個人或團隊處理自己的專案。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 2%

---

# 設定ACL {#setting-up-acls}

下節將說明如何使用ACL來分隔專案，以便每個個人或團隊處理自己的專案。

身為AEM管理員，您想要確保專案的團隊成員不會干預其他專案。 每個使用者都會根據專案需求獲派特定角色。

## 設定許可權 {#setting-up-permissions}

下列步驟摘要說明為專案設定ACL的程式：

1. 登入AEM並導覽至&#x200B;**工具** > **安全性**。

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. 按一下&#x200B;**群組**&#x200B;並輸入ID （例如Acme）。

   或者，使用此連結`http://localhost:4502/libs/granite/security/content/groupadmin.html`。

   接著，按一下&#x200B;**儲存**。

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. 按一下清單中的&#x200B;**參與者**，然後按兩下。

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. 將&#x200B;**Acme** （您建立的專案）新增至&#x200B;**新增成員至群組**。 按一下「**儲存**」。

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >如果您希望專案團隊成員註冊播放器（包括為每個播放器建立使用者），請尋找群組使用者管理員，並將ACME群組新增到使用者管理員

1. 將處理&#x200B;**Acme**&#x200B;專案的所有使用者新增至&#x200B;**Acme**&#x200B;群組。

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. 使用此`(http://localhost:4502/useradmin)`設定群組&#x200B;**Acme**&#x200B;的許可權。

   按一下群組&#x200B;**Acme**&#x200B;並按一下&#x200B;**許可權**。

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### 權限 {#permissions}

下表總結了具有專案層級許可權的路徑：

| **路徑** | **許可權** | **說明** |
|---|---|---|
| `/apps/<project>` | 讀取 | 提供專案檔案的存取權（如果適用）。 |
| `/content/dam/<project>` | 全部 | 提供在DAM中儲存專案資產（例如影像或影片）的存取權。 |
| `/content/screens/<project>` | 全部 | 移除/content/screens底下所有其他專案的存取權。 |
| `/content/screens/svc` | 讀取 | 提供註冊服務的存取權。 |
| `/libs/screens` | 讀取 | 提供DCC的存取權。 |
| `/var/contentsync/content/screens/` | 全部 | 協助您更新專案的離線內容。 |

>[!NOTE]
>
>有時候，您可以將作者功能（例如管理資產和建立管道）與管理功能（例如註冊播放器）分開。 在這種情況下，請建立兩個群組，並將作者群組新增至貢獻者，並將管理員群組新增至貢獻者和使用者管理員。

### 建立群組 {#creating-groups}

建立專案時，也應建立具有指派基本許可權集的預設使用者群組。 將許可權擴充至AEM Screens中定義的典型角色。

例如，您可以建立下列專案特定群組：

* Screens專案管理員
* Screens專案操作者（註冊播放器，以及管理位置和裝置）
* Screens專案使用者（處理頻道、時程表和頻道指派）

下表摘要列出具有AEM Screens專案說明和許可權的群組：

<table>
 <tbody>
  <tr>
   <td><strong>群組名稱</strong></td>
   <td><strong>說明</strong></td>
   <td><strong>權限</strong></td>
  </tr>
  <tr>
   <td>Screens管理員<br /> <em><code>screens-admins</code></em></td>
   <td>管理員層級存取AEM Screens功能</td>
   <td>
    <ul>
     <li>貢獻者成員</li>
     <li>使用者管理員成員</li>
     <li>所有/content/screens</li>
     <li>ALL /content/dam</li>
     <li>所有/content/experience-fragments</li>
     <li>所有/etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens使用者<br /> <em><code>screens-users</code></em></td>
   <td>在AEM Screens中建立和更新頻道和排程並指派至位置</td>
   <td>
    <ul>
     <li>貢獻者成員</li>
     <li><code>&lt;project&gt; /content/screens</code></li>
     <li><code>&lt;project&gt; /content/dam</code></li>
     <li><code>&lt;project&gt; /content/experience-fragments</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens運運算元<br /> <em><code>screens-operators</code></em></td>
   <td>在AEM Screens中建立和更新位置結構並註冊播放器</td>
   <td>
    <ul>
     <li>貢獻者成員</li>
     <li><code>jcr:all /home/users/screens</code></li>
     <li><code>jcr:all /home/groups/screens</code></li>
     <li><code>&lt;project&gt; /content/screens</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens Players<br /> <em><code>screens-&lt;project&gt;-devices</code></em></td>
   <td>所有播放器和所有播放器/裝置會自動成為貢獻者成員。</td>
   <td><p> 貢獻者成員</p> </td>
  </tr>
 </tbody>
</table>

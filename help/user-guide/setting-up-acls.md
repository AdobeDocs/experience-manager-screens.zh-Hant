---
title: 設定ACL
seo-title: 設定ACL
description: 請遵循本頁，瞭解如何使用ACL分離項目，使每個個人或團隊都能處理自己的項目。
seo-description: 請遵循本頁，瞭解如何使用ACL分離項目，使每個個人或團隊都能處理自己的項目。
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 設定ACL {#setting-up-acls}

下節將說明如何使用ACL分離項目，以便讓每個個人或團隊處理自己的項目。

身為AEM管理員，您需要確保專案的團隊成員不會干擾其他專案，而且每個使用者都會根據專案需求指派特定角色。

## 設定權限 {#setting-up-permissions}

以下步驟概括了為項目設定ACL的過程：

1. 登入AEM並導覽至「工 **具** &gt;安 **全性**」。

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. 按一 **下「群組** 」並輸入ID（例如Acme）。

   或者，使用此連結 `http://localhost:4502/libs/granite/security/content/groupadmin.html`。

   隨後，按一下「 **保存」**。

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. 從清單 **中選取** 「參與者」，然後按兩下它。

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. 將 **Acme** （您建立的專案）新增至 **「新增成員至群組」**。 按一下&#x200B;**「儲存」**。

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >如果您希望專案團隊成員註冊播放器（包括為每個播放器建立使用者），請尋找群組使用者管理員，並將ACME群組新增至使用者管理員

1. 將要處理 **Acme** Project的所有使用者新增至 **Acme** 群組。

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. 使用此項設定群組 **Acme** 的權限 `(http://localhost:4502/useradmin)`。

   選取群組 **Acme** ，然後按一下 **權限**。

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### 權限 {#permissions}

下表匯總了具有項目級別權限的路徑：

| **路徑** | **權限** | **說明** |
|---|---|---|
| `/apps/<project>` | 讀取 | 提供對專案檔案的存取權（如果適用） |
| `/content/dam/<project>` | 全部 | 可存取在DAM中儲存專案資產，例如影像或視訊 |
| `/content/screens/<project>` | 全部 | 移除/content/screens下所有其他專案的存取權 |
| `/content/screens/svc` | 讀取 | 提供註冊服務的存取權 |
| `/libs/screens` | 讀取 | 提供DCC的存取權 |
| `/var/contentsync/content/screens/` | 全部 | 允許更新專案的離線內容 |

>[!NOTE]
>
>在某些情況下，您可以將作者功能（例如管理資產和建立渠道）與管理功能（例如註冊播放器）分開。 在這種情況下，請建立兩個群組，並將作者群組新增至參與者，並將管理員群組新增至參與者和使用者管理員。

### 建立群組 {#creating-groups}

建立新專案時，也應建立指派基本權限集的預設使用者群組。 您應將權限延伸至我們對AEM畫面擁有的典型角色。

例如，您可以建立下列專案特定群組：

* 畫面專案管理員
* 畫面專案營運商（註冊播放器，以及管理位置和裝置）
* 畫面專案使用者（處理頻道、排程和頻道指派）

下表匯總了AEM Screens專案的說明和權限群組：

<table>
 <tbody>
  <tr>
   <td><strong>群組名稱</strong></td>
   <td><strong>說明</strong></td>
   <td><strong>權限</strong></td>
  </tr>
  <tr>
   <td>畫面管理員<br /> 畫 <em>面管理員</em></td>
   <td>AEM Screens功能的管理員層級存取</td>
   <td>
    <ul>
     <li>投稿人成員</li>
     <li>OF用戶管理員成員</li>
     <li>所有/content/screens</li>
     <li>所有/content/dam</li>
     <li>ALL /content/experience-fragments</li>
     <li>ALL /etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>畫面使用者<br /> 畫 <em>面使用者</em></td>
   <td>建立和更新頻道和排程，並指派至AEM畫面中的位置</td>
   <td>
    <ul>
     <li>投稿人成員</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>畫面營運商<br /> 畫 <em>面營運商</em></td>
   <td>在AEM Screens中建立和更新位置結構並註冊播放器</td>
   <td>
    <ul>
     <li>投稿人成員</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>螢幕播放<br /><em>器螢幕——我們——零售裝置</em></td>
   <td>將所有播放器和所有播放器／裝置自動分組為參與者的成員。</td>
   <td><p> 投稿人成員</p> </td>
  </tr>
 </tbody>
</table>

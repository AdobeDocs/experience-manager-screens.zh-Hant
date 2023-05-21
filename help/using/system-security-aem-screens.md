---
title: AEM Screens安全檢查表
seo-title: Security Checklist for AEM Screens
description: 該頁介紹了AEM Screens的安全檢查清單
seo-description: The page describes Security Checklist for AEM Screens
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 1%

---


# 系統安全注意事項AEM Screens {#security-checklist}

>[!IMPORTANT]
>這是內部Git資源。

本頁重點介紹AEM Screens的系統安全注意事項。


## AEM Screens安全白皮書 {#white-paper}

本節介紹白皮書。 （掛起的白皮書附件）


## AEM Screens安全常見問題 {#faqs-screens}

以下常見問題假定使用HTTPS作為播放器和伺服器之間的通信協定的經過驗證的註冊的播放器體AEM系結構。

### 常見問題1 {#faq1}

是否可以將播放器流量重新路由到惡意伺服器並指示下載和播放惡意媒體內容？

**答案**

不可能，因為HTTP連接標識連接的兩端並對其進行加密。 如果您試圖處於中間位置並攔截它，則您只看到加密內容，如果您試圖模擬伺服器，則播放器將拒絕您，因為您的證書不同。


### 常見問題2 {#faq2}

是否應使用HTTP或HTTP?

**答案**

使用HTTP。 如果你擔心安全，這是必備的。 利用HTTPs，玩家和伺服器之間的通信被加密，攔截或修改內容幾乎是不可能的。


### 常見問題3 {#faq3}

在內容下載中，是否存在對內容或散列的簽名？

**答案**

每個資產都由伺服器簽名(SHA)，然後由播放器驗證相同的散列以確保完整性。
如果哈希不匹配，我們將嘗試重新驗證3次。 3次嘗試後，我們認為download命令無效。


### 常見問題4 {#faq4}

伺服器AEM是否安全？

**答案**

答案4。 假設您在AMS上，我們會使用與站點或資產相同的功能來處理所有伺服器安全性。


### 常見問題5 {#faq5}

設備是否安全？

**答案**

理論上可以操縱身體受損的玩家來播放任何內容。 您也可以將播放器插出並插入USB/HDMI棒。

因此，建議將設備置於不可觸及的位置，優選在固定的容器中，並且電纜也固定。 還禁用任何IR-remote埠。

如果設備作業系統未定期更新，則可能會使作業系統暴露在安全漏洞中，並允許通過網路進行遠程攻擊。

>[!NOTE]
>
>建議使用適當的遠程更新和控制功能（遠程案頭、MDM解決方案等）來測試設備。 還建議使用專用網路，例如，不要暴露在公共WIFI中。


### 常見問題6 {#faq6}

駭客會如何試圖危害玩家？

**答案**

危害玩家設備的唯一方法是：

1. 危害DNS以模擬其主機名上的伺服器，
1. 妥協
   1. 模擬伺服器的證書伺服器端
   1. 設備並模擬證書客戶端

>[!IMPORTANT]
>即使設備已遭到破壞，您仍然可以輕鬆撤銷其憑據，以便它無法再連AEM接到。






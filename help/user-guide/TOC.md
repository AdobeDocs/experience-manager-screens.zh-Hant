---
cloud: experience-cloud
product: experience manager
audience: end-user
user-guide-title: Adobe Experience Manager Screens 說明
breadcrumb-title: AEM Screens 指南
user-guide-description: 了解如何使用數位簽署解決方案，輕鬆發佈動態的互動式數位體驗和互動。
feature-set: Experience Manager Screens
source-git-commit: 9d8b336c12d5e44beb831ba41f3df5031a6ca32d
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 14%

---


# AEM Screens 使用手冊 {#user-guide}

+ [螢幕簡介](aem-screens-introduction.md)
+ 概述和Kickstart指南 {#overview}
   + [Kickstart指南](kickstart-for-aem-screens.md)
   + [螢幕最佳做法指南](https://experienceleague.adobe.com/docs/experience-manager-screens/using/about-guide.html)
   + [關鍵術語](screens-glossary.md)
+ 數字標牌網路基礎 {#digital-signage-network}
   + [第1部分：項目角色和責任](project-roles-responsibilities.md)
   + [第二部分：項目範圍時的注意事項](project-considerations.md)
   + [第三部分：測試、POC、試運行和部署](testing-pocs-pilots-rollouts.md)
   + [第四部分：項目管理和部署](project-management-and-deployment.md)
   + [第五部分：支援注意事項](support-considerations.md)
+ 配置和管理 {#administering}
   + [螢幕伺服器配置](configuring-screens-introduction.md)
   + [設定Dispatcher配置](dispatcher-configurations-aem-screens.md)
   + [安裝 Screens 播放器](installing-screens-player.md)
   + [連接螢幕播放器](working-with-screens-player.md)
   + [裝置註冊](device-registration.md)
   + [設定ACL](setting-up-acls.md)
   + [AEM Screens安全檢查表](security-checklist.md)
   + [從ContentSync過渡到SmartSync](smartsync.md)
   + [從檔案新建項目導入程式](project-importer.md)
   + [將資料觸發器複製到發佈伺服器](replicating-data-triggers.md)
   + [配置螢幕複製代理](configure-screens-replication.md)
   + 客戶端特定注意事項 {#installing-client}
      + [Chrome OS播放器](implementing-chrome-os-player.md)
      + [使用Chrome Player作為故障診斷的擴展](using-chrome-player-as-an-extension.md)
      + [Android播放器](implementing-android-player.md)
      + [Windows播放器](implementing-windows-player.md)
      + [蒂森玩家](tizen-player.md)
      + [玩家自動註冊](auto-registration-players.md)
      + [使用遙控器](implementing-remote-control.md)
   + 作者發佈 {#author-publish}
      + [作者 — 發佈體系結構概述](author-publish-architecture-overview.md)
      + [配置作者和發佈](author-and-publish.md)
   + 與AEM Screens的分析整合 {#analytics-integration}
      + [Adobe Analytics 整合](adobe-analytics-integration-aem-screens.md)
      + [配置Adobe Analytics與AEM Screens](configuring-adobe-analytics-aem-screens.md)
+ 創作和使用案例示例 {#authoring}
   + 設定螢幕項目 {#setting-up-projects}
      + [建立和管理項目](creating-a-screens-project.md)
      + [建立和管理渠道](managing-channels.md)
      + [建立和管理顯示](managing-displays.md)
      + [建立和管理位置](managing-locations.md)
      + [建立和管理計畫](managing-schedules.md)
      + [管理設備](managing-devices.md)
      + 分配通道 {#assigning-channels}
         + [頻道指定任務](channel-assignment-latest-fp.md)
         + [渠道分配：舊AEM Screens功能包](channel-assignment.md)
   + 使用核心產品功能 {#product-features}
      + [文字重疊](text-overlay.md)
      + [批量離線更新](bulk-offline-update.md)
      + [AEM Screens通知服務](screens-notifications-service.md)
      + [使用體驗片段](experience-fragments-in-screens.md)
      + [資產級激活](asset-level-scheduling.md)
      + [通道級激活](channel-level-activation.md)
      + [建立和管理即時拷貝](managing-livecopy.md)
      + [建立視頻填充工作流](creating-a-video-padding-workflow.md)
      + [將元件添加到通道](adding-components-to-a-channel.md)
      + [嵌入序列](embedded-sequences.md)
      + [多區域佈局](multi-zone-layout-aem-screens.md)
      + [視頻格式副本](generating-renditions.md)
      + [動態內嵌序列](dynamic-embedded-sequences.md)
      + [通道級批量影像播放持續時間](channel-level-image-playback.md)
      + [命令同步](using-command-sync.md)
      + [使用資料觸發器創作](authoring-data-triggers.md)
      + [語音識別](voice-recognition.md)
      + [內容指派報表](content-assignment-report.md)
      + [影片的縮圖支援](thumbnail-support.md)
      + [在AEM Screens使用自適應格式副本](using-adaptive-renditions.md)
   + 管理內容更新 {#content-updates}
      + [按需內容更新](on-demand-content.md)
      + [內容即服務更新](content-update-as-a-service.md)
      + [使用螢幕啟動更新內容](launches.md)
   + 用例示例 {#use-case-examples}
      + [緊急通道](emergency-channel.md)
      + [旅行中心溫度激活](local-temperature-activation.md)
      + [酒店預訂激活](hospitality-reservation-activation.md)
      + [零售庫存目標激活](retail-inventory-activation.md)
      + [應用過渡](applying-transitions.md)
      + [多區域到單區域過渡](multizone-to-singlezone.md)
      + [一次性TakeOver通道](single-use-takeover-channel.md)
      + [永久使用接管渠道](perpetual-takeover-channel.md)
+ 開發人員和API資源 {#developing}
   + [REST API](rest-api.md)
   + [為AEM Screens開發定制元件](developing-custom-component-tutorial-develop.md)
   + [離線通道](offline-channels.md)
   + [擴展AEM Screens元件](extending-component-tutorial-develop.md)
   + [建立元件](creating-components.md)
   + [使用編輯器嵌入REACT應AEM用SPA程式並與AEM Screens分析整合](embedding-react-app.md)
   + [在AEM Screens配置ContextHub](configuring-context-hub.md)
   + [為多區域佈局建立自定義模板](creating-custom-templates-multizone-layouts.md)
   + [為文本覆蓋應用自定義品牌和樣式](custom-branding-text-overlays.md)
   + [自適應格式副本：體系結構概述和配置](/help/user-guide/adaptive-renditions.md)
+ 故障排除和常見問題 {#troubleshooting}
   + [AEM Screens常見問題](aem-screens-faqs.md)
   + [設備控制中心故障排除](monitoring-screens.md)
   + [視頻播放配置](troubleshoot-videos.md)
+ 發行說明 {#release-notes}
   + [功能包202204發行說明](release-notes-fp-202204.md)
   + [功能包202203發行說明](release-notes-fp-202203.md)
   + [功能包202112發行說明](release-notes-fp-202112.md)
   + [功能包202109發行說明](release-notes-fp-202109.md)
   + [功能包202105發行說明](release-notes-fp-202105.md)
   + [功能包202103發行說明](release-notes-fp-202103.md)
   + [功能包202011發行說明](release-notes-fp-202011.md)
   + [功能包202008發行說明](release-notes-fp-202008.md)
   + [功能包202004發行說明](release-notes-fp-202004.md)
   + [功能包202001發行說明](release-notes-fp-202001.md)
   + [功能包201909發行說明](release-notes-fp-201909.md)
   + [功能包201907發行說明](release-notes-fp-201907.md)
   + [功能包201905發行說明](screens-release-notes-fp-201905.md)
   + [功能包201812發行說明](release-notes-fp-201812.md)
   + [功能包201809發行說明](screens-release-notes.md)

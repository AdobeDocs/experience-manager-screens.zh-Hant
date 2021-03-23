---
cloud: experience-cloud
product: experience manager
audience: end-user
user-guide-title: Adobe Experience Manager Screens 說明
breadcrumb-title: AEM Screens 指南
user-guide-description: 了解如何使用數位簽署解決方案，輕鬆發佈動態的互動式數位體驗和互動。
feature-set: Experience Manager Screens
translation-type: tm+mt
source-git-commit: 5daa0cdcecc3ddb9c93033754a505ff54d59f886
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 13%

---


# AEM Screens 使用手冊 {#user-guide}

+ [螢幕簡介](aem-screens-introduction.md)
+ 概述和啟動指南{#overview}
   + [Kickstart指南](kickstart-for-aem-screens.md)
   + [螢幕最佳實務指南](https://docs.adobe.com/content/help/zh-Hant/experience-manager-screens/using/about-guide.html)
   + [主要條款](screens-glossary.md)
+ 數位標牌網路基本概念{#digital-signage-network}
   + [第1部分：項目角色和責任](project-roles-responsibilities.md)
   + [第二部分：項目範圍時的注意事項](project-considerations.md)
   + [第3部分：測試、POC、試點和推展](testing-pocs-pilots-rollouts.md)
   + [第四部分：專案管理與部署](project-management-and-deployment.md)
   + [第5部分：支援考量事項](support-considerations.md)
+ 配置和管理{#administering}
   + [畫面伺服器組態](configuring-screens-introduction.md)
   + [設定Dispatcher配置](dispatcher-configurations-aem-screens.md)
   + [安裝Screens Player](installing-screens-player.md)
   + [連接畫面播放器](working-with-screens-player.md)
   + [裝置註冊](device-registration.md)
   + [設定ACL](setting-up-acls.md)
   + [AEM Screens安全檢查清單](security-checklist.md)
   + [從ContentSync轉換到SmartSync](smartsync.md)
   + [從檔案新增專案匯入工具](project-importer.md)
   + [將資料觸發器複製至發佈伺服器](replicating-data-triggers.md)
   + 客戶端特定考量事項{#installing-client}
      + [Chrome OS Player](implementing-chrome-os-player.md)
      + [使用Chrome Player做為擴充功能進行疑難排解](using-chrome-player-as-an-extension.md)
      + [Android Player](implementing-android-player.md)
      + [Windows Player](implementing-windows-player.md)
      + [Tizen Player](tizen-player.md)
      + [播放器的自動註冊](auto-registration-players.md)
   + 作者發佈{#author-publish}
      + [作者——發佈架構概觀](author-publish-architecture-overview.md)
      + [設定作者和發佈](author-and-publish.md)
   + Analytics與AEM Screens的整合{#analytics-integration}
      + [Adobe Analytics 整合](adobe-analytics-integration-aem-screens.md)
      + [配置Adobe Analytics與AEM Screens](configuring-adobe-analytics-aem-screens.md)
+ 編寫和使用案例示例{#authoring}
   + 設定畫面專案{#setting-up-projects}
      + [建立和管理專案](creating-a-screens-project.md)
      + [建立和管理渠道](managing-channels.md)
      + [建立和管理顯示](managing-displays.md)
      + [建立和管理位置](managing-locations.md)
      + [建立和管理計畫](managing-schedules.md)
      + [管理裝置](managing-devices.md)
      + 分配通道{#assigning-channels}
         + [頻道指定任務](channel-assignment-latest-fp.md)
         + [渠道分配：舊版AEM Screens功能套件](channel-assignment.md)
   + 使用核心產品功能{#product-features}
      + [文字重疊](text-overlay.md)
      + [大量離線更新](bulk-offline-update.md)
      + [AEM Screens通知服務](screens-notifications-service.md)
      + [使用體驗片段](experience-fragments-in-screens.md)
      + [資產層級啟動](asset-level-scheduling.md)
      + [通路層級啟動](channel-level-activation.md)
      + [建立和管理即時副本](managing-livecopy.md)
      + [建立視訊填補工作流程](creating-a-video-padding-workflow.md)
      + [新增元件至渠道](adding-components-to-a-channel.md)
      + [內嵌序列](embedded-sequences.md)
      + [多區域版面](multi-zone-layout-aem-screens.md)
      + [視訊轉譯](generating-renditions.md)
      + [動態內嵌序列](dynamic-embedded-sequences.md)
      + [頻道層級大量影像播放持續時間](channel-level-image-playback.md)
      + [命令同步](using-command-sync.md)
      + [使用資料觸發器製作內容](authoring-data-triggers.md)
      + [語音識別](voice-recognition.md)
      + [內容指派報表](content-assignment-report.md)
   + 管理內容更新{#content-updates}
      + [隨選內容更新](on-demand-content.md)
      + [內容即服務更新](content-update-as-a-service.md)
      + [使用畫面啟動來更新內容](launches.md)
   + 使用案例範例{#use-case-examples}
      + [緊急通道](emergency-channel.md)
      + [旅行中心溫度激活](local-temperature-activation.md)
      + [酒店預訂激活](hospitality-reservation-activation.md)
      + [零售庫存鎖定](retail-inventory-activation.md)
      + [套用轉場效果](applying-transitions.md)
      + [多區域到單區域的過渡](multizone-to-singlezone.md)
      + [單次使用TakeOver通道](single-use-takeover-channel.md)
      + [永久使用TakeOver Channel](perpetual-takeover-channel.md)
+ 開發人員與API資源{#developing}
   + [REST API](rest-api.md)
   + [開發適用於AEM Screens的自訂元件](developing-custom-component-tutorial-develop.md)
   + [離線渠道](offline-channels.md)
   + [擴展AEM Screens元件](extending-component-tutorial-develop.md)
   + [建立元件](creating-components.md)
   + [使用編輯器內嵌REACT應AEM用程SPA式並與AEM Screens分析整合](embedding-react-app.md)
   + [在AEM Screens配置ContextHub](configuring-context-hub.md)
   + [建立多區域版面的自訂範本](creating-custom-templates-multizone-layouts.md)
   + [為文字覆蓋套用自訂品牌和樣式](custom-branding-text-overlays.md)
+ 疑難排解和常見問答集{#troubleshooting}
   + [AEM Screens常見問答集](aem-screens-faqs.md)
   + [設備控制中心故障排除](monitoring-screens.md)
   + [視訊播放設定](troubleshoot-videos.md)
+ 發行說明 {#release-notes}
   + [功能套件202103發行說明](release-notes-fp-202103.md)
   + [功能套件202011發行說明](release-notes-fp-202011.md)
   + [功能套件202008發行說明](release-notes-fp-202008.md)
   + [功能套件202004發行說明](release-notes-fp-202004.md)
   + [功能套件202001發行說明](release-notes-fp-202001.md)
   + [功能套件201909發行說明](release-notes-fp-201909.md)
   + [功能套件201907發行說明](release-notes-fp-201907.md)
   + [功能套件201905發行說明](screens-release-notes-fp-201905.md)
   + [功能套件201812發行說明](release-notes-fp-201812.md)
   + [功能套件201809發行說明](screens-release-notes.md)

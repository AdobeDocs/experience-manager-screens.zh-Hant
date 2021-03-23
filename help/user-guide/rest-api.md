---
title: REST API
seo-title: REST API
description: AEM Screens提供了遵循Siren規範的簡單REST風格API。 請依照本頁來瞭解如何導覽內容結構，並傳送指令至環境中的裝置。
seo-description: AEM Screens提供了遵循Siren規範的簡單REST風格API。 請依照本頁來瞭解如何導覽內容結構，並傳送指令至環境中的裝置。
uuid: 5988fdcb-cda5-4d3e-a2ab-f9ee4179e568
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: c07b6e4f-c0a4-4151-a543-76dabd6d5146
feature: 開發螢幕
role: 開發人員
level: 中級
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# REST API{#rest-apis}

AEM Screens提供遵循[Siren](https://github.com/kevinswiber/siren)規範的簡單REST風格API。 它允許導航內容結構，並向環境中的設備發送命令。

API可從&#x200B;[*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json)存取。

## 導覽內容結構{#navigating-content-structure}

API呼叫傳回的JSON會列出與目前資源相關的實體。 在列出的自連結後，這些實體中的每個實體都可作為REST資源再次訪問。

例如，若要存取我們展示旗艦位置的顯示畫面，您可以呼叫：

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship.json HTTP/1.1
Host: http://localhost:4502
```

或使用捲曲：

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json
```

結果會是：

```xml
{
  "class": [
    "aem-io/screens/location"
  ],
  "links": [
    {
      "rel": [
        "self"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json"
    },
    {
      "rel": [
        "parent"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo.json"
    }
  ],
  "properties": {…},
  "entities": [
    {
      "class": [
        "aem-io/screens/display"
      ],
      "links": [
        {
          "rel": [
            "self"
          ],
          "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json"
        }
      ],
      "rel": [
        "child"
      ],
      "properties": {
        "title": "Single Screen Display",
        "height": 1440,
        "description": "Demo location of a single screen display.",
        "name": "single",
        "width": 2560,
        "idletimeout": 300,
        "layoutrows": 1,
        "layoutcols": 1
      }
    },
    …
  ]
}
```

然後，若要存取「單一螢幕顯示」，您可呼叫：

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

## 在資源{#executing-actions-on-the-resource}上執行操作

API呼叫傳回的JSON可包含資源上可用動作的清單。

例如，顯示器列出了&#x200B;*broadcast-command*&#x200B;操作，該操作允許向分配給該顯示器的所有設備發送命令。

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

或使用捲曲：

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

***結果:***

```xml
{
  "class": [
    "aem-io/screens/display"
  ],
  "links": […],
  "properties": {…},
  "entities": […],
  "actions": [
    {
      "title": "",
      "name": "broadcast-command",
      "method": "POST",
      "href": "/api/screens/content/screens/we-retail/locations/demo/flagship/single",
      "fields": [
        {
          "name": ":operation",
          "value": "broadcast-command",
          "type": "hidden"
        },
        {
          "name": "msg",
          "type": "text"
        }
      ]
    }
  ]
}
```

若要觸發此動作，您會呼叫：

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

或使用捲曲：

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```


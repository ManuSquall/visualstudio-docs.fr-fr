---
title: "JsSerializedScriptLoadSourceCallback, Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSerializedScriptLoadSourceCallback, Typedef
Appelé par le runtime pour charger le code source du script sérialisé. L’appelant doit conserver la mémoire tampon du script valide jusqu’à `JsSerializedScriptUnloadCallback`.  
  
## Syntaxe  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### Paramètres  
 `sourceContext`  
 Contexte passé à `JsParseSerializedScriptWithCallback` ou `JsRunSerializedScriptWithCallback`.  
  
 `scriptBuffer`  
 Script retourné.  
  
## Notes  
  
> [!WARNING]
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)
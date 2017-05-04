---
title: "JsSerializedScriptUnloadCallback, typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSerializedScriptUnloadCallback, typedef
Appelé par le runtime quand il en a terminé avec toutes les ressources liées à l’exécution du script. L’appelant doit libérer la source si elle est chargée, le code d’octet et le contexte à ce moment\-là.  
  
## Syntaxe  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### Paramètres  
 `sourceContext`  
 Contexte passé à `JsParseSerializedScriptWithCallback` ou `JsRunSerializedScriptWithCallback`.  
  
## Notes  
  
> [!WARNING]
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)
---
title: "JsContextRef, typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsContextRef, typedef
Une référence à un contexte de script.  
  
## Syntaxe  
  
```  
typedef JsRef JsContextRef;  
```  
  
## Notes  
 Chaque contexte de script contient son propre objet global, distinct de l'objet global des autres contextes de script.  
  
 De nombreuses API d'hébergement Chakra nécessitent un contexte de script « actif », qui peut être défini à l'aide de `JsSetCurrentContext`.  Quand les API hébergeant Chakra nécessitent un contexte actif à définir, leur documentation l'indique explicitement.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)
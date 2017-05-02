---
title: "JsRef, typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsRef, typedef
Une référence à un objet détenu par le récupérateur de mémoire Chakra.  
  
## Syntaxe  
  
```  
typedef void *JsRef;  
```  
  
## Notes  
 Un runtime Chakra fera automatiquement le suivi des références JsRef dès lors qu'elles sont stockées dans des variables locales ou dans des paramètres \(c'est\-à\-dire  sur la pile\).  Le stockage d'une référence JsRef ailleurs que sur la pile nécessite l'appel de JsAddRef et de JsRelease pour gérer le cycle de vie de l'objet, sans quoi le récupérateur de mémoire est susceptible de libérer l'objet alors qu'il est encore utilisé.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)
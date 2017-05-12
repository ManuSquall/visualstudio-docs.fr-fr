---
title: "JsBackgroundWorkItemCallback, typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: e6db52e1-830c-46a2-b9f9-cc2d450a1da8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsBackgroundWorkItemCallback, typedef
Un rappel d'élément de travail d'arrière\-plan.  
  
## Syntaxe  
  
```  
typedef void (CALLBACK *JsBackgroundWorkItemCallback)(  
   _In_opt_ void *callbackData  
);  
```  
  
#### Paramètres  
 donnéesRappel  
 Argument de données passé au service de thread.  
  
## Notes  
 Il est passé au service de thread de l'hôte \(s'il est spécifié\) pour permettre à l'hôte d'appeler le rappel d'élément de travail sur le thread d'arrière\-plan de son choix.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)
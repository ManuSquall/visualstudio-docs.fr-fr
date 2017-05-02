---
title: "JsThreadServiceCallback, typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsThreadServiceCallback, typedef
Un rappel de service de thread.  
  
## Syntaxe  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### Paramètres  
 rappel  
 Le rappel pour l'élément de travail d'arrière\-plan.  
  
 donnéesRappel  
 L'argument de données à passer au rappel.  
  
## Notes  
 L'hôte peut spécifier un service de thread d'arrière\-plan lors de l'appel de JsCreateRuntime.  S'il est spécifié, les éléments de travail d'arrière\-plan seront passés à l'hôte à l'aide de ce rappel.  Il est attendu de l'hôte qu'il commence à exécuter immédiatement l'élément de travail d'arrière\-plan et qu'il retourne true, ou bien qu'il retourne false et que le runtime gère l'élément de travail dans un thread.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)
---
title: "JsRuntimeHandle, typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsRuntimeHandle, typedef
Un handle vers un runtime Chakra.  
  
## Syntaxe  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## Notes  
 Chaque runtime Chakra a son propre moteur d'exécution indépendant, son compilateur JIT et son tas récupéré par le garbage collector.  Ainsi, chaque runtime est complètement isolé des autres runtimes.  
  
 Les runtimes peuvent être utilisés par tous les threads, mais il ne peut y avoir qu'un seul appel de thread à la fois dans un runtime.  
  
> [!WARNING]
>  Un handle JsRuntimeHandle, au contraire des autres références d'objet dans l'API hébergeant Chakra, n'est pas récupéré par le garbage collector car il contient le tas récupéré par le garbage collector lui\-même.  Un runtime continue d'exister jusqu'à ce que JsDisposeRuntime soit appelé.  
  
## Configuration requise  
 **En\-tête :** jsrt.h  
  
## Voir aussi  
 [Référence \(JavaScript Runtime\)](../chakra-hosting/reference-javascript-runtime.md)
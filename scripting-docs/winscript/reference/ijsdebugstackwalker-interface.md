---
title: "IJsDebugStackWalker, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugStackWalker, interface
Représente un explorateur de piles pour un thread spécifié.  
  
## Syntaxe  
  
```  
IJsDebugStackWalker : public IUnknown;  
```  
  
## Membres  
  
### Méthodes publiques  
  
|Nom|Description|  
|---------|-----------------|  
|[IJsDebugStackWalker::GetNext, méthode](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Obtient le frame suivant.|  
  
## Notes  
 Les explorateurs de pile ne peuvent être créés que pendant l'arrêt de la cible, et ne sont pas valides après la reprise du processus cible.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [Interfaces Windows Script, référence](../../winscript/reference/windows-script-interfaces-reference.md)
---
title: "IJsDebugProcess, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugProcess, interface
Fournit des routines pour inspecter et contrôler le processus cible.  
  
## Syntaxe  
  
```  
IJsDebugProcess : public IUnknown;  
```  
  
## Membres  
  
### Méthodes publiques  
  
|Nom|Description|  
|---------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint, méthode](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Définit le point d'arrêt à la position spécifiée de document.|  
|[IJsDebugProcess::CreateStackWalker, méthode](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Méthode de fabrique pour l'explorateur de piles.|  
|[IJsDebugProcess::PerformAsyncBreak, méthode](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Place le moteur de script en mode arrêt, ce qui provoque son arrêt sur l'instruction de script suivante.|  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [Interfaces Windows Script, référence](../../winscript/reference/windows-script-interfaces-reference.md)
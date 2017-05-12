---
title: "IJsDebugProcess::CreateStackWalker, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateStackWalker
apilocation: jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugProcess::CreateStackWalker, m&#233;thode
Méthode de fabrique pour l'explorateur de piles.  
  
## Syntaxe  
  
```  
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### Paramètres  
 `threadId`  
 \[in\] ID de thread.  
  
 `ppStackWalker`  
 \[out\] Nouvel objet d'explorateur de piles.  
  
## Valeur de retour  
  
## Notes  
 Retourne E\_JsDEBUG\_UNKNOWN\_THREAD si le thread ne contient pas JavaScript.  Cette méthode peut uniquement être appelée quand le processus cible est arrêté.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugProcess, interface](../../winscript/reference/ijsdebugprocess-interface.md)
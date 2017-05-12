---
title: "IJsDebugDataTarget::GetThreadContext, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetThreadContext
apilocation: jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::GetThreadContext, m&#233;thode
Récupère le contexte pour un thread donné.  
  
## Syntaxe  
  
```  
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### Paramètres  
 `threadId`  
 \[in\] Thread s'exécutant dans le processus cible.  
  
 `contextFlags`  
 \[in\] Spécifie les indicateurs de contexte.  Cela correspond au champ ContextFlags du CONTEXTE \(pour plus d'informations, consultez winnt.h, recherchez CONTEXT\_ALL\).  
  
 `contextSize`  
 \[in\] Taille de la mémoire tampon spécifiée par pContext.  
  
 `pContext`  
 \[out\] Reçoit la structure de CONTEXTE spécifique à la plateforme dans la mémoire tampon spécifiée par pContext.  
  
## Valeur de retour  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugDataTarget, interface](../../winscript/reference/ijsdebugdatatarget-interface.md)
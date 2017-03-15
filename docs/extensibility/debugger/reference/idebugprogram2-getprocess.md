---
title: "IDebugProgram2::GetProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetProcess"
helpviewer_keywords: 
  - "IDebugProgram2::GetProcess"
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtenez le processus que ce programme est exécuté.  
  
## Syntaxe  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```c#  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### Paramètres  
 `ppProcess`  
 \[out\]  Retourne l'interface d' [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) qui représente le processus.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 À moins qu'un \(DE\) moteur de débogage implémente l'interface d' [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) , l'implémentation De de cette méthode doit toujours retourner `E_NOTIMPL` car un De ne peut pas déterminer le processus s'exécutent dans et ne peut donc pas besoin de satisfaire une implémentation de cette méthode.  
  
 Implémenter l'interface de `IDebugEngineLaunch2` signifie que le De doit savoir comment créer un processus ; par conséquent, l'implémentation De de l'interface d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) peut savoir dans quel processus elle s'exécute.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
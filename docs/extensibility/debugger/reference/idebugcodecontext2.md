---
title: "IDebugCodeContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCodeContext2"
helpviewer_keywords: 
  - "Interface de IDebugCodeContext2"
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCodeContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente la position de départ d'une instruction de code.  pour la plupart des architectures à l'exécution aujourd'hui, un contexte de code peut être considéré comme une adresse dans un flux de données de l'exécution du programme.  
  
## Syntaxe  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur de débogage implémente cette interface pour comparer la position d'une instruction de code à une position de document.  
  
## Remarques pour les appelants  
 Les méthodes dans de nombreuses interfaces retournent cette interface, le plus courant, [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md).  Il est également largement utilisés avec l'interface d' [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) ainsi que dans les informations sur la résolution de point d'arrêt.  
  
## méthodes en commande de Vtable  
 En plus de les méthodes sur l'interface d' [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)|obtient le contexte de document qui correspond au contexte de code actif.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Obtient les informations de langage dans ce contexte de code.|  
  
## Notes  
 la différence principale entre une interface d' `IDebugCodeContext2` et une interface d' [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) est qu' `IDebugCodeContext2` instruction\-est toujours aligné.  Cela signifie qu' `IDebugCodeContext2` toujours pointe vers le début d'une instruction, alors qu' `IDebugMemoryContext2` peut indiquer tout octet de mémoire dans l'architecture au moment de l'exécution.  `IDebugCodeContext2` est incrémenté par l'instruction plutôt que par la taille de stockage de base \(en général octets\).  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../Topic/IDebugThread2::CanSetNextStatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)   
 [Suivant](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
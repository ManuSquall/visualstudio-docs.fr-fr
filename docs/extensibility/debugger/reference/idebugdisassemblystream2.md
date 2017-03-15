---
title: "IDebugDisassemblyStream2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2"
helpviewer_keywords: 
  - "Interface de IDebugDisassemblyStream2"
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente un flux de données de l'instruction.  
  
## Syntaxe  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un moteur de débogage implémente cette interface pour prendre en charge le code machine du code d'un programme.  
  
## Remarques pour les appelants  
 Un appel à la méthode d' [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) retourne cette interface.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugDisassemblyStream2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|L'instruction lectures à partir de la position actuelle dans le code machine des flux.|  
|[Recherche](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Déplace le pointeur de lecture dans le flux de code machine un nombre donné d'instruction par rapport à la position spécifiée.|  
|[GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)|Retourne un identificateur d'emplacement du code pour un contexte de code particulier.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Retourne un objet de contexte de code correspondant à un identificateur spécifié d'emplacement du code.|  
|[GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)|Retourne un identificateur d'emplacement de code qui représente l'emplacement actuel du code.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Obtient le document source associé à ce flux de code machine.|  
|[GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md)|Obtient la portée de ce flux du code machine.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Obtient la taille de ce flux du code machine.|  
  
## Notes  
 Le flux de code machine peut être créé pour représenter l'espace d'adressage entier ou d'une fonction ou un module dans l'espace.  chaque instruction est représentée par une structure de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) retournée par un appel à la méthode d' [Lecture](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
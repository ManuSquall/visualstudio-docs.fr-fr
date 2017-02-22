---
title: "IDebugMemoryContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2"
helpviewer_keywords: 
  - "Interface de IDebugMemoryContext2"
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente une position dans l'espace d'adressage de l'ordinateur exécutant le programme débogué.  
  
## Syntaxe  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 le moteur de débogage \(DE\) implémente cette interface pour représenter une adresse dans la mémoire.  
  
## Remarques pour les appelants  
 Un appel à [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) ou à [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) retourne cette interface.  En outre, les appels copies de retour d' [Ajouter](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) et d' [Soustraire](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) à de nouvelles de cette interface après l'opération arithmétique appropriée a été appliqués.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugMemoryContext2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Obtient le nom utilisateur\-affichable dans ce contexte.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|obtient les informations qui décrivent ce contexte.|  
|[Ajouter](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|ajoute une valeur spécifiée à l'adresse actuelle du contexte pour créer un nouveau contexte.|  
|[Soustraire](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|soustrait une valeur spécifiée de l'adresse actuelle du contexte pour créer un nouveau contexte.|  
|[Comparer](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Compare deux contextes de la façon indiquée par comparaison des balises.|  
  
## Notes  
 Les appels [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) de fenêtre de **Mémoire** de Visual Studio pour obtenir l'interface d' `IDebugMemoryContext2` qui contient l'expression évaluée les avez utilisés pour l'adresse mémoire.  Ce contexte est ensuite passé à [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) et à [WriteAt](../Topic/IDebugMemoryBytes2::WriteAt.md) pour spécifier l'adresse pour lire ou écrire.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../Topic/IDebugMemoryBytes2::WriteAt.md)
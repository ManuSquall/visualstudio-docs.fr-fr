---
title: "IDebugModule3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3"
helpviewer_keywords: 
  - "Interface de IDebugModule3"
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugModule3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente un module qui prend en charge les autres emplacements des symboles et des rapports de JustMyCode.  
  
## Syntaxe  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage implémente cette interface pour prendre en charge les autres emplacements des symboles et utiliser des rapports de JustMyCode \(consultez [Glossaire du débogueur Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) pour une définition de « JustMyCode »\).  
  
## Remarques pour les appelants  
 Un appel à [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) retourne cette interface.  Le De envoie l'interface d' [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) au gestionnaire de débogage de session \(SDM\) à l'aide de la méthode d' [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .  En outre, un appel à [QueryInterface](/visual-cpp/atl/queryinterface) sur une interface d' [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) retourne cette interface.  
  
## méthodes en commande de Vtable  
 En plus de les méthodes sur l'interface d' [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Retourne une liste de chemins d'accès de la recherche de symboles et les résultats de la recherche chaque chemin d'accès.|  
|[LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md)|Les charges et initialise les symboles pour le module actuel.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Retourne marquent les indicateurs de spécifier si le module représente le code utilisateur.|  
|[SetJustMyCodeState](../Topic/IDebugModule3::SetJustMyCodeState.md)|Spécifie, que le module doit être considéré comme le code utilisateur ou pas.|  
  
## Notes  
 Visual Studio est le consommateur courante de cette interface.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
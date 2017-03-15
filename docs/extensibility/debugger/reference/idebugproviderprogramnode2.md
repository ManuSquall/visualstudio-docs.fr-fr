---
title: "IDebugProviderProgramNode2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProviderProgramNode2"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2"
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProviderProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface marshale les interfaces en rapport avec le programme au delà de les limites du processus.  
  
## Syntaxe  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage implémente cette interface sur le même objet qui implémente [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) pour prendre en charge les interfaces de marshaling au delà de les limites du processus.  
  
## Remarques pour les appelants  
 Appelez [QueryInterface](/visual-cpp/atl/queryinterface) à une interface de `IDebugProgramNode2` pour obtenir cette interface.  Si cette interface ne peut pas être obtenue, le De ne prend pas en charge le marshaling des interfaces.  
  
## méthodes en commande de Vtable  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Obtient une interface spécifiée au delà de les limites du processus.|  
  
## Notes  
 Cette interface est implémentée lorsque les passes de dans un espace de processus séparé du programme débogué : par exemple, lors De l'exécution dans l'espace de processus Visual Studio plutôt que de l'espace de processus du programme débogué.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
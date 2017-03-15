---
title: "IDebugProgramEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEx2"
helpviewer_keywords: 
  - "Interface de IDebugProgramEx2"
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface permet au gestionnaire de débogage de session \(SDM\) attacher le débogueur à un programme et obtenir le nœud de programmation associé à un programme.  
  
## Syntaxe  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un fournisseur de port implémente cette interface sur le même objet que l'interface d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) afin de permettre l'attachement de SDM à un programme pendant qu'en même temps que le fournisseur de port pour suivre les sessions se joignait au programme.  Le fournisseur de port peut implémenter cette interface s'il choisit.  
  
## Remarques pour les appelants  
 Le SDM appelle [QueryInterface](/visual-cpp/atl/queryinterface) sur une interface d' `IDebugProgram2` pour obtenir cette interface pour suivre les sessions qui se sont attachées aux programmes.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugProgramEx2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|joint un programme à une session.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtient le nœud de programmation associé à un programme.|  
  
## Notes  
 cette interface est privée entre le SDM et le programme.  
  
## Configuration requise  
 en\-tête : Portpriv.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
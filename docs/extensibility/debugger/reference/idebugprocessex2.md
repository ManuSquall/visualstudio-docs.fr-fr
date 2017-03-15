---
title: "IDebugProcessEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2"
helpviewer_keywords: 
  - "Interface de IDebugProcessEx2"
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface permet au gestionnaire de débogage de session \(SDM\) avertir un processus qu'elle est attaché ou se détache de processus.  
  
## Syntaxe  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un fournisseur de port implémente cette interface sur le même objet que l'interface d' [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) :  
  
-   Suivi de prise en charge des sessions connectés à un processus  
  
-   Auto\-attachement de prise en charge sur plusieurs moteurs de débogage  
  
 Le fournisseur de port peut implémenter cette interface s'il choisit.  
  
## Remarques pour les appelants  
  
-   Le SDM appelle [QueryInterface](/visual-cpp/atl/queryinterface) sur une interface d' `IDebugProcess2` pour obtenir cette interface.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugProcessEx2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informe le processus qu'une session sont traduits maintenant le processus.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informe le processus qu'une session ne débogue plus le processus.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Ajoute des nœuds de programme d'une liste de moteurs de débogage.|  
  
## Notes  
 cette interface est privée entre le SDM et le processus.  
  
## Configuration requise  
 en\-tête : Portpriv.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
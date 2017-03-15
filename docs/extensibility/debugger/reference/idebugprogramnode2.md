---
title: "IDebugProgramNode2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2"
helpviewer_keywords: 
  - "Interface de IDebugProgramNode2"
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# IDebugProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente un programme qui peut être débogué.  
  
## Syntaxe  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un moteur \(DE\) de débogage ou un fournisseur de port implémente cette interface pour représenter un programme qui peut être débogué.  Cette interface est généralement implémenté sur le même objet qui implémente l'interface d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .  cette interface est enregistrée avec [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] en appelant [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## Remarques pour les appelants  
 Appel [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) pour retourner cette interface.  Un fournisseur de port reçoit cette interface via un appel à [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md).  Un De reçoit cette interface via un appel à [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugProgramNode2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|obtient le nom d'un programme.|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Obtient le nom de l'hébergement de processus un programme.|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|obtient à l'identificateur de processus système pour l'hébergement de processus un programme.|  
|[GetHostMachineName\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|DÉCONSEILLÉ.  NE SUR UTILISEZ NOT.|  
|[Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|DÉCONSEILLÉ.  NE SUR UTILISEZ NOT.  Consultez l'interface d' [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) pour une autre approche.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Obtient le nom et l'identificateur de running ce programme.|  
|[DetachDebugger\_V7](../Topic/IDebugProgramNode2::DetachDebugger_V7.md)|DÉCONSEILLÉ.  NE SUR UTILISEZ NOT.|  
  
## Notes  
 Le gestionnaire de débogage de session \(SDM\) appelle généralement [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) pour obtenir cette interface.  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
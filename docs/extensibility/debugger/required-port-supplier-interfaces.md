---
title: "Interfaces de fournisseur de Port requis | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fournisseurs de port, interfaces requises"
  - "débogage (débogage SDK), des fournisseurs de port"
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Interfaces de fournisseur de Port requis
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

un fournisseur de port doit implémenter l'interface d' [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) .       [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Étant donné que les orifices d'alimentation d'un fournisseur de port, il doit également les implémenter.  par conséquent, il doit implémenter les interfaces suivantes :  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Décrit le port et peut énumérer tous les processus qui s'exécutent sur le port.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Fournit pour démarrer et arrêter des processus sur le port.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Fournit un mécanisme pour les programmes qui s'exécutent dans le contexte de ce port pour l'informer pour la création et la destruction du nœud de programme.  Pour plus d'informations, consultez [Nœuds de programme](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     fournit un point de connexion pour [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## opération de fournisseur de port  
 Le récepteur d' [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) reçoit des notifications lorsque le processus et des programmes sont créés et détruits sur un port.  Un port est requis pour envoyer [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) lorsqu'un processus est créé et [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) lorsqu'un processus est détruit sur le port.  Un port est également requis pour envoyer [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) lorsqu'un programme est créé et [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) lorsqu'un programme est détruit dans un processus s'exécutant sur le port.  
  
 un port envoie en général le programme créent et détruisent des événements en réponse aux méthodes d' [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) et de [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , respectivement.  
  
 Étant donné qu'un port peut démarrer et arrêter des processus physiques et des programmes logiques, ces interfaces doivent également être implémentées par le moteur de débogage :  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     décrit le processus physique.  au moins les méthodes suivantes doivent être implémentées :  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Permet que le SDM s'attache et de se détache d'un processus.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     décrit le programme logique.  au moins les méthodes suivantes doivent être implémentées :  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Offre un moyen pour le SDM de s'attacher à ce programme.  
  
## Voir aussi  
 [L'implémentation d'un fournisseur de Port](../../extensibility/debugger/implementing-a-port-supplier.md)
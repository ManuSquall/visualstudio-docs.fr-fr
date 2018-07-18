---
title: Interfaces de fournisseur de Port obligatoires | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e34627effce5e2f0d1401da683536548a32d3f6e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128652"
---
# <a name="required-port-supplier-interfaces"></a>Interfaces de fournisseur de Port requis
Un fournisseur de port doit implémenter la [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interface.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 La mesure où un fournisseur de port fournit des ports, il doit également implémenter les. Par conséquent, il doit implémenter les interfaces suivantes :  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Décrit le port et peut énumérer tous les processus en cours d’exécution sur le port.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Fournit pour lancer et arrêter les processus sur le port.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Fournit un mécanisme pour les programmes qui s’exécutent dans le contexte de ce port pour l’informer de la création de nœuds de programme et la destruction. Pour plus d’informations, consultez [programme nœuds](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Fournit un point de connexion pour [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Opération de fournisseur de port  
 Le [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) récepteur reçoit des notifications lorsque le processus et les programmes sont créés et détruits sur un port. Un port est requis pour envoyer [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) lors de la création d’un processus et [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) lorsqu’un processus sont détruit sur le port. Un port est également requis pour envoyer [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) lors de la création d’un programme et [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) quand un programme est détruit dans un processus en cours d’exécution sur le port.  
  
 Un port généralement envoie programme créer et détruire les événements en réponse à la [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) et [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) méthodes, respectivement.  
  
 Comme un port peut lancer et arrêter les processus physiques et logiques programmes, ces interfaces doivent également être implémentées par le moteur de débogage :  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Décrit le processus physique. Au moins les méthodes suivantes doivent être implémentées :  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Fournit un moyen pour le SDM attachement et détachement lui-même à partir d’un processus.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Décrit le programme logique. Au moins les méthodes suivantes doivent être implémentées :  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Fournit un moyen pour le SDM attacher à ce programme.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un fournisseur de port](../../extensibility/debugger/implementing-a-port-supplier.md)
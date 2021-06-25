---
title: Interfaces du fournisseur de port requises | Microsoft Docs
description: En savoir plus sur les interfaces qu’un fournisseur de port doit exécuter. Un fournisseur de port fournit des ports et les implémente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96cf70302839a9de3c5fb0fec01136d9700ee17e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902369"
---
# <a name="required-port-supplier-interfaces"></a>Interfaces du fournisseur de port requises
Un fournisseur de ports doit implémenter l’interface [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) . [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Un fournisseur de port fournit des ports et les implémente. Par conséquent, il doit exécuter les interfaces suivantes :

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Décrit le port et énumère tous les processus en cours d’exécution sur le port.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Permet de lancer et d’arrêter des processus sur le port.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Fournit un mécanisme pour les programmes qui s’exécutent dans le contexte de ce port pour les informer de la création et de la destruction de nœuds de programme. Pour plus d’informations, consultez la rubrique [nœuds de programme](../../extensibility/debugger/program-nodes.md).

- `IConnectionPointContainer`

  Fournit un point de connexion pour [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).

## <a name="port-supplier-operation"></a>Opération du fournisseur de port
 Le récepteur [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) reçoit des notifications lorsque des processus et des programmes sont créés et détruits sur un port. Un port est requis pour envoyer des [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) lorsqu’un processus est créé et [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) lorsqu’un processus est détruit sur le port. Un port est également requis pour envoyer des [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) lorsqu’un programme est créé et [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) lorsqu’un programme est détruit dans un processus en cours d’exécution sur le port.

 Un port envoie généralement des événements de création et de destruction de programme en réponse aux méthodes [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) et [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , respectivement.

 Comme un port peut lancer et mettre fin à la fois à des processus physiques et à des programmes logiques, les interfaces suivantes doivent également être implémentées par le moteur de débogage :

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Décrit le processus physique. Au moins les méthodes suivantes doivent être implémentées :

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessID,](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Offre un moyen pour le SDM de s’attacher et de se détacher d’un processus.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Décrit le programme logique. Au moins les méthodes suivantes doivent être implémentées :

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess,](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Offre un moyen pour le SDM de s’attacher à ce programme.

## <a name="see-also"></a>Voir aussi
- [Implémentation d’un fournisseur de port](../../extensibility/debugger/implementing-a-port-supplier.md)

---
title: Interfaces fournisseurs portuaires requises (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2aeb1f26f81d773e171aa3fed6b0f2ef976c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713148"
---
# <a name="required-port-supplier-interfaces"></a>Interfaces de fournisseur portuaire requises
Un fournisseur de port doit mettre en œuvre l’interface [IDebugPortSupplier2.](../../extensibility/debugger/reference/idebugportsupplier2.md) [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Un fournisseur portuaire fournit des ports et les met en œuvre. Par conséquent, il doit exécuter les interfaces suivantes:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Décrit le port et énumère tous les processus en cours d’exécution sur le port.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Fournit des processus de lancement et de résiliation sur le port.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Fournit un mécanisme pour les programmes qui s’inscrivent dans le contexte de ce port afin de l’aviser de la création et de la destruction des nœuds de programme. Pour plus d’informations, voir [les nœuds du programme](../../extensibility/debugger/program-nodes.md).

- `IConnectionPointContainer`

  Fournit un point de connexion pour [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).

## <a name="port-supplier-operation"></a>Opération fournisseur de port
 [L’évier IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) reçoit des notifications lorsque le processus et les programmes sont créés et détruits sur un port. Un port est nécessaire pour envoyer [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) lorsqu’un processus est créé et [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) lorsqu’un processus est détruit sur le port. Un port est également nécessaire pour envoyer [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) lorsqu’un programme est créé et [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) lorsqu’un programme est détruit dans le cadre d’un processus en cours d’exécution sur le port.

 Un port envoie généralement des programmes créer et détruire des événements en réponse aux méthodes [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) et [RemoveProgramNode,](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) respectivement.

 Étant donné qu’un port peut lancer et mettre fin à la fois aux processus physiques et aux programmes logiques, les interfaces suivantes doivent également être mises en œuvre par le moteur de débogé :

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Décrit le processus physique. Au moins les méthodes suivantes doivent être mises en œuvre :

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId (en)](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Fournit un moyen pour le SDM de s’attacher et de se détacher d’un processus.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Décrit le programme logique. Au moins les méthodes suivantes doivent être mises en œuvre :

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess (en)](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Fournit un moyen pour le SDM de s’attacher à ce programme.

## <a name="see-also"></a>Voir aussi
- [Mise en œuvre d’un fournisseur portuaire](../../extensibility/debugger/implementing-a-port-supplier.md)

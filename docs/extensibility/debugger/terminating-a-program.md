---
title: Arrêt d’un programme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 729d37c36782cd1786124c94796f610931473f0c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912747"
---
# <a name="terminating-a-program"></a>Arrêt d’un programme
La section suivante décrit l’arrêt d’un programme unique avec un seul thread.

## <a name="termination-process"></a>Processus d’arrêt

1. L’envoie DE un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) avec valide [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).

2. L’envoie DE un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) avec valide [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).

   L’IDE repasse en mode design. Le moteur de débogage ou d’un environnement d’exécution appelle [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) pour supprimer le programme à partir du port.

## <a name="see-also"></a>Voir aussi
- [Appel des événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)
---
title: Mettre fin à un programme (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 985b20fe75f8ceee3d434ac681b437c51baf85e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712523"
---
# <a name="terminating-a-program"></a>Mettre fin à un programme
La section suivante décrit la fin d’un seul programme avec un seul thread.

## <a name="termination-process"></a>Processus de résiliation

1. Le DE envoie un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) avec un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)valide .

2. Le DE envoie un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) avec un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)valide .

   L’IDE passe en mode design. Le moteur de déboguer ou l’environnement de temps d’exécution appelle [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) pour supprimer le programme du port.

## <a name="see-also"></a>Voir aussi
- [Appel d’événements débbugger](../../extensibility/debugger/calling-debugger-events.md)

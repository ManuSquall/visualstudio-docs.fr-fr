---
title: Arrêt d’un programme | Microsoft Docs
description: Cet article explique comment l’IDE utilise le moteur de débogage pour mettre fin à un seul programme avec un seul thread.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1b2b883611d5479f0febc169b32f7f378230be4c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995978"
---
# <a name="terminating-a-program"></a>Arrêt d’un programme
La section suivante décrit l’arrêt d’un seul programme avec un seul thread.

## <a name="termination-process"></a>Processus d’arrêt

1. Le DE envoie un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) avec un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)valide.

2. Le DE envoie un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) avec un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)valide.

   L’IDE passe en mode Design. Le moteur de débogage ou l’environnement d’exécution appelle [IDebugPortNotify2 :: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) pour supprimer le programme du port.

## <a name="see-also"></a>Voir aussi
- [Appel des événements du débogueur](../../extensibility/debugger/calling-debugger-events.md)

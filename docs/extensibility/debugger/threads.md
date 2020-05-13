---
title: Fils Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ed5c06e0c42dac1f0539cc2c7c5886d95b23ae1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712477"
---
# <a name="threads"></a>Threads
Dans l’architecture débbugger, un *fil*:

- Est l’unité fondamentale du calcul. Un thread exécute séquentiellement ses instructions dans le contexte d’une pile d’appels unique, passant d’un contexte de code à l’autre.

- Peut s’identifier et le programme dans lequel il est en cours d’exécution. Les fils peuvent être nommés, suspendus et repris. Un thread peut également énumérer ses cadres de pile associés et, dans certaines conditions, peut être déplacé vers un autre cadre de pile. Compte tenu du contexte d’un cadre de pile, un thread peut retourner son thread logique associé, le cas échéant. Un thread a des propriétés, telles qu’un compte de suspension, qui peuvent être affichés dans la fenêtre **Threads** de l’IDE.

- Est représenté par une interface [IDebugThread2,](../../extensibility/debugger/reference/idebugthread2.md) généralement créée par un moteur de débogé (DE) ou une machine virtuelle à la suite de l’exécution d’un programme.

## <a name="see-also"></a>Voir aussi
- [Programmes](../../extensibility/debugger/programs.md)
- [Piles de cadres](../../extensibility/debugger/stack-frames.md)
- [Moteur Debug](../../extensibility/debugger/debug-engine.md)
- [Concepts Debugger](../../extensibility/debugger/debugger-concepts.md)
- [Gestionnaire de débogé de session](../../extensibility/debugger/session-debug-manager.md)

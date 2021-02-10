---
title: Threads | Microsoft Docs
description: Cet article décrit la définition et le rôle d’un thread dans l’architecture du débogueur dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec3c427e722739f17984866b8756d606ecb57813
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965458"
---
# <a name="threads"></a>Threads
Dans l’architecture du débogueur, un *thread*:

- Est l’unité fondamentale du calcul. Un thread exécute séquentiellement ses instructions dans le contexte d’une pile des appels unique, en passant d’un contexte de code à l’autre.

- Peut s’identifier et le programme dans lequel il s’exécute. Les threads peuvent être nommés, suspendus et repris. Un thread peut également énumérer ses frames de pile associés et, sous certaines conditions, peut être déplacé vers un autre frame de pile. Étant donné le contexte d’un frame de pile, un thread peut retourner son thread logique associé, le cas échéant. Un thread a des propriétés, telles qu’un compteur de suspension, qui peuvent être affichées dans la fenêtre **Threads** de l’IDE.

- Est représenté par une interface [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) , généralement créée par un moteur de débogage (de) ou une machine virtuelle suite à l’exécution d’un programme.

## <a name="see-also"></a>Voir aussi
- [Programmes](../../extensibility/debugger/programs.md)
- [Frames de pile](../../extensibility/debugger/stack-frames.md)
- [Moteur de débogage](../../extensibility/debugger/debug-engine.md)
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [Gestionnaire de débogage de session](../../extensibility/debugger/session-debug-manager.md)

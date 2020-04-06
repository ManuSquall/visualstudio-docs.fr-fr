---
title: Appel d’événements Debugger (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 869bd87952aebf8ad640c5aeb439c9e99929f4c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739162"
---
# <a name="call-debugger-events"></a>Événements de débogénaire d’appel
Les événements dans les sessions de débogage se produisent dans un ordre spécifique.

## <a name="discussion"></a>Discussions
 Pour comprendre le modèle d’appels entre le moteur de débogé (DE) et le gestionnaire de débogage de session (SDM), ce qui suit représente l’ordre d’appel des événements qui se produisent dans une session typique de débogage:

1. [Attachement et détachement à un programme](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Lancement du débbugger](../../extensibility/debugger/launching-the-debugger.md)

3. [Mettre fin à un programme](../../extensibility/debugger/terminating-a-program.md)

4. [Création d’un point d’arrêt](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Lorsqu’un point d’arrêt se lie ou devient non lié](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Erreurs de point de rupture](../../extensibility/debugger/breakpoint-errors.md)

7. [Hitting a breakpoint](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Suppression d’un point d’arrêt](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Entrée en mode pause](../../extensibility/debugger/entering-break-mode.md)

10. [Passer en mode pause](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Évaluation de l’expression en mode pause](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Manipulation d’exception](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Voir aussi
- [Création d’un moteur de débogé personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)

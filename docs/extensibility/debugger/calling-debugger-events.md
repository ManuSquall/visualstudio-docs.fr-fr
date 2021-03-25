---
title: Appel des événements du débogueur | Microsoft Docs
description: Les événements dans les sessions de débogage se produisent dans un ordre spécifique. Cet article répertorie l’ordre d’appel des événements qui se produisent dans une session de débogage classique.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b0c3169039115432758cfdcd3f0612c3578b74c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055048"
---
# <a name="call-debugger-events"></a>Appeler les événements du débogueur
Les événements dans les sessions de débogage se produisent dans un ordre spécifique.

## <a name="discussion"></a>Discussions
 Pour comprendre le modèle d’appels entre le moteur de débogage (DE) et le gestionnaire de débogage de session (SDM), les éléments suivants représentent l’ordre d’appel des événements qui se produisent dans une session de débogage classique :

1. [Attachement et détachement d’un programme](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Lancement du débogueur](../../extensibility/debugger/launching-the-debugger.md)

3. [Arrêt d’un programme](../../extensibility/debugger/terminating-a-program.md)

4. [Création d’un point d’arrêt](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Quand un point d’arrêt est lié ou devient non lié](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Erreurs de point d’arrêt](../../extensibility/debugger/breakpoint-errors.md)

7. [Atteinte à un point d’arrêt](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Suppression d’un point d’arrêt](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Passage en mode arrêt](../../extensibility/debugger/entering-break-mode.md)

10. [Exécution pas à pas en mode arrêt](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Évaluation d’expression en mode arrêt](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Gestion des exceptions](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Voir aussi
- [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)

---
title: Tâches de débogage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 070068853d962bdf9b209edb9410d33d46ccf853
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903556"
---
# <a name="debug-tasks"></a>Tâches de débogage
Pour déboguer un programme, celui-ci doit être lancé et un moteur de débogage (DE) doit être attaché à celui-ci, sinon le DE doit être attaché à un programme lancé précédemment. Une fois attaché, le DE doit générer certains événements DE démarrage. En réponse, le package de débogage tente de lier les points d’arrêt définis dans l’IDE. Lorsque le programme atteint un point d’arrêt lié, il s’arrête et attend une entrée de l’utilisateur.

## <a name="in-this-section"></a>Dans cette section
 [Problèmes de sécurité](../../extensibility/debugger/security-issues.md) Décrit les étapes de sécurité nécessaires pour déboguer un programme.

 [Lancer un programme](../../extensibility/debugger/launching-a-program.md) Fournit des instructions pas à pas sur la façon de spécifier un DE, qui appelle le système d’exploitation pour lancer le programme.

 [Attachement direct à un programme](../../extensibility/debugger/attaching-directly-to-a-program.md) Décrit le processus utilisé pour déboguer un programme dans un processus qui est déjà en cours d’exécution.

 [Envoyer des événements de démarrage après un lancement](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Répertorie les événements qui ont lieu une fois que le DE est attaché au programme, jusqu’à ce que le programme soit à son point d’entrée principal et qu’il soit prêt pour le débogage.

 [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md) Explique comment le DE envoie généralement un événement DE point d’entrée, un événement de chargement complet ou un événement d’arrêt, selon les circonstances.

 [Lier des points d’arrêt](../../extensibility/debugger/binding-breakpoints.md) Décrit comment, si l’utilisateur définit un point d’arrêt, l’IDE formule la demande et invite la session de débogage à créer le point d’arrêt.

 [Évaluer les expressions](../../extensibility/debugger/evaluating-expressions.md) Explique comment les expressions sont créées et ce qui se passe lorsqu’une expression est évaluée.

 Visualiser [et afficher des données](../../extensibility/debugger/visualizing-and-viewing-data.md) Explique comment les visualiseurs de type et les visionneuses personnalisées sont pris en charge par l’évaluateur d’expression (EE).

## <a name="related-sections"></a>Sections connexes
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md) Décrit les principaux concepts architecturaux du débogage.

 [Composants du débogueur](../../extensibility/debugger/debugger-components.md) Fournit une vue d’ensemble des composants de débogage de Visual Studio, qui incluent le gestionnaire DE symboles DE, EE et (SH).

 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md) Explique comment le fonctionne simultanément dans le code, la documentation et les contextes d’évaluation des expressions. Décrit, pour chacun des trois contextes, l’emplacement, la position ou l’évaluation qui s’y rapporte.

## <a name="see-also"></a>Voir aussi
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

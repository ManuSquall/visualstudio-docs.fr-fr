---
title: Tâches de débogage (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d41f53ab1392ea3c31908faf65a871fa100fbb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738960"
---
# <a name="debug-tasks"></a>Tâches de débogé
Pour déboiffer un programme, il doit être lancé et un moteur de débogé (DE) doit être attaché à elle, ou bien le DE doit être attaché à un programme précédemment lancé. Une fois attaché, le DE doit générer certains événements de démarrage. En réponse, le paquet de déboise tente de lier les points d’arrêt définis dans l’IDE. Lorsque le programme atteint un point d’arrêt lié, il s’arrête et attend l’entrée de l’utilisateur.

## <a name="in-this-section"></a>Contenu de cette section
 [Problèmes de sécurité](../../extensibility/debugger/security-issues.md) Discute des mesures de sécurité nécessaires pour déboiffer un programme.

 [Lancer un programme](../../extensibility/debugger/launching-a-program.md) Fournit des instructions étape par étape sur la façon de spécifier un DE, qui appelle le système d’exploitation pour lancer le programme.

 [Joindre directement à un programme](../../extensibility/debugger/attaching-directly-to-a-program.md) Décrit le processus utilisé pour déboguer un programme dans un processus qui est déjà en cours d’exécution.

 [Envoyer des événements de démarrage après un lancement](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Répertorie les événements qui ont lieu une fois que le DE est attaché au programme, jusqu’à ce que le programme soit à son point d’entrée principal et est prêt pour le débogage.

 [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md) Explique comment le DE envoie généralement un événement de point d’entrée, un événement complet de charge, ou un événement d’arrêt, selon les circonstances.

 [Bind points d’arrêt](../../extensibility/debugger/binding-breakpoints.md) Décrit comment, si l’utilisateur définit un point d’arrêt, l’IDE formule la demande et invite la session de débogé pour créer le point d’arrêt.

 [Évaluer les expressions](../../extensibility/debugger/evaluating-expressions.md) Explique comment les expressions sont créées et ce qui se passe lorsqu’une expression est évaluée.

 [Visualiser et afficher les données](../../extensibility/debugger/visualizing-and-viewing-data.md) Explique comment les visualisateurs de type et les téléspectateurs personnalisés sont pris en charge par l’évaluateur d’expression (EE).

## <a name="related-sections"></a>Sections connexes
 [Concepts Debugger](../../extensibility/debugger/debugger-concepts.md) Décrit les principaux concepts architecturaux débogage.

 [Composants Debugger](../../extensibility/debugger/debugger-components.md) Fournit un aperçu des composants de débogage Visual Studio, qui comprennent le DE, EE, et gestionnaire de symbole (SH).

 [Contextes Debugger](../../extensibility/debugger/debugger-contexts.md) Explique comment le DE fonctionne simultanément dans les contextes d’évaluation du code, de la documentation et de l’expression. Décrit, pour chacun des trois contextes, l’emplacement, le poste ou l’évaluation qui lui est pertinent.

## <a name="see-also"></a>Voir aussi
 [Bien démarrer](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

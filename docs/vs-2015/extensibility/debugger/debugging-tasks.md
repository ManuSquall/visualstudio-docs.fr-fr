---
title: Tâches de débogage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab02c40911f4dbeb2d4452bebfd42c13ec232fc4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254058"
---
# <a name="debugging-tasks"></a>Tâches de débogage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pour déboguer un programme, il doit être lancé et un moteur de débogage (dé) doit être attaché à celui-ci, sans quoi le DE doit être attaché à un programme lancé précédemment. Une fois attaché, le DE doit générer certains événements de démarrage. En réponse, le package de débogage tente de lier les points d’arrêt définis dans l’IDE. Quand le programme atteint un point d’arrêt lié, il s’arrête et attend une saisie de l’utilisateur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Problèmes de sécurité](../../extensibility/debugger/security-issues.md)  
 Décrit les étapes de sécurité qui sont nécessaires pour déboguer un programme.  
  
 [Lancement d’un programme](../../extensibility/debugger/launching-a-program.md)  
 Fournit des instructions détaillées sur la façon de spécifier un DE, qui appelle le système d’exploitation pour lancer le programme.  
  
 [Attachement directement à un programme](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Décrit le processus utilisé pour déboguer un programme dans un processus qui est déjà en cours d’exécution.  
  
 [Envoi d’événements de démarrage après un lancement](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Répertorie les événements qui ont lieu une fois que l’Allemagne est attaché au programme, jusqu'à ce que le programme est à son point d’entrée principal et est prêt pour le débogage.  
  
 [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md)  
 Explique comment le DE généralement envoie un événement de point d’entrée, un événement de fin de charge ou un événement d’arrêt en cours, selon les circonstances.  
  
 [Liaison de points d’arrêt](../../extensibility/debugger/binding-breakpoints.md)  
 Décrit comment, si l’utilisateur définit un point d’arrêt, l’IDE formule la demande et vous invite à entrer la session de débogage pour créer le point d’arrêt.  
  
 [Évaluation des expressions](../../extensibility/debugger/evaluating-expressions.md)  
 Explique comment les expressions sont créées et que se passe-t-il lorsqu’une expression est évaluée.  
  
 [Visualisation et affichage des données](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Explique comment les visualiseurs de type et les visionneuses personnalisées sont prises en charge par l’évaluateur d’expression (EE).  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts architectures débogage.  
  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)  
 Fournit une vue d’ensemble des composants de débogage Visual Studio, qui incluent l’Allemagne, EE et le Gestionnaire de symboles (es).  
  
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)  
 Explique comment le D’opère simultanément dans le code, documentation et contextes d’évaluation d’expression. Décrit, pour chacun des trois contextes, emplacement, position ou d’évaluation pertinente à ce dernier.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)


---
title: "Tâches de débogage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 08f6d64a86982ad7425a2e89815765ce63dbf28c
ms.lasthandoff: 02/22/2017

---
# <a name="debugging-tasks"></a>Tâches de débogage
Pour déboguer un programme, il doit être lancé et un moteur de débogage (DE) doit être lié à, faute de quoi le DE doit être lié à un programme lancé précédemment. Une fois attaché, le DE doit générer certains événements de démarrage. En réponse, le package de débogage tente de lier les points d’arrêt définis dans l’IDE. Lorsque le programme atteint un point d’arrêt lié, celui-ci s’arrête et attend une entrée d’utilisateur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Problèmes de sécurité](../../extensibility/debugger/security-issues.md)  
 Décrit les étapes de sécurité qui sont nécessaires pour déboguer un programme.  
  
 [Lancement d’un programme](../../extensibility/debugger/launching-a-program.md)  
 Fournit des instructions détaillées sur la façon de spécifier un DE, qui appelle le système d’exploitation pour lancer le programme.  
  
 [Attachement directement à un programme](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Décrit le processus utilisé pour déboguer un programme dans un processus en cours d’exécution.  
  
 [L’envoi d’événements de démarrage après le lancement d’un](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Répertorie les événements qui ont lieu une fois la D’est attachée au programme, jusqu'à ce que le programme est à son point d’entrée principal et est prêt pour le débogage.  
  
 [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md)  
 Explique comment le D’envoie généralement un événement de point d’entrée, un événement de fin de charge ou un événement d’arrêt, selon les circonstances.  
  
 [Liaison des points d’arrêt](../../extensibility/debugger/binding-breakpoints.md)  
 Explique comment, si l’utilisateur définit un point d’arrêt, l’IDE formule la demande et vous invite à entrer la session de débogage pour créer le point d’arrêt.  
  
 [L’évaluation des Expressions](../../extensibility/debugger/evaluating-expressions.md)  
 Explique comment les expressions sont créées et que se passe-t-il lorsqu’une expression est évaluée.  
  
 [Visualisation et affichage des données](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Explique comment les visualiseurs de type et les visionneuses personnalisées sont prises en charge par l’évaluateur d’expression (EE).  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts architecturaux de débogage.  
  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)  
 Fournit une vue d’ensemble des composants de débogage Visual Studio, qui incluent le DE, EE et Gestionnaire de symboles (es).  
  
 [Contextes de débogueur](../../extensibility/debugger/debugger-contexts.md)  
 Explique comment le DE fonctionne simultanément dans le code, la documentation et contextes d’évaluation d’expression. Décrit, pour chacun des trois contextes, emplacement, position ou évaluation pertinente pour elle.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

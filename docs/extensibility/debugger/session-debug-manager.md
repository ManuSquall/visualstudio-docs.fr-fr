---
title: Session de débogage Manager | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 321b0a7c7eb2a30465098da39abc49cbc9261e11
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947203"
---
# <a name="session-debug-manager"></a>Gestionnaire de session de débogage
Le Gestionnaire de session de débogage (SDM) gère n’importe quel nombre de moteurs de débogage (dé) que le débogage n’importe quel nombre de programmes dans plusieurs processus sur un nombre illimité d’ordinateurs. En plus de constituer un multiplexeur de moteur de débogage, le SDM fournit une vue unifiée de la session de débogage à l’IDE.  
  
## <a name="session-debug-manager-operation"></a>Opération de gestionnaire de débogage de session  
 Le Gestionnaire de session de débogage (SDM) gère l’Allemagne. Il peut y avoir plus d’un moteur de débogage en cours d’exécution sur un ordinateur en même temps. Pour multiplexer la norme DEs, le SDM encapsule un nombre d’interfaces à partir de la norme DEs et les expose à l’IDE comme une interface unique.  
  
 Pour améliorer les performances, certaines interfaces ne sont pas multiplexés. Au lieu de cela, ils sont utilisés directement à partir de l’Allemagne et les appels à ces interfaces ne passent pas par le SDM. Par exemple, les interfaces utilisées avec la mémoire, le code et les contextes de document ne sont pas multiplexés, car ils font référence à une instruction spécifique, la mémoire ou le document dans un programme spécifique de débogage par un spécifique DE. Aucune autre dé ne doit être impliqué dans ce niveau de la communication.  
  
 Cela n’est pas vrai pour tous les contextes. Les appels à l’interface de contexte d’évaluation expression passent par le SDM. Lors de l’évaluation d’expression, le SDM encapsule le [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface il donne à l’IDE, car lorsque cette expression est évaluée, elle peut impliquer plusieurs DEs que déboguez des programmes dans le même processus qui peuvent être en cours d’exécution sur le même thread.  
  
 Le SDM sert généralement d’un mécanisme de délégation, mais il peut agir comme un mécanisme de diffusion. Par exemple, lors de l’évaluation d’expression, le SDM agit comme un mécanisme de diffusion pour notifier DEs tous les qu’ils peuvent exécuter du code sur un thread spécifié. De même, lorsque le SDM reçoit un événement d’arrêt, il diffuse vers les programmes qu’il doivent s’arrêter. Lorsqu’une étape est appelée, le SDM diffuse vers les programmes qu’ils peuvent continuer à s’exécuter. Points d’arrêt sont également diffusés à chaque DE.  
  
 Le SDM ne suit pas le programme en cours, le thread ou le frame de pile. Le processus, programme et informations sur le thread sont envoyés vers le SDM conjointement avec les événements de débogage spécifiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)   
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)
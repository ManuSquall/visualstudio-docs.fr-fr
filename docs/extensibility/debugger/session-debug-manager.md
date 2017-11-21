---
title: "Session de débogage Manager | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8100c43578c11ae73f26764df74aa17caccc3611
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="session-debug-manager"></a>Gestionnaire de session de débogage
Le Gestionnaire de session de débogage (SDM) gère n’importe quel nombre de moteurs de débogage (DE) n’importe quel nombre de programmes dans plusieurs processus sur n’importe quel nombre d’ordinateurs de débogage. En plus de constituer un moteur de débogage multiplexeur, le SDM fournit une vue unifiée de la session de débogage à l’IDE.  
  
## <a name="session-debug-manager-operation"></a>Opération Gestionnaire de session de débogage  
 Le Gestionnaire de session de débogage (SDM) gère le DE. Il peut y avoir plus d’un moteur de débogage en cours d’exécution sur un ordinateur en même temps. Pour multiplexer la norme DEs, le SDM encapsule un certain nombre d’interfaces à partir de la norme DEs et les expose à l’IDE comme une interface unique.  
  
 Pour améliorer les performances, certaines interfaces ne sont pas multiplexés. Au lieu de cela, ils sont utilisés directement à partir de la DE, et les appels à ces interfaces ne passent pas le SDM. Par exemple, les interfaces utilisées avec la mémoire, le code et les contextes de document ne sont pas multiplexés, car ils font référence à une instruction spécifique, la mémoire ou le document dans un programme spécifique de débogage par un spécifique DE. Aucune autre DE ne doit être associé à ce niveau de la communication.  
  
 Cela n’est pas vrai pour tous les contextes. Les appels à l’interface de contexte d’évaluation expression passent par le SDM. Lors de l’évaluation d’expression, le SDM encapsule le [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface qui permet à l’IDE, car lorsque cette expression est évaluée, elle peut impliquer DEs multiples que vous déboguez des programmes dans le même processus qui peuvent être en cours d’exécution sur le même thread.  
  
 Le SDM sert généralement d’un mécanisme de délégation, mais il peut agir comme un mécanisme de diffusion. Par exemple, lors de l’évaluation d’expression, le SDM joue un mécanisme de diffusion pour notifier DEs tous les qu’ils peuvent exécuter du code sur un thread spécifié. De même, lorsque le SDM reçoit un événement d’arrêt, il diffuse sur tous les programmes qu’ils ne doivent plus en cours d’exécution. Lorsqu’une étape est appelée, le SDM diffuse à tous les programmes qu’ils peuvent continuer à s’exécuter. Points d’arrêt sont également diffusés à tous DE.  
  
 Le SDM ne suit pas le programme en cours, le thread ou le frame de pile. Le processus, le programme et le thread informations sont envoyées vers le SDM conjointement avec les événements de débogage spécifiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)   
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)
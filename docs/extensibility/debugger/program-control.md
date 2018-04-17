---
title: Contrôle du programme | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c227f38c926cb6d764ddf47541b8bd744eb6f7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="program-control"></a>Contrôle du programme
Dans Visual Studio, le débogage, tous les de l’exécution pas à pas suivantes et en continuant de routines de se produisent au niveau du programme :  
  
-   Définir l’instruction suivante, autrement dit, configuration de votre ordinateur à la prochaine instruction à exécuter dans un environnement de frame particulier  
  
-   Poursuite de l’exécution, autrement dit, quitter le mode pas à pas  
  
-   Pas à pas à l’instruction suivante  
  
-   Continuer avec le mode d’exécution pas à pas en cours  
  
-   Suspendre les threads contenus par le programme  
  
-   La reprise de threads contenus par le programme  
  
> [!NOTE]
>  Affichage de la pile des appels est implémentée au niveau du thread. Pour énumérer les informations de frame lors de l’affichage de la pile des appels d’un thread, vous devez implémenter toutes les méthodes de la [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interface.  
  
## <a name="methods-of-program-control"></a>Méthodes de contrôle du programme  
 Le tableau suivant présente les méthodes de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) qui doit être implémentée pour un moteur de débogage fonctionnel au minimum (DE) et le contrôle de l’exécution.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continue de s’exécuter tous les threads sont contenus par un programme à partir d’un état arrêté. Obligatoire pour le contrôle de l’exécution.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continue de s’exécuter tous les threads sont contenus par un programme à partir d’un état arrêté. Obligatoire pour le contrôle de l’exécution.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Effectue une étape sur le thread donné. Continue de s’exécuter tous les autres threads contenus par le programme. Obligatoire pour le contrôle de l’exécution.|  
  
 Pour les programmes multithreads, vous devez également implémenter la [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) (méthode) et toutes les méthodes de la [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de l’exécution et évaluation de l’état](../../extensibility/debugger/execution-control-and-state-evaluation.md)
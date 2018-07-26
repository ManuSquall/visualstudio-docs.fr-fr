---
title: Contrôle du programme | Microsoft Docs
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
ms.openlocfilehash: a60b766763ca5f68f8c379fbab9372e41c319671
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251096"
---
# <a name="program-control"></a>Contrôle du programme
Dans Visual Studio, le débogage, tous l’exécution pas à pas suivantes et en continuant de routines de se produisent au niveau du programme :  
  
-   Définition de l’instruction suivante, autrement dit, définition de votre ordinateur à la prochaine instruction à exécuter dans un environnement de frame particulier  
  
-   L’exécution, autrement dit, continuer quitter le mode pas à pas  
  
-   Pas à pas à l’instruction suivante  
  
-   Continuer avec le mode actuel de l’exécution pas à pas  
  
-   Suspendre les threads contenues par le programme  
  
-   La reprise des threads contenues par le programme  
  
> [!NOTE]
>  Affichage de la pile des appels est implémenté au niveau du thread. Pour énumérer les informations de frame lors de l’affichage de la pile des appels pour un thread, vous devez implémenter toutes les méthodes de la [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interface.  
  
## <a name="methods-of-program-control"></a>Méthodes de contrôle du programme  
 Le tableau suivant présente les méthodes de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) qui doit être implémentée pour un moteur de débogage fonctionnel au minimum (DE) et le contrôle de l’exécution.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continue de s’exécuter tous les threads sont contenus par un programme à partir d’un état arrêté. Requis pour le contrôle de l’exécution.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continue de s’exécuter tous les threads sont contenus par un programme à partir d’un état arrêté. Requis pour le contrôle de l’exécution.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Exécute une étape sur le thread donné. Continue de s’exécuter tous les autres threads contenues par le programme. Requis pour le contrôle de l’exécution.|  
  
 Pour les programmes multithreads, vous devez également implémenter la [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) (méthode) et toutes les méthodes de la [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Évaluation de contrôle et l’état d’exécution](../../extensibility/debugger/execution-control-and-state-evaluation.md)
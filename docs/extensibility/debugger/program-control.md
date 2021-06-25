---
title: Contrôle du programme | Microsoft Docs
description: Découvrez les routines du débogage Visual Studio qui se produisent au niveau du programme, telles que l’exécution, l’exécution pas à pas, la poursuite et la suspension/reprise de threads.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b2946309c72fbdddf2794c1da1e773e9a529368
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900709"
---
# <a name="program-control"></a>Contrôle du programme
Dans le débogage Visual Studio, toutes les routines d’exécution pas à pas et de continuation suivantes se produisent au niveau du programme :

- Définition de l’instruction suivante, c’est-à-dire la définition de votre ordinateur sur la prochaine instruction à exécuter dans un environnement de cadre particulier

- En cours d’exécution, autrement dit, en continuant à quitter le mode pas à pas

- Exécution pas à pas de l’instruction suivante

- Poursuite du mode pas à pas actif

- Suspension des threads contenus dans le programme

- Reprise des threads contenus dans le programme

> [!NOTE]
> L’affichage de la pile des appels est implémenté au niveau du thread. Pour énumérer les informations de frame lors de l’affichage de la pile des appels d’un thread, vous devez implémenter toutes les méthodes de l’interface [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) .

## <a name="methods-of-program-control"></a>Méthodes de contrôle de programme
 Le tableau suivant présente les méthodes de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) qui doivent être implémentées pour un moteur de débogage fonctionnel minimal (de) et un contrôle d’exécution.

|Méthode|Description|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Poursuit l’exécution de tous les threads contenus dans un programme à partir d’un état arrêté. Requis pour le contrôle de l’exécution.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Poursuit l’exécution de tous les threads contenus dans un programme à partir d’un état arrêté. Requis pour le contrôle de l’exécution.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Exécute une étape sur le thread donné. Poursuit l’exécution de tous les autres threads contenus dans le programme. Requis pour le contrôle de l’exécution.|

 Pour les programmes multithreads, vous devez également implémenter la méthode [IDebugProgram2 :: enumthreads,](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) et toutes les méthodes de l’interface [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) .

## <a name="see-also"></a>Voir aussi
- [Contrôle d’exécution et évaluation de l’État](../../extensibility/debugger/execution-control-and-state-evaluation.md)

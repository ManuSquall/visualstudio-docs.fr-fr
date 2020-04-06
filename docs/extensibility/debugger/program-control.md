---
title: Contrôle du programme (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e77e233050c5ce10aef5053f82c8d26cb984b85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738232"
---
# <a name="program-control"></a>Contrôle du programme
Dans Visual Studio débogage, toutes les étapes suivantes et les routines continues se produisent au niveau du programme:

- Définir la déclaration suivante, c’est-à-dire régler votre ordinateur à l’instruction suivante à exécuter dans un environnement de cadre particulier

- Exécution, c’est-à-dire, continuer à sortir du mode de pas

- Passer à l’instruction suivante

- Continuer avec le mode de pas actuel

- Suspension des fils contenus par le programme

- Reprise des fils contenus par le programme

> [!NOTE]
> L’affichage de la pile d’appels est implémenté au niveau du thread. Pour énumérer les informations de cadre lors de la visualisation de la pile d’appels pour un thread, vous devez implémenter toutes les méthodes de l’interface [IEnumDebugFrameInfo2.](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)

## <a name="methods-of-program-control"></a>Méthodes de contrôle du programme
 Le tableau suivant montre les méthodes [d’IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) qui doivent être mises en œuvre pour un moteur de débogé minimalement fonctionnel (DE) et le contrôle d’exécution.

|Méthode|Description|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continue à exécuter tous les threads contenus par un programme à partir d’un état arrêté. Nécessité d’un contrôle d’exécution.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continue à exécuter tous les threads contenus par un programme à partir d’un état arrêté. Nécessité d’un contrôle d’exécution.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Effectue une étape sur le thread donné. Continue d’exécuter tous les autres threads contenus par le programme. Nécessité d’un contrôle d’exécution.|

 Pour les programmes multithreaded, vous devez également implémenter la méthode [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) et toutes les méthodes de [l’interface IEnumDebugThreads2.](../../extensibility/debugger/reference/ienumdebugthreads2.md)

## <a name="see-also"></a>Voir aussi
- [Contrôle des exécutions et évaluation de l’État](../../extensibility/debugger/execution-control-and-state-evaluation.md)

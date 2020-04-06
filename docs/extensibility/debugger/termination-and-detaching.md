---
title: Termination et détachement Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b88255d618ce42fa55d878f192d31523ba3f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712489"
---
# <a name="termination-and-detaching"></a>Termination et détachement
La section suivante décrit la résiliation normale.

## <a name="discussion"></a>Discussions
 Après la poursuite de [l’interface IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2,](../../extensibility/debugger/reference/idebugentrypointevent2.md) s’il n’y a pas de points d’arrêt, d’exceptions, d’erreurs de temps d’exécution ou de boucles infinies dans l’application à déboguer, le programme étant débbugged s’exécute à son terme. Ce processus est la résiliation normale.

 Vous devez envoyer un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) pour implémenter la résiliation normale. La terminaison normale nécessite l’exécution de la méthode [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) méthode.

## <a name="see-also"></a>Voir aussi
- [Création d’un moteur de débogé personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)

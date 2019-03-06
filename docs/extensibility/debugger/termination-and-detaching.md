---
title: Arrêt et détachement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a727f30f6070b44e16dbc4206ac56e0224ff3d67
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682165"
---
# <a name="termination-and-detaching"></a>Arrêt et détachement
La section suivante décrit une fin normale.

## <a name="discussion"></a>Discussion
 Après le [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interface se poursuit, si aucun des points d’arrêt, exceptions, erreurs d’exécution, ou les boucles infinies dans l’application à déboguer, le programme en cours de débogage s’exécute jusqu'à son achèvement. Ce processus est une fin normale.

 Vous devez envoyer un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) pour implémenter une fin normale. Arrêt normal requiert l’exécution le [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) (méthode).

## <a name="see-also"></a>Voir aussi
- [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)
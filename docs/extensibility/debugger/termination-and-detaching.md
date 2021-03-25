---
title: Terminaison et détachement | Microsoft Docs
description: La fin normale signifie qu’un programme en cours de débogage s’exécute jusqu’à son achèvement sans points d’arrêt, exceptions, erreurs d’exécution ou boucles infinies.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8662809b50dbfec3046af1d0d6b6fa151c3a33e0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057830"
---
# <a name="termination-and-detaching"></a>Arrêt et détachement
La section suivante décrit l’arrêt normal.

## <a name="discussion"></a>Discussions
 Après la poursuite de l’interface [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , s’il n’y a pas de points d’arrêt, d’exceptions, d’erreurs d’exécution ou de boucles infinies dans l’application à déboguer, le programme en cours de débogage s’exécute jusqu’à son achèvement. Ce processus est un arrêt normal.

 Vous devez envoyer un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) pour implémenter l’arrêt normal. L’arrêt normal requiert l’exécution de la méthode [IDebugProgramDestroyEvent2 :: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>Voir aussi
- [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)

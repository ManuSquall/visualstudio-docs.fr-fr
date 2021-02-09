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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6ac3e8517ee99dcd52261eb87b6cee3954793d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895893"
---
# <a name="termination-and-detaching"></a>Arrêt et détachement
La section suivante décrit l’arrêt normal.

## <a name="discussion"></a>Discussions
 Après la poursuite de l’interface [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , s’il n’y a pas de points d’arrêt, d’exceptions, d’erreurs d’exécution ou de boucles infinies dans l’application à déboguer, le programme en cours de débogage s’exécute jusqu’à son achèvement. Ce processus est un arrêt normal.

 Vous devez envoyer un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) pour implémenter l’arrêt normal. L’arrêt normal requiert l’exécution de la méthode [IDebugProgramDestroyEvent2 :: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>Voir aussi
- [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)

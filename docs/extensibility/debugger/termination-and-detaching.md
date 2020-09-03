---
title: Terminaison et détachement | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712489"
---
# <a name="termination-and-detaching"></a>Arrêt et détachement
La section suivante décrit l’arrêt normal.

## <a name="discussion"></a>Discussion
 Après la poursuite de l’interface [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , s’il n’y a pas de points d’arrêt, d’exceptions, d’erreurs d’exécution ou de boucles infinies dans l’application à déboguer, le programme en cours de débogage s’exécute jusqu’à son achèvement. Ce processus est un arrêt normal.

 Vous devez envoyer un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) pour implémenter l’arrêt normal. L’arrêt normal requiert l’exécution de la méthode [IDebugProgramDestroyEvent2 :: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>Voir aussi
- [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)

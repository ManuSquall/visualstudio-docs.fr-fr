---
title: Arrêt et le détachement | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5af218098f6d79cf6208c66b314c35d2471af15
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127372"
---
# <a name="termination-and-detaching"></a>Arrêt et le détachement
La section suivante décrit une fin normale.  
  
## <a name="discussion"></a>Discussion  
 Après le [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interface continue, s’il n’y aucun points d’arrêt, les exceptions, les erreurs d’exécution ou les boucles infinies dans l’application à déboguer le programme en cours de débogage s’exécute jusqu'à son achèvement. Il s’agit d’une fin normale.  
  
 Vous devez envoyer une [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) pour implémenter une fin normale. Cela requiert l’implémentation du [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)
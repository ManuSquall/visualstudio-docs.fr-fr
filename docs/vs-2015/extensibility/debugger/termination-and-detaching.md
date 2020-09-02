---
title: Terminaison et détachement | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d92fe88826baf19ba66b200990aee7797e91f87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176671"
---
# <a name="termination-and-detaching"></a>Arrêt et détachement
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les éléments suivants décrivent l’arrêt normal.  
  
## <a name="discussion"></a>Discussion  
 Après la poursuite de l’interface [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , s’il n’y a pas de points d’arrêt, d’exceptions, d’erreurs d’exécution ou de boucles infinies dans l’application à déboguer, le programme en cours de débogage s’exécutera jusqu’à la fin. Il s’agit d’un arrêt normal.  
  
 Vous devez envoyer un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) pour implémenter l’arrêt normal. Cela requiert l’implémentation de la méthode [IDebugProgramDestroyEvent2 :: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)

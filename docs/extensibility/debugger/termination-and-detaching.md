---
title: "Arrêt et le détachement | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9efd8e7bdaf9f75f3c3d81f7738d6bfb078cfcb2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="termination-and-detaching"></a>Arrêt et le détachement
La section suivante décrit une fin normale.  
  
## <a name="discussion"></a>Discussion  
 Après le [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interface continue, s’il n’y aucun points d’arrêt, les exceptions, les erreurs d’exécution ou les boucles infinies dans l’application à déboguer le programme en cours de débogage s’exécute jusqu'à son achèvement. Il s’agit d’une fin normale.  
  
 Vous devez envoyer une [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) pour implémenter une fin normale. Cela requiert l’implémentation du [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)
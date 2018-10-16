---
title: Arrêt d’un programme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf972e6bb38d9dcd2995814e885ceb0b071abe29
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294671"
---
# <a name="terminating-a-program"></a>Arrêt d’un programme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Voici une description de l’arrêt d’un programme unique avec un seul thread.  
  
## <a name="termination-process"></a>Processus d’arrêt  
  
1.  L’envoie DE un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) avec valide [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2.  L’envoie DE un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) avec valide [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
 L’IDE repasse en mode design. Le moteur de débogage ou d’un environnement d’exécution appelle [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) pour supprimer le programme à partir du port.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)


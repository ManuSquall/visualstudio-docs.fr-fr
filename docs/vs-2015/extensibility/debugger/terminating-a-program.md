---
title: Arrêt d’un programme | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 6092e7f393eb973980cfca123264326aa0b2388b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505258"
---
# <a name="terminating-a-program"></a>Arrêt d’un programme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [arrêt d’un programme](https://docs.microsoft.com/visualstudio/extensibility/debugger/terminating-a-program).  
  
Voici une description de l’arrêt d’un programme unique avec un seul thread.  
  
## <a name="termination-process"></a>Processus d’arrêt  
  
1.  L’envoie DE un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) avec valide [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2.  L’envoie DE un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) avec valide [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
 L’IDE repasse en mode design. Le moteur de débogage ou d’un environnement d’exécution appelle [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) pour supprimer le programme à partir du port.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)


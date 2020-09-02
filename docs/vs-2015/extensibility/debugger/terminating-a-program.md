---
title: Arrêt d’un programme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f0b9ad248751af0885fa4edc0275be2ede5ddd9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421861"
---
# <a name="terminating-a-program"></a>Arrêt d’un programme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez ci-dessous une description de l’arrêt d’un seul programme avec un seul thread.  
  
## <a name="termination-process"></a>Processus d’arrêt  
  
1. Le DE envoie un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) avec un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)valide.  
  
2. Le DE envoie un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) avec un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)valide.  
  
   L’IDE passe en mode Design. Le moteur de débogage ou l’environnement d’exécution appelle [IDebugPortNotify2 :: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) pour supprimer le programme du port.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)

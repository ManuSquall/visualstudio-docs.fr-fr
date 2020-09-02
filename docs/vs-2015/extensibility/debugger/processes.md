---
title: Processus | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 82718a7ceb7a18f9978840f35ca0c5fce5628e81
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153669"
---
# <a name="processes"></a>Processus
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En termes d’architecture du débogueur, un **processus**:  
  
- Est un conteneur pour un ensemble de programmes. Il est étroitement analogue à un processus Windows, qui est un conteneur pour un ensemble de threads.  
  
- Peut s’identifier à l’aide d’un nom, d’un identificateur ou d’un identificateur physique.  
  
- Peut énumérer tous les programmes en cours d’exécution (et leurs threads).  
  
- Peut se décrire lui-même, le port dans lequel il s’exécute et l’ordinateur qui le contient.  
  
- Peut créer un ou plusieurs programmes, terminer l’un des programmes qu’il crée ou provoquer l’arrêt d’un programme.  
  
- Est représenté par une interface [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , qui est créée lorsque le processus est lancé. Un processus est lancé par le gestionnaire de débogage de session (SDM) ou par [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
  Le package de débogage peut attacher un moteur de débogage (DE) à un processus en appelant [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Cela signifie que le DE est attaché à tous les programmes qui s’exécutent dans le processus qu’il peut gérer. Par exemple, si le common language runtime DE s’attache à un processus, il s’attache uniquement aux programmes qui exécutent le code managé.  
  
## <a name="see-also"></a>Voir aussi  
 [Installés](../../extensibility/debugger/programs.md)   
 [Thèmes](../../extensibility/debugger/threads.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Package de débogage](../../extensibility/debugger/debug-package.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attacher](../../extensibility/debugger/reference/idebugprocess2-attach.md)

---
title: Notifier le Port | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91bedf387fe86c2bf2fefb34e643e581a37c15bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="notifying-the-port"></a>Notifier le Port
Après le lancement d’un programme, le port doit être averti, comme suit :  
  
1.  Lorsqu’un port reçoit un nouveau nœud de programme, il envoie un événement de création de programme à la session de débogage. L’événement s’accompagne d’une interface qui représente le programme.  
  
2.  Le programme pour l’identificateur d’un moteur de débogage (DE) que vous pouvez attacher à des requêtes la session de débogage.  
  
3.  La session de débogage vérifie si le DE figure dans la liste DEs autorisée pour ce programme. La session de débogage Obtient la liste de paramètres de programme actif de la solution, à l’origine passés par le package de débogage.  
  
     Le DE doit se trouver sur la liste autorisée, ou bien le DE ne sera pas attaché au programme.  
  
 Par programme, lorsqu’un port reçoit d’abord un nouveau nœud de programme, il crée un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interface pour représenter le programme.  
  
> [!NOTE]
>  Cela ne doit pas être confondu avec le `IDebugProgram2` interface créée ultérieurement par le moteur de débogage (DE).  
  
 Le port envoie un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) événement de création de programme vers le Gestionnaire de session de débogage (SDM) au moyen de COM `IConnectionPoint` interface.  
  
> [!NOTE]
>  Cela ne doit pas être confondu avec le `IDebugProgramCreateEvent2` interface, qui est ultérieurement envoyé par le DE.  
  
 En même temps que l’interface d’événement lui-même, le port envoie le [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), et [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaces qui représentent le port, traitent, et programmer, respectivement. Les appels SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) pour obtenir le GUID de la DE qui peut déboguer le programme. Le GUID a été obtenu à l’origine à partir de la [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface.  
  
 Le SDM vérifie si le DE figure dans la liste DEs autorisée. Le SDM Obtient la liste de paramètres de programme actif de la solution, à l’origine passés par le package de débogage. Le DE doit se trouver sur la liste autorisée, sans quoi il ne sera pas attaché au programme.  
  
 Une fois que l’identité de la DE est connue, le SDM est prêt à joindre au programme.  
  
## <a name="see-also"></a>Voir aussi  
 [Lancement d’un programme](../../extensibility/debugger/launching-a-program.md)   
 [Attachement d’après le lancement d’un](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
---
title: Notification du Port | Microsoft Docs
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
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ce692e30951c6a74203b71690a26001ccc0b48f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263547"
---
# <a name="notifying-the-port"></a>Notification du port
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Après avoir lancé un programme, le port doit être averti, comme suit :  
  
1.  Lorsqu’un port reçoit un nouveau nœud de programme, il renvoie un événement de création de programme à la session de débogage. L’événement s’accompagne d’une interface qui représente le programme.  
  
2.  La session de débogage interroge le programme pour l’identificateur d’un moteur de débogage (dé) qui permettre attacher à.  
  
3.  La session de débogage vérifie si le DE figure dans la liste DEs autorisée pour ce programme. La session de débogage obtient cette liste à partir des paramètres de programme actif de la solution, à l’origine passés par le package de débogage.  
  
     Le DE doit se trouver sur la liste autorisée, sans quoi le DE ne sera pas attaché au programme.  
  
 Par programmation, lorsqu’un port reçoit tout d’abord un nouveau nœud de programme, il crée un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interface pour représenter le programme.  
  
> [!NOTE]
>  Il ne faut pas confondre avec le `IDebugProgram2` interface créée ultérieurement par le moteur de débogage (dé).  
  
 Le port envoie un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) événement de création de programme au Gestionnaire de débogage de session (SDM) au moyen d’un COM `IConnectionPoint` interface.  
  
> [!NOTE]
>  Il ne faut pas confondre avec le `IDebugProgramCreateEvent2` interface, qui est envoyée plus tard par l’Allemagne.  
  
 Avec l’interface d’événement proprement dit, le port envoie le [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), et [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaces qui représentent le port, traitement, et programmer, respectivement. Les appels SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) pour obtenir le GUID de l’Allemagne qui peut déboguer le programme. Le GUID a été obtenu à l’origine à partir de la [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface.  
  
 Le SDM vérifie si le DE figure dans la liste DEs autorisée. Le SDM obtient cette liste à partir des paramètres de programme actif de la solution, à l’origine passés par le package de débogage. Le DE doit se trouver sur la liste autorisée, sans quoi il ne sera pas attaché au programme.  
  
 Une fois que l’identité de l’Allemagne est connue, le SDM est prêt à attacher au programme.  
  
## <a name="see-also"></a>Voir aussi  
 [Lancement d’un programme](../../extensibility/debugger/launching-a-program.md)   
 [Attachement après un lancement](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)


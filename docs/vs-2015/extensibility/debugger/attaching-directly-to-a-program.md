---
title: Attachement directement à un programme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab49163fc1474b541df3bc1b54d336574761baa3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951995"
---
# <a name="attaching-directly-to-a-program"></a>Attachement direct à un programme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les utilisateurs qui souhaitent déboguer des programmes dans un processus qui est déjà en cours d’exécution en général, procédez comme suit :  
  
1. Dans l’IDE, choisissez le **déboguer les processus** commande à partir de la **outils** menu.  
  
    La boîte de dialogue **Processus** s’affiche.  
  
2. Choisir un processus et cliquez sur le **attacher** bouton.  
  
    Le **attacher au processus** boîte de dialogue apparaît, répertoriant tous les moteurs de débogage (DEs) installés sur l’ordinateur.  
  
3. Spécifiez la norme à utiliser pour déboguer le processus sélectionné, puis cliquez sur **OK**.  
  
   Le package de débogage démarre une session de débogage et lui transmet la liste de DEs. La session de débogage à son tour transmet cette liste, ainsi que d’une fonction de rappel pour le processus sélectionné et vous demande ensuite le processus à énumérer ses programmes en cours d’exécution.  
  
   Par programme, en réponse à la demande de l’utilisateur, le package de débogage instancie le Gestionnaire de session de débogage (SDM) et lui passe la liste de DEs sélectionné. En même temps que la liste, le package de débogage transmet le SDM un [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interface. Le package de débogage transmet la liste de pour le processus sélectionné en appelant [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Le SDM appelle ensuite [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) sur le port pour énumérer les programmes en cours d’exécution dans le processus.  
  
   À ce stade, chaque moteur de débogage est attaché à un programme exactement comme indiqué dans [attachement après un lancement](../../extensibility/debugger/attaching-after-a-launch.md), avec deux exceptions.  
  
   Pour plus d’efficacité, DEs, qui sont implémentées pour partager un espace d’adressage avec le SDM sont regroupés afin que chaque dé a un ensemble de programmes, il s’attache à. Dans ce cas, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) appels [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) et transmet un tableau des programmes à attacher à.  
  
   La seconde exception est que les événements de démarrage envoyés par un D’attachement à un programme qui est déjà en cours d’exécution n’incluent pas généralement l’événement de point d’entrée.  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi d’événements de démarrage après un lancement](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)

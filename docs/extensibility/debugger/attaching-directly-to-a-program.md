---
title: "Attachement directement &#224; un programme | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "moteurs de débogage, attacher aux programmes"
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Attachement directement &#224; un programme
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les utilisateurs qui souhaitent aux programmes de débogage dans un processus en cours en général suivent ce processus :  
  
1.  Dans l'IDE de, choisissez la commande de **processus de débogage** le menu pour **Outils** .  
  
     La boîte de dialogue **Processus** s'affiche.  
  
2.  choisissez un processus et cliquez sur le bouton d' **Attacher** .  
  
     La boîte de dialogue d' **Attacher au processus** s'affiche, répertoriant tous les moteurs \(DEs\) de débogage installés sur l'ordinateur.  
  
3.  Spécifiez le à utiliser pour déboguer le processus sélectionné, puis cliquez sur **OK**.  
  
 Le package de débogage démarre une session de débogage et passe la liste DES lui.  La session de débogage passe ensuite cette liste, avec une fonction de rappel, au processus sélectionné, et demande ensuite au processus pour énumérer ses programmes en cours de exécution.  
  
 Par programme, en réponse à la demande de l'utilisateur, le package de débogage instancie le gestionnaire de débogage de \(SDM\) session et passe la liste DES sélectionné à celui\-ci.  avec la liste, le package de débogage passe le SDM une interface d' [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) .  Le package de débogage passe la liste de les au processus sélectionné en appelant [IDebugProcess2 : : Attachement](../../extensibility/debugger/reference/idebugprocess2-attach.md).  Le SDM appelle ensuite [IDebugProcess2 : : EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) sur le port pour énumérer les programmes s'exécutant dans le processus.  
  
 À partir de là, chaque moteur de débogage est attaché à un programme exactement comme indiqué dans [Attachement après un lancement](../../extensibility/debugger/attaching-after-a-launch.md), avec deux exceptions.  
  
 Pour des raisons d'efficacité, le DES qui sont implémentées pour partager un espace d'adressage avec le SDM lui sont regroupés afin que chaque De dispose d'un jeu de programmes se joindra valeur.  Dans ce cas, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) appelle [IDebugEngine2 : : Attachement](../../extensibility/debugger/reference/idebugengine2-attach.md) et le passe un tableau de programmes à l'attachement à.  
  
 La deuxième exception est que les événements de démarrage envoyés par l'un De l'attachement à un programme qui s'exécute déjà n'incluent pas généralement un événement de point d'entrée.  
  
## Voir aussi  
 [L'envoi d'événements de démarrage après le lancement d'un](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
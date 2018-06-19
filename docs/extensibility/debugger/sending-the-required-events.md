---
title: Envoyer les événements requis | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: deeffb814dacc58b1fb3a3f993203139d9b1a081
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126169"
---
# <a name="sending-the-required-events"></a>Envoyer les événements requis
Utilisez cette procédure pour l’envoi d’événements requis.  
  
## <a name="process-for-sending-required-events"></a>Processus d’envoi d’événements requis  
 Les événements suivants sont requis, dans cet ordre, lors de la création d’un débogage du moteur (DE) et en l’attachant à un programme :  
  
1.  Envoyer un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) objet d’événement pour le Gestionnaire de session de débogage (SDM) lors de l’initialisation de la DE un ou plusieurs programmes dans un processus de débogage.  
  
2.  Lorsque le programme à déboguer est attaché à, envoyer un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) objet d’événement pour le SDM. Cet événement peut être un événement d’arrêt, en fonction de votre conception de moteur.  
  
3.  Si le programme est attaché à lorsque le processus est appelé, envoyez un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) objet d’événement pour le SDM pour notifier l’IDE du nouveau thread. Cet événement peut être un événement d’arrêt, en fonction de votre conception de moteur.  
  
4.  Envoyer un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) objet d’événement pour le SDM lorsque le programme débogué est le chargement terminé ou quand l’attachement au programme est terminé. Cet événement doit être un événement d’arrêt.  
  
5.  Si l’application à déboguer est lancée, envoyez un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) objet d’événement pour le SDM lors de la première instruction du code dans l’architecture de l’exécution est sur le point d’être exécutée. Cet événement est toujours un arrêt. Lors de l’exécution pas à pas dans la session de débogage, l’IDE s’arrête sur cet événement.  
  
> [!NOTE]
>  De nombreux langages utilisent initialiseurs globales ou des fonctions externes, précompilées (à partir de la bibliothèque CRT ou le _Main) au début du code. Si la langue du programme que vous déboguez contient un de ces types d’éléments avant le point d’entrée initial, ce code est exécuté et l’événement de point d’entrée est envoyé lorsque l’utilisateur point d’entrée, tel que **principal** ou `WinMain`, a été atteint.  
  
## <a name="see-also"></a>Voir aussi  
 [Activation d’un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
---
title: Attachement au programme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab9301f31976b084c3c8565329dca248503e40ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839529"
---
# <a name="attaching-to-the-program"></a>Attachement au programme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Une fois que vous avez enregistré vos programmes avec le port approprié, vous devez attacher le débogueur au programme que vous souhaitez déboguer.  
  
## <a name="choosing-how-to-attach"></a>Choix de la méthode d’attachement  
 Le gestionnaire de débogage de session (SDM) tente de s’attacher au programme en cours de débogage de trois façons.  
  
1. Pour les programmes qui sont lancés par le moteur de débogage par le biais de la méthode [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (typique des langages interprétés, par exemple), le SDM obtient l’interface [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) à partir de l’objet [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associé au programme en cours d’attachement. Si le SDM peut obtenir l' `IDebugProgramNodeAttach2` interface, le SDM appelle ensuite la méthode [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . La `IDebugProgramNodeAttach2::OnAttach` méthode retourne `S_OK` pour indiquer qu’elle n’a pas été attachée au programme et que d’autres tentatives peuvent être effectuées pour attacher le programme.  
  
2. Si le SDM peut obtenir l’interface [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) à partir du programme auquel il est attaché, le SDM appelle la méthode d' [attachement](../../extensibility/debugger/reference/idebugprogramex2-attach.md) . Cette approche est courante pour les programmes qui ont été lancés à distance par le fournisseur de port.  
  
3. Si le programme ne peut pas être attaché par le biais des `IDebugProgramNodeAttach2::OnAttach` `IDebugProgramEx2::Attach` méthodes ou, le SDM charge le moteur de débogage (s’il n’est pas déjà chargé) en appelant la `CoCreateInstance` fonction, puis appelle la méthode d' [attachement](../../extensibility/debugger/reference/idebugengine2-attach.md) . Cette approche est courante pour les programmes lancés localement par un fournisseur de ports.  
  
    Il est également possible pour un fournisseur de port personnalisé d’appeler la `IDebugEngine2::Attach` méthode dans l’implémentation du fournisseur de port personnalisé de la `IDebugProgramEx2::Attach` méthode. En général, dans ce cas, le fournisseur de port personnalisé lance le moteur de débogage sur l’ordinateur distant.  
  
   La pièce jointe est obtenue lorsque le gestionnaire de débogage de session (SDM) appelle la méthode [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
   Si vous exécutez votre DE dans le même processus que l’application à déboguer, vous devez implémenter les méthodes suivantes de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
  Une fois la `IDebugEngine2::Attach` méthode appelée, procédez comme suit dans votre implémentation de la `IDebugEngine2::Attach` méthode :  
  
1. Envoie un objet d’événement [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) au SDM. Pour plus d’informations, consultez [envoi d’événements](../../extensibility/debugger/sending-events.md).  
  
2. Appelez la méthode [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sur l’objet [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) qui a été passé à la `IDebugEngine2::Attach` méthode.  
  
     Cela retourne un `GUID` qui est utilisé pour identifier le programme. Le `GUID` doit être stocké dans l’objet qui représente le programme local dans le de, et il doit être retourné lorsque la `IDebugProgram2::GetProgramId` méthode est appelée sur l' `IDebugProgram2` interface.  
  
    > [!NOTE]
    > Si vous implémentez l' `IDebugProgramNodeAttach2` interface, le programme `GUID` est passé à la `IDebugProgramNodeAttach2::OnAttach` méthode. `GUID`Utilisé pour le programme `GUID` retourné par la `IDebugProgram2::GetProgramId` méthode.  
  
3. Envoie un objet d’événement [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) pour notifier au SDM que l' `IDebugProgram2` objet local a été créé pour représenter le programme au de. Pour plus d’informations, consultez [envoi d’événements](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    > Il ne s’agit pas du même `IDebugProgram2` objet que celui qui a été passé dans la `IDebugEngine2::Attach` méthode. L’objet précédemment passé `IDebugProgram2` est reconnu par le port uniquement et est un objet distinct.  
  
## <a name="see-also"></a>Voir aussi  
 [Pièce jointe basée sur le lancement](../../extensibility/debugger/launch-based-attachment.md)   
 [Envoi d’événements](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Attacher](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attacher](../../extensibility/debugger/reference/idebugengine2-attach.md)

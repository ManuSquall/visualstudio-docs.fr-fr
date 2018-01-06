---
title: Attachement au programme | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 75b532005bf4aeb471aa16ecfc6ac8ff508e3c7f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="attaching-to-the-program"></a>Attachement au programme
Une fois que vous avez enregistré vos programmes avec le port approprié, vous devez attacher le débogueur au programme que vous souhaitez déboguer.  
  
## <a name="choosing-how-to-attach"></a>Choix du mode d’attachement  
 Il existe trois façons dans lequel le Gestionnaire de session de débogage (SDM) tente d’attacher au programme en cours de débogage.  
  
1.  Pour les programmes qui sont lancées par le moteur de débogage par le biais du [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) Obtient de le SDM (méthode) (standard de langages interprétés, par exemple), le [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) à partir de l’interface le [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) objet associé au programme en cours d’attachement. Si le SDM peut obtenir le `IDebugProgramNodeAttach2` le SDM interface, puis appelle la [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) (méthode). Le `IDebugProgramNodeAttach2::OnAttach` retourne de la méthode `S_OK` pour indiquer qu’il n’avez pas attaché au programme et que les autres tentatives peuvent être effectuées à joindre au programme.  
  
2.  Si le SDM peut obtenir le [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) de l’interface du programme en cours d’attachement pour les appels SDM le [attacher](../../extensibility/debugger/reference/idebugprogramex2-attach.md) (méthode). Cette approche est généralement utilisée pour les programmes qui ont été lancées à distance par le fournisseur de port.  
  
3.  Si le programme ne peut pas être connecté via le `IDebugProgramNodeAttach2::OnAttach` ou `IDebugProgramEx2::Attach` méthodes, le SDM charge le moteur de débogage (si pas déjà chargé) en appelant le `CoCreateInstance` (fonction), puis appelle la [attacher](../../extensibility/debugger/reference/idebugengine2-attach.md) (méthode). Cette approche est généralement utilisée pour les programmes lancées localement par un fournisseur de port.  
  
     Il est également possible pour un fournisseur de port personnalisé appeler le `IDebugEngine2::Attach` méthode dans l’implémentation du fournisseur de port personnalisé de la `IDebugProgramEx2::Attach` (méthode). En général, dans ce cas, le fournisseur de port personnalisé lance le moteur de débogage sur l’ordinateur distant.  
  
 Pièce jointe est atteint lorsque le Gestionnaire de session de débogage (SDM) appelle le [attacher](../../extensibility/debugger/reference/idebugengine2-attach.md) (méthode).  
  
 Si vous exécutez votre DE dans le même processus que l’application à déboguer, vous devez implémenter les méthodes suivantes de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 Après le `IDebugEngine2::Attach` est appelée, procédez comme suit dans votre implémentation de la `IDebugEngine2::Attach` méthode :  
  
1.  Envoyer un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) objet d’événement pour le SDM. Pour plus d’informations, consultez [envoyer des événements](../../extensibility/debugger/sending-events.md).  
  
2.  Appelez le [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) méthode sur le [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objet qui a été passé à la `IDebugEngine2::Attach` (méthode).  
  
     Cette opération retourne un `GUID` qui est utilisé pour identifier le programme. Le `GUID` doivent être stockées dans l’objet que représente l’ordinateur local du programme pour le DE, et il doit être retourné lorsque le `IDebugProgram2::GetProgramId` méthode est appelée sur le `IDebugProgram2` interface.  
  
    > [!NOTE]
    >  Si vous implémentez le `IDebugProgramNodeAttach2` interface du programme `GUID` est passé à la `IDebugProgramNodeAttach2::OnAttach` (méthode). Cela `GUID` est utilisé pour le programme `GUID` retournée par le `IDebugProgram2::GetProgramId` (méthode).  
  
3.  Envoyer un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) objet d’événement pour avertir le SDM qui local `IDebugProgram2` objet a été créé pour représenter le programme à le DE. Pour plus d’informations, consultez [envoyer des événements](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Cela n’est pas le même `IDebugProgram2` objet qui a été passée dans le `IDebugEngine2::Attach` (méthode). Précédemment passé `IDebugProgram2` objet n’est reconnu par le port uniquement et est un objet distinct.  
  
## <a name="see-also"></a>Voir aussi  
 [Pièce jointe de lancement](../../extensibility/debugger/launch-based-attachment.md)   
 [Envoi d’événements](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Joindre](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attacher](../../extensibility/debugger/reference/idebugengine2-attach.md)
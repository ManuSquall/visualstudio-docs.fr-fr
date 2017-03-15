---
title: "Attacher au programme | Microsoft Docs"
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
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Attacher au programme
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Après avoir enregistré vos programmes avec le port approprié, vous devez attacher le débogueur au programme que vous voulez déboguer.  
  
## Choisir de l'attachement  
 Il existe trois façons dont le gestionnaire de débogage de session \(SDM\) tente de s'attacher au programme en cours de débogage.  
  
1.  Pour les programmes qui sont lancées par le moteur de débogage via la méthode d' [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) \(standard des langages interprètes, par exemple\), le SDM obtient l'interface d' [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) de l'objet d' [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associé au programme en cours attaché.  Si le SDM peut obtenir l'interface d' `IDebugProgramNodeAttach2` , le SDM appelle ensuite la méthode d' [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .  La méthode d' `IDebugProgramNodeAttach2::OnAttach` retourne `S_OK` pour indiquer qu'elle ne dispose pas attachée le programme et que d'autres tentatives peuvent être effectuées attachement au programme.  
  
2.  Si le SDM peut obtenir l'interface d' [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) du programme en cours attaché, le SDM appelle la méthode d' [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) .  Cette approche est généralement utilisé pour les programmes lancées à distance par le fournisseur de port.  
  
3.  Si le programme ne peut pas être attaché via les méthodes d' `IDebugProgramNodeAttach2::OnAttach` ou d' `IDebugProgramEx2::Attach` , les charges de SDM le moteur de débogage \(si ce n'est déjà chargé\) en appelant la fonction de `CoCreateInstance` et appelle ensuite la méthode d' [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) .  Cette approche est typique pour les programmes s'exécutent localement par un fournisseur de port.  
  
     Il est également possible qu'un fournisseur de port appelle la méthode d' `IDebugEngine2::Attach` dans l'implémentation personnalisée du fournisseur de port de la méthode d' `IDebugProgramEx2::Attach` .  En général dans ce cas, le fournisseur de port lance le moteur de débogage sur l'ordinateur distant.  
  
 La pièce jointe est réalisée lorsque le gestionnaire de débogage de \(SDM\) session appelle la méthode d' [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
 Si vous exécutez votre De dans le même processus que l'application à déboguer, vous devez implémenter les méthodes suivantes pour [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 Une fois que la méthode d' `IDebugEngine2::Attach` appelée, suivez ces étapes dans votre implémentation de la méthode d' `IDebugEngine2::Attach` :  
  
1.  envoyez un objet événement d' [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) au SDM.  Pour plus d'informations, consultez [L'envoi d'événements](../../extensibility/debugger/sending-events.md).  
  
2.  Appelez la méthode d' [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sur l'objet d' [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) passé à la méthode d' `IDebugEngine2::Attach` .  
  
     Retourne `GUID` utilisé pour identifier le programme.  `GUID` doit être stocké dans l'objet qui représente le programme local au De, et il doit être retourné lorsque la méthode d' `IDebugProgram2::GetProgramId` est appelée sur l'interface d' `IDebugProgram2` .  
  
    > [!NOTE]
    >  si vous implémentez l'interface d' `IDebugProgramNodeAttach2` , `GUID` du programme est passé à la méthode d' `IDebugProgramNodeAttach2::OnAttach` .  cet `GUID` est utilisé pour `GUID` du programme retourné par la méthode d' `IDebugProgram2::GetProgramId` .  
  
3.  envoyez un objet événement d' [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) pour informer le SDM que l'objet local d' `IDebugProgram2` a été créé pour représenter le programme au De.  Pour plus d'informations, consultez [L'envoi d'événements](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Ce n'est pas le même objet d' `IDebugProgram2` qui a été passé à la méthode d' `IDebugEngine2::Attach` .  L'objet précédemment passé d' `IDebugProgram2` est identifié par le port uniquement et est un objet distinct.  
  
## Voir aussi  
 [Basé sur le lancement de pièce jointe](../../extensibility/debugger/launch-based-attachment.md)   
 [L'envoi d'événements](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
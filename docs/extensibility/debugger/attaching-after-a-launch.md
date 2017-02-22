---
title: "Attachement d&#39;apr&#232;s le lancement d&#39;un | Microsoft Docs"
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
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Attachement d&#39;apr&#232;s le lancement d&#39;un
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Une fois qu'un programme a été lancé, la session de débogage est prête à joindre le \(DE\) moteur de débogage à ledit programme.  
  
## décisions de conception  
 Étant donné que la communication est plus facile dans un espace d'adressage partagé, vous devez décider s'il est plus raisonnable de faciliter la communication entre la session de débogage et le De, ou entre le De et le programme.  Choisissez entre les éléments suivants :  
  
-   S'il est plus raisonnable de faciliter la communication entre la session de débogage et De, la session de débogage crée le De et indique au De pour attacher au programme.  Cela permet la session de débogage et De jeu dans un espace d'adressage, et l'environnement d'exécution et programme ensemble dans un autre.  
  
-   S'il est plus raisonnable de faciliter la communication entre le De et le programme, l'environnement d'exécution crée le De.  Cela permet au SDM dans un espace d'adressage, et le De, environnement d'exécution, et programme ensemble dans un autre.  Il s'agit d'un type De qui est implémentée avec un interpréteur pour exécuter des langages prédéfinis.  
  
    > [!NOTE]
    >  Comment les garbage collection au programme est implémentation\-dépendant.  la communication entre le De et le programme est également implémentation\-dépendant.  
  
## Implémentation  
 Par programme, lorsque le gestionnaire de débogage de session \(SDM\) reçoit d'abord l'objet d' [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme à exécuter, il appelle la méthode d' [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) , en lui passant un objet d' [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , qui est utilisé ultérieurement afin de passer des événements de débogage vers le SDM.  La méthode `IDebugProgram2::Attach` appelle ensuite la méthode [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md).  Pour plus d'informations sur la façon dont le SDM reçoit l'interface d' `IDebugProgram2` , consultez [Notifier le Port](../../extensibility/debugger/notifying-the-port.md).  
  
 Si votre De doit s'exécuter dans le même espace d'adressage que le programme débogué, généralement parce que le De fait partie d'un interpréteur exécutant un script, la méthode d' `IDebugProgramNodeAttach2::OnAttach` retourne `S_FALSE`, indiquant qu'elle a terminé le processus d'attachement.  
  
 Si, en revanche, le De fonctions dans l'espace d'adressage du SDM, la méthode d' `IDebugProgramNodeAttach2::OnAttach` retourne `S_OK` ou d'une interface [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) n'est pas implémentée du tout sur l'objet d' [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associé au programme en cours de débogage.  Dans ce cas, la méthode d' [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) est finalement appelée pour terminer l'opération d'attachement.  
  
 Dans ce dernier cas, vous devez appeler la méthode d' [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sur l'objet d' `IDebugProgram2` passé à la méthode d' `IDebugEngine2::Attach` , enregistre `GUID` dans l'objet local de programme, et retourne cet `GUID` lorsque la méthode d' `IDebugProgram2::GetProgramId` est ensuite appelée sur cet objet.  `GUID` est utilisé pour identifier le programme uniquement entre les différents composants de débogage.  
  
 Notez que dans le cas de la méthode d' `IDebugProgramNodeAttach2::OnAttach` retournant `S_FALSE`, `GUID` à utiliser pour le programme est passé à cette méthode et c'est la méthode d' `IDebugProgramNodeAttach2::OnAttach` qui définit `GUID` sur l'objet local de programme.  
  
 Le du est désormais attaché au programme et prêt pour envoyer tous les événements de démarrage.  
  
## Voir aussi  
 [Attachement directement à un programme](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Notifier le Port](../../extensibility/debugger/notifying-the-port.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
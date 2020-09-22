---
title: Attachement après un lancement | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 693cf6d746f51862415f2f30e46d48a998047f14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840192"
---
# <a name="attaching-after-a-launch"></a>Attachement après un lancement
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Une fois qu’un programme a été lancé, la session de débogage est prête à attacher le moteur de débogage (DE) à ce programme.  
  
## <a name="design-decisions"></a>Décisions de conception  
 Étant donné que la communication est plus facile dans un espace d’adressage partagé, vous devez décider s’il est plus logique de faciliter la communication entre la session de débogage et le ou entre le et le programme. Choisissez l’une des options suivantes :  
  
- S’il est plus logique de faciliter la communication entre la session DE débogage et le, la session de débogage co-crée le DE et demande au DE s’attacher au programme. Cela laisse la session de débogage et regroupe dans un espace d’adressage, et l’environnement d’exécution et le programme dans un autre.  
  
- S’il est plus logique de faciliter la communication entre le et le programme, l’environnement d’exécution co-crée le DE. Cela laisse le SDM dans un espace d’adressage, et l’environnement DE, d’exécution et le programme dans un autre. Il s’agit généralement d’un de qui est implémenté avec un interpréteur pour exécuter des langages de script.  
  
    > [!NOTE]
    > La façon dont le s’attache au programme dépend de l’implémentation. La communication entre le et le programme dépend également de l’implémentation.  
  
## <a name="implementation"></a>Implémentation  
 Par programmation, lorsque le gestionnaire de débogage de session (SDM) reçoit d’abord l’objet [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme à lancer, il appelle la méthode [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) , en lui passant un objet [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , qui est ensuite utilisé pour passer les événements de débogage au SDM. La `IDebugProgram2::Attach` méthode appelle ensuite la méthode [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Pour plus d’informations sur la façon dont le SDM reçoit l' `IDebugProgram2` interface, consultez [notification du port](../../extensibility/debugger/notifying-the-port.md).  
  
 Si votre DE doit s’exécuter dans le même espace d’adressage que le programme en cours de débogage, en général parce que le DE fait partie d’un interpréteur qui exécute un script, la `IDebugProgramNodeAttach2::OnAttach` méthode retourne `S_FALSE` , indiquant qu’elle a terminé le processus d’attachement.  
  
 Si, en revanche, le DE s’exécute dans l’espace d’adressage du SDM, la `IDebugProgramNodeAttach2::OnAttach` méthode retourne `S_OK` ou l’interface [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) n’est pas implémentée du tout sur l’objet [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associé au programme en cours de débogage. Dans ce cas, la méthode d' [attachement](../../extensibility/debugger/reference/idebugengine2-attach.md) est finalement appelée pour terminer l’opération d’attachement.  
  
 Dans ce dernier cas, vous devez appeler la méthode [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sur l' `IDebugProgram2` objet qui a été passé à la `IDebugEngine2::Attach` méthode, stocker le `GUID` dans l’objet programme local et le retourner `GUID` lorsque la `IDebugProgram2::GetProgramId` méthode est appelée par la suite sur cet objet. Le `GUID` est utilisé pour identifier le programme de manière unique parmi les différents composants de débogage.  
  
 Notez que, dans le cas de la `IDebugProgramNodeAttach2::OnAttach` méthode qui retourne `S_FALSE` , le `GUID` à utiliser pour le programme est passé à cette méthode et c’est la `IDebugProgramNodeAttach2::OnAttach` méthode qui définit le `GUID` sur l’objet programme local.  
  
 Le DE est maintenant attaché au programme et prêt à envoyer des événements de démarrage.  
  
## <a name="see-also"></a>Voir aussi  
 [Attachement direct à un programme](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Notification du port](../../extensibility/debugger/notifying-the-port.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Attacher](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attacher](../../extensibility/debugger/reference/idebugengine2-attach.md)

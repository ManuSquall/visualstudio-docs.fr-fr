---
title: "Attachement d’après le lancement d’un | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 890023b8336f130cf3b8cfcfe640da46af9cf0d1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="attaching-after-a-launch"></a>Attachement d’après le lancement d’un
Après le lancement d’un programme, la session de débogage est prête à attacher le moteur de débogage (DE) ce programme.  
  
## <a name="design-decisions"></a>Décisions de conception  
 Étant donné que la communication est plus facile au sein d’un espace d’adressage partagé, vous devez décider s’il est plus judicieux pour faciliter la communication entre la session de débogage et DE, ou entre les périphériques et le programme. Le choix entre les éléments suivants :  
  
-   S’il est plus judicieux pour faciliter la communication entre la session de débogage et DE, la session de débogage crée le DE et vous demande le DE à joindre au programme. Cela laisse la session de débogage et DE ensemble dans un espace d’adressage et l’environnement d’exécution et le programme dans un autre.  
  
-   S’il est plus judicieux pour faciliter la communication entre les périphériques et le programme, puis l’environnement d’exécution crée le DE. Cela laisse le SDM dans un espace d’adressage et le DE, un environnement d’exécution et un programme dans un autre. Ceci est normal d’un DE est implémenté avec un interpréteur pour exécuter des langages de script.  
  
    > [!NOTE]
    >  Comment le D’attache au programme est dépendant de l’implémentation. Communication entre les périphériques et le programme est également dépend de l’implémentation.  
  
## <a name="implementation"></a>Implémentation  
 Par programme, lorsque le Gestionnaire de session de débogage (SDM) reçoit d’abord le [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objet qui représente le programme à exécuter, il appelle la [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) méthode, en lui passant un [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) objet, qui est plus récente est utilisé pour passer les événements de débogage à le SDM. Le `IDebugProgram2::Attach` méthode appelle ensuite la [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) (méthode). Pour plus d’informations sur la façon dont le SDM reçoit le `IDebugProgram2` l’interface, consultez [notifier le Port](../../extensibility/debugger/notifying-the-port.md).  
  
 Si votre DE doit s’exécuter dans le même espace d’adressage que le programme débogué, généralement parce que le DE fait partie d’un interpréteur exécutant un script, le `IDebugProgramNodeAttach2::OnAttach` méthode retourne `S_FALSE`, indiquant qu’elle a été le processus d’attachement.  
  
 Si, en revanche, le DE s’exécute dans l’espace d’adressage de la SDM, la `IDebugProgramNodeAttach2::OnAttach` méthode retourne `S_OK` ou [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interface n’est pas implémentée tout en la [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) objet associé au programme en cours de débogage. Dans ce cas, le [attacher](../../extensibility/debugger/reference/idebugengine2-attach.md) méthode est appelée par la suite pour terminer l’opération d’attachement.  
  
 Dans ce cas, vous devez appeler le [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) méthode sur le `IDebugProgram2` objet qui a été passé à la `IDebugEngine2::Attach` (méthode), le magasin du `GUID` dans le programme local de l’objet et retourner cette `GUID` lorsque le `IDebugProgram2::GetProgramId` méthode est appelée par la suite sur cet objet. Le `GUID` est utilisé pour identifier de manière unique le programme sur les différents composants de débogage.  
  
 Notez que dans le cas de la `IDebugProgramNodeAttach2::OnAttach` méthode retournant `S_FALSE`, le `GUID` à utiliser pour le programme est passé à cette méthode, il le `IDebugProgramNodeAttach2::OnAttach` méthode qui définit la `GUID` sur l’objet de programme local.  
  
 Le D’est maintenant attaché au programme et prêt à envoyer les événements de démarrage.  
  
## <a name="see-also"></a>Voir aussi  
 [Attachement directement à un programme](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Notifier le Port](../../extensibility/debugger/notifying-the-port.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Joindre](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attacher](../../extensibility/debugger/reference/idebugengine2-attach.md)
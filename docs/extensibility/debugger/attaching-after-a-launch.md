---
title: Attachement après un lancement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33bc38ca3e0c9b3bde07be48c74c31e4fc5148df
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922208"
---
# <a name="attach-after-a-launch"></a>Attachement après un lancement
Une fois un programme démarre, la session de débogage est prête à attacher le moteur de débogage (dé) dudit programme.  
  
## <a name="design-decisions"></a>Décisions de conception  
 Étant donné que la communication est plus facile au sein d’un espace d’adressage partagé, vous devez choisir entre deux approches de conception : définir la communication entre la session de débogage et l’Allemagne. Ou bien, définir la communication entre l’Allemagne et le programme. Le choix entre les éléments suivants :  
  
-   S’il est plus judicieux de configurer la communication entre la session de débogage et l’Allemagne, la session de débogage crée l’Allemagne et vous demande de l’Allemagne à joindre au programme. Cette conception laisse la session de débogage et DE ensemble dans un espace d’adressage et l’environnement d’exécution et le programme dans un autre.  
  
-   S’il est plus judicieux de configurer la communication entre l’Allemagne et le programme, l’environnement d’exécution crée l’Allemagne. Cette conception laisse le SDM dans un espace d’adressage et l’Allemagne, environnement d’exécution et programme ensemble dans un autre. Cette conception est typique d’un dé est implémentée avec un interpréteur pour exécuter des langages de script.  
  
    > [!NOTE]
    >  Comment le D’attache au programme est dépend de l’implémentation. Communication entre l’Allemagne et le programme est également dépend de l’implémentation.  
  
## <a name="implementation"></a>Implémentation  
 Par programmation, lorsque le Gestionnaire de session de débogage (SDM) reçoit d’abord le [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objet qui représente le programme doit être lancé, il appelle le [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) méthode, en lui transmettant un [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) objet, qui est ultérieur utilisé pour transmettre des événements de débogage vers le SDM. Le `IDebugProgram2::Attach` méthode appelle ensuite la [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) (méthode). Pour plus d’informations sur la façon dont le SDM reçoit le `IDebugProgram2` l’interface, consultez [notification du port](../../extensibility/debugger/notifying-the-port.md).  
  
 Si votre dé doit s’exécuter dans le même espace d’adressage que le programme que vous déboguez : étant donné que l’Allemagne fait généralement partie d’un interpréteur qui exécute un script, le `IDebugProgramNodeAttach2::OnAttach` retourne de la méthode `S_FALSE`. Le `S_FALSE` retour indique qu’il terminé le processus d’attachement.  
  
 Si, toutefois, l’Allemagne s’exécute dans l’espace d’adressage du SDM : le `IDebugProgramNodeAttach2::OnAttach` retourne de la méthode `S_OK`, ou le [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interface n’est pas implémentée du tout dans le [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) objet associée au programme que vous déboguez. Dans ce cas, le [attacher](../../extensibility/debugger/reference/idebugengine2-attach.md) méthode est appelée par la suite pour terminer l’opération d’attachement.  
  
 Dans ce cas, vous devez appeler le [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) méthode sur le `IDebugProgram2` objet qui a été passé à la `IDebugEngine2::Attach` (méthode), le magasin de la `GUID` dans le programme local de l’objet et retournez cette `GUID` lorsque le `IDebugProgram2::GetProgramId` méthode est appelée par la suite sur cet objet. Le `GUID` est utilisé pour identifier de manière unique le programme entre les différents composants de débogage.  
  
 Dans le cas de la `IDebugProgramNodeAttach2::OnAttach` méthode retournant `S_FALSE`, le `GUID` à utiliser pour le programme est passé à cette méthode, il le `IDebugProgramNodeAttach2::OnAttach` méthode qui définit la `GUID` sur l’objet de programme local.  
  
 L’Allemagne est maintenant attaché au programme et prêt à envoyer les événements de démarrage.  
  
## <a name="see-also"></a>Voir aussi  
 [Attachement directement à un programme](../../extensibility/debugger/attaching-directly-to-a-program.md)   
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
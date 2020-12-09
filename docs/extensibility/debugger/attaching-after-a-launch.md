---
title: Attachement après un lancement | Microsoft Docs
description: Lors du lancement d’un programme, la session de débogage est prête à attacher le moteur de débogage au programme. Choisissez une approche de conception pour la communication avec le moteur de débogage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e19d9090126a13b657f53c20d7ec44a793d5376
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913891"
---
# <a name="attach-after-a-launch"></a>Attacher après un lancement
Après le lancement d’un programme, la session de débogage est prête à attacher le moteur de débogage (DE) à ce programme.

## <a name="design-decisions"></a>Choix de conception
 Étant donné que la communication est plus facile dans un espace d’adressage partagé, vous devez choisir entre deux approches de conception : définir la communication entre la session DE débogage et le. Ou définissez la communication entre le programme DE et le programme. Choisissez l’une des options suivantes :

- S’il est plus judicieux de configurer la communication entre la session DE débogage et le, la session de débogage co-crée le DE et demande au DE s’attacher au programme. Cette conception quitte la session de débogage et regroupe dans un espace d’adressage, et l’environnement d’exécution et le programme dans un autre.

- S’il est plus judicieux de configurer la communication entre le et le programme, l’environnement d’exécution co-crée le DE. Cette conception laisse le SDM dans un espace d’adressage et dans l’environnement DE, d’exécution et dans un autre programme. Cette conception est typique d’un qui est implémenté avec un interpréteur pour exécuter des langages de script.

    > [!NOTE]
    > La façon dont le s’attache au programme dépend de l’implémentation. La communication entre le et le programme dépend également de l’implémentation.

## <a name="implementation"></a>Implémentation
 Par programmation, lorsque le gestionnaire de débogage de session (SDM) reçoit d’abord l’objet [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme à lancer, il appelle la méthode [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) , en lui passant un objet [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , qui est ensuite utilisé pour passer les événements de débogage au SDM. La `IDebugProgram2::Attach` méthode appelle ensuite la méthode [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Pour plus d’informations sur la façon dont le SDM reçoit l' `IDebugProgram2` interface, consultez [notification du port](../../extensibility/debugger/notifying-the-port.md).

 Si votre DE doit s’exécuter dans le même espace d’adressage que le programme que vous déboguez : étant donné que le DE fait généralement partie d’un interpréteur qui exécute un script, la `IDebugProgramNodeAttach2::OnAttach` méthode retourne `S_FALSE` . Le `S_FALSE` retour indique qu’il a terminé le processus d’attachement.

 Toutefois, si le est DE s’exécute dans l’espace d’adressage du SDM : la `IDebugProgramNodeAttach2::OnAttach` méthode retourne `S_OK` , ou l’interface [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) n’est pas implémentée du tout sur l’objet [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associé au programme que vous déboguez. Dans ce cas, la méthode d' [attachement](../../extensibility/debugger/reference/idebugengine2-attach.md) est finalement appelée pour terminer l’opération d’attachement.

 Dans ce dernier cas, vous devez appeler la méthode [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sur l' `IDebugProgram2` objet qui a été passé à la `IDebugEngine2::Attach` méthode, stocker le `GUID` dans l’objet programme local et le retourner `GUID` lorsque la `IDebugProgram2::GetProgramId` méthode est appelée par la suite sur cet objet. Le `GUID` est utilisé pour identifier le programme de manière unique parmi les différents composants de débogage.

 Dans le cas de la `IDebugProgramNodeAttach2::OnAttach` méthode `S_FALSE` qui retourne, le `GUID` à utiliser pour le programme est passé à cette méthode et c’est la `IDebugProgramNodeAttach2::OnAttach` méthode qui définit le `GUID` sur l’objet programme local.

 Le DE est maintenant attaché au programme et prêt à envoyer des événements de démarrage.

## <a name="see-also"></a>Voir aussi
- [Attachement direct à un programme](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Notification du port](../../extensibility/debugger/notifying-the-port.md)
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Attacher](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attacher](../../extensibility/debugger/reference/idebugengine2-attach.md)

---
title: Fixation après un lancement (fr) Microsoft Docs
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
ms.openlocfilehash: 3a4ce0a7465891035b43bbb8f6f22f0c064d104c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739283"
---
# <a name="attach-after-a-launch"></a>Attachez après un lancement
Après un lancement du programme, la session de débog est prêt à attacher le moteur de débogé (DE) à ce programme.

## <a name="design-decisions"></a>Choix de conception
 Parce que la communication est plus facile dans un espace d’adresse partagé, vous devez choisir entre deux approches de conception: définir la communication entre la session de déboulant et le DE. Ou, définir la communication entre le DE et le programme. Choisissez entre les éléments suivants :

- S’il est plus logique de mettre en place la communication entre la session de débog et le DE, la session de débog co-crée le DE et demande à l’DE de s’attacher au programme. Cette conception laisse la session de déboguer et DE ensemble dans un espace d’adresse, et l’environnement de run-time et le programme ensemble dans un autre.

- S’il est plus logique de mettre en place la communication entre le DE et le programme, l’environnement de run-time co-crée le DE. Cette conception laisse le SDM dans un espace d’adresse et le DE, environnement de run-time, et programmer ensemble dans un autre. Cette conception est typique d’un DE qui est implémenté avec un interprète pour exécuter des langues scénarisées.

    > [!NOTE]
    > La façon dont le DE s’attache au programme dépend de la mise en œuvre. La communication entre le DE et le programme est également dépendante de la mise en œuvre.

## <a name="implementation"></a>Implémentation
 Sur le plan programmatique, lorsque le gestionnaire de débogé de session (SDM) reçoit pour la première fois [l’objet IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme à lancer, il appelle la méthode [Attach,](../../extensibility/debugger/reference/idebugprogram2-attach.md) en le transmettant un objet [IDebugEventCallback2,](../../extensibility/debugger/reference/idebugeventcallback2.md) qui est ensuite utilisé pour transmettre les événements debug au SDM. La `IDebugProgram2::Attach` méthode appelle alors la méthode [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Pour plus d’informations sur la `IDebugProgram2` façon dont le SDM reçoit l’interface, voir [Notifier le port](../../extensibility/debugger/notifying-the-port.md).

 Si votre DE a besoin d’exécuter dans le même espace d’adresse que le programme que vous débugging: parce que le DE fait généralement partie d’un interprète qui exécute un script, la `IDebugProgramNodeAttach2::OnAttach` méthode revient `S_FALSE`. La `S_FALSE` déclaration indique qu’elle a terminé le processus de fixation.

 Si, cependant, le DE fonctionne dans l’espace `IDebugProgramNodeAttach2::OnAttach` d’adresse du SDM: la méthode revient `S_OK`, ou l’interface [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) n’est pas du tout implémenté sur l’objet [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associé au programme que vous débugging. Dans ce cas, la méthode [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) est finalement appelée pour compléter l’opération de fixation.

 Dans ce dernier cas, vous devez appeler la `IDebugProgram2` méthode [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sur l’objet qui a été `GUID` transmis `IDebugProgram2::GetProgramId` à la `IDebugEngine2::Attach` méthode, stocker l’objet `GUID` dans le programme local, et le retourner lorsque la méthode est ensuite appelée sur cet objet. L’est `GUID` utilisé pour identifier le programme uniquement à travers les différents composants de débogé.

 Dans le cas `IDebugProgramNodeAttach2::OnAttach` du `S_FALSE`retour `GUID` de la méthode, le à utiliser pour `IDebugProgramNodeAttach2::OnAttach` le programme `GUID` est passé à cette méthode et c’est la méthode qui définit l’objet sur le programme local.

 Le DE est maintenant attaché au programme et prêt à envoyer tous les événements de démarrage.

## <a name="see-also"></a>Voir aussi
- [S’attacher directement à un programme](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Notifier le port](../../extensibility/debugger/notifying-the-port.md)
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)

---
title: S’attacher au programme Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f39b489a57ab93ba5f2d116738c591bd53ff95f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739243"
---
# <a name="attach-to-the-program"></a>Joindre au programme
Une fois que vous avez enregistré vos programmes auprès du port approprié, vous devez joindre le débbuggeur au programme que vous souhaitez déboquer.

## <a name="choose-how-to-attach"></a>Choisissez comment joindre
 Il y a trois façons dont le gestionnaire de déboiffé de session (SDM) tente de s’attacher au programme étant débogé.

1. Pour les programmes lancés par le moteur de débogé par la méthode [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (typique des langues interprétées, par exemple), le SDM obtient [l’interface IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) à partir de [l’objet IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associé au programme attaché à. Si le SDM `IDebugProgramNodeAttach2` peut obtenir l’interface, le SDM appelle alors la méthode [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) La `IDebugProgramNodeAttach2::OnAttach` méthode `S_OK` renvoie pour indiquer qu’elle ne s’est pas jointe au programme et que d’autres tentatives peuvent être faites pour s’attacher au programme.

2. Si le SDM peut obtenir [l’interface IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) à partir du programme qui est attaché, le SDM appelle la méthode [Attach.](../../extensibility/debugger/reference/idebugprogramex2-attach.md) Cette approche est typique pour les programmes qui ont été lancés à distance par le fournisseur portuaire.

3. Si le programme ne `IDebugProgramNodeAttach2::OnAttach` peut `IDebugProgramEx2::Attach` pas être fixé par le biais ou les méthodes, le `CoCreateInstance` SDM charge le moteur de débogé (si elle n’est pas déjà chargée) en appelant la fonction, puis appelle la méthode [Attach.](../../extensibility/debugger/reference/idebugengine2-attach.md) Cette approche est typique des programmes lancés localement par un fournisseur portuaire.

    Il est également possible pour un `IDebugEngine2::Attach` fournisseur de port personnalisé d’appeler `IDebugProgramEx2::Attach` la méthode dans la mise en œuvre de la méthode par le fournisseur de ports personnalisés. Typiquement dans ce cas, le fournisseur de port personnalisé lance le moteur de débogé sur la machine à distance.

   La pièce jointe est atteinte lorsque le gestionnaire de déboquement de session (SDM) appelle la méthode [Attach.](../../extensibility/debugger/reference/idebugengine2-attach.md)

   Si vous exécutez votre DE dans le même processus que la demande à déboguer, alors vous devez implémenter les méthodes suivantes de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  Une `IDebugEngine2::Attach` fois la méthode appelée, suivez ces `IDebugEngine2::Attach` étapes dans votre mise en œuvre de la méthode :

1. Envoyer un objet de l’événement [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) au SDM. Pour plus d’informations, voir [Envoyer des événements](../../extensibility/debugger/sending-events.md).

2. Appelez la méthode [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sur [l’objet IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) qui a été transmis à la `IDebugEngine2::Attach` méthode.

     Cela renvoie un `GUID` qui est utilisé pour identifier le programme. Le `GUID` doit être stocké dans l’objet qui représente le programme local `IDebugProgram2::GetProgramId` à la `IDebugProgram2` DE, et il doit être retourné lorsque la méthode est appelée sur l’interface.

    > [!NOTE]
    > Si vous `IDebugProgramNodeAttach2` implémentez l’interface, le programme `GUID` est transmis à la `IDebugProgramNodeAttach2::OnAttach` méthode. Ceci `GUID` est utilisé pour `GUID` le programme `IDebugProgram2::GetProgramId` retourné par la méthode.

3. Envoyer un objet de l’événement [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) pour `IDebugProgram2` aviser le SDM que l’objet local a été créé pour représenter le programme à la DE. Pour plus de détails, voir [Envoyer des événements](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    > Ce n’est `IDebugProgram2` pas le même `IDebugEngine2::Attach` objet qui a été passé dans la méthode. L’objet `IDebugProgram2` précédemment passé est reconnu par le port seulement et est un objet séparé.

## <a name="see-also"></a>Voir aussi
- [Pièce jointe basée sur le lancement](../../extensibility/debugger/launch-based-attachment.md)
- [Envoi des événements](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)

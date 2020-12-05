---
title: Notification du port | Microsoft Docs
description: Découvrez comment le port est notifié après le lancement d’un programme. Cet article contient une description détaillée.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9a838879e7c1eb590bb16cd12a6bf345de8031a
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606617"
---
# <a name="notify-the-port"></a>Notifier le port
Après le lancement d’un programme, le port doit être notifié, comme suit :

1. Lorsqu’un port reçoit un nouveau nœud de programme, il renvoie un événement de création de programme à la session de débogage. L’événement comporte une interface qui représente le programme.

2. La session de débogage interroge le programme sur l’identificateur d’un moteur de débogage (DE) pouvant être attaché à.

3. La session de débogage vérifie si le DE est dans la liste des autorisés pour ce programme. La session de débogage obtient cette liste à partir des paramètres de programme actifs de la solution, qui lui sont passés à l’origine par le package de débogage.

    Le DE doit figurer dans la liste autorisée, sinon le DE ne sera pas attaché au programme.

   Par programmation, lorsqu’un port reçoit d’abord un nouveau nœud de programme, il crée une interface [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) pour représenter le programme.

> [!NOTE]
> Cela ne doit pas être confondu avec l' `IDebugProgram2` interface créée ultérieurement par le moteur de débogage (de).

 Le port envoie un événement de création de programme [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) au gestionnaire de débogage de session (SDM) au moyen d’une `IConnectionPoint` interface com.

> [!NOTE]
> Cela ne doit pas être confondu avec l' `IDebugProgramCreateEvent2` interface, qui est envoyée plus tard par le de.

 Avec l’interface d’événement elle-même, le port envoie les interfaces [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)et [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , qui représentent respectivement le port, le processus et le programme. Le SDM appelle [IDebugProgram2 :: GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) pour récupérer le GUID du qui peut déboguer le programme. Le GUID a été obtenu à l’origine à partir de l’interface [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .

 Le SDM vérifie si le DE est dans la liste des autorisées. Le SDM obtient cette liste à partir des paramètres de programme actifs de la solution, qui lui sont passés à l’origine par le package de débogage. La valeur DE doit figurer dans la liste autorisée, sinon elle ne sera pas attachée au programme.

 Une fois que l’identité du est connue, le SDM est prêt à l’attacher au programme.

## <a name="see-also"></a>Voir aussi
- [Lancement d’un programme](../../extensibility/debugger/launching-a-program.md)
- [Attacher après un lancement](../../extensibility/debugger/attaching-after-a-launch.md)
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)

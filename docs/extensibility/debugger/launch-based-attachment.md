---
title: Pièce jointe basée sur le lancement (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4910a97350366500b56593ec0076fdf0990b6d8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738462"
---
# <a name="launch-based-attachment"></a>Pièce jointe basée sur le lancement
La pièce jointe basée sur le lancement à un programme est automatique. Lorsque le processus d’hébergement du programme est lancé par le SDM, la pièce jointe basée sur le lancement suit un chemin similaire à celui de la méthode d’attachement manuel. Pour plus d’informations, voir [Joindre au programme](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Le processus d’attachement
 La principale différence est la séquence des événements suivant **l’appel Attach,** comme suit :

1. Envoyer un objet de l’événement **IDebugEngineCreateEvent2** au SDM. Pour plus de détails, voir [Envoyer les événements](../../extensibility/debugger/sending-events.md).

2. Appelez `IDebugProgram2::GetProgramId` la méthode sur l’interface **IDebugProgram2** transmise à la méthode **Attach.**

3. Envoyer un objet **d’événement IDebugProgramCreateEvent2** pour aviser le SDM que l’objet **local IDebugProgram2** a été créé pour représenter le programme à l’DE.

4. Envoyer un objet d’événement [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) pour informer le SDM qu’un nouveau thread est créé pour le processus qui a été lancé.

## <a name="see-also"></a>Voir aussi
- [Envoyer les événements requis](../../extensibility/debugger/sending-the-required-events.md)
- [Permettre la déboiffée d’un programme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

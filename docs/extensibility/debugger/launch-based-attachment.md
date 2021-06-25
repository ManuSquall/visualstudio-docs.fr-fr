---
title: Pièce jointe basée sur le lancement | Microsoft Docs
description: En savoir plus sur la pièce jointe basée sur le lancement d’un programme, qui est automatique et suit un chemin comme celui de la pièce jointe manuelle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97bbc098e766a1025c372ff35c5849bfe652649f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904332"
---
# <a name="launch-based-attachment"></a>Pièce jointe basée sur le lancement
La pièce jointe basée sur le lancement d’un programme est automatique. Lorsque le processus hébergeant le programme est lancé par le SDM, la pièce jointe basée sur le lancement suit un chemin d’accès similaire à celui de la méthode manuelle des pièces jointes. Pour plus d’informations, consultez [attacher au programme](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Processus d’attachement
 La principale différence est la séquence d’événements qui suivent l’appel d' **attachement** , comme suit :

1. Envoie un objet d’événement **IDebugEngineCreateEvent2** au SDM. Pour plus d’informations, consultez [Envoyer des événements](../../extensibility/debugger/sending-events.md).

2. Appelez la `IDebugProgram2::GetProgramId` méthode sur l’interface **IDebugProgram2** transmise à la méthode **Attach** .

3. Envoie un objet d’événement **IDebugProgramCreateEvent2** pour notifier au SDM que l’objet **IDebugProgram2** local a été créé pour représenter le programme au de.

4. Envoie un objet d’événement [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) pour notifier au SDM qu’un nouveau thread est créé pour le processus qui a été lancé.

## <a name="see-also"></a>Voir aussi
- [Envoyer les événements requis](../../extensibility/debugger/sending-the-required-events.md)
- [Activer un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

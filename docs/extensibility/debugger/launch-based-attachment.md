---
title: Pièce jointe basée sur le lancement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0cf41afa91ce1e77904b99f17ea0321e9bdb12d1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091718"
---
# <a name="launch-based-attachment"></a>Pièce jointe basée sur le lancement
En fonction du lancement de pièce jointe à un programme est automatique. Lorsque le processus qui héberge le programme est lancé par le SDM, basée sur le lancement de pièce jointe suit un chemin d’accès semblable à celle de la méthode manuelle de pièce jointe. Pour plus d’informations, consultez [joindre au programme](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Le processus d’attachement
 La principale différence est la séquence d’événements suivant le **attacher** appeler, comme suit :

1. Envoyer un **IDebugEngineCreateEvent2** objet d’événement pour le SDM. Pour plus d’informations, consultez [envoyer des événements](../../extensibility/debugger/sending-events.md).

2. Appelez le `IDebugProgram2::GetProgramId` méthode sur le **IDebugProgram2** interface passé à la **attacher** (méthode).

3. Envoyer un **IDebugProgramCreateEvent2** objet d’événement pour avertir le SDM qui local **IDebugProgram2** objet a été créé pour représenter le programme pour l’Allemagne.

4. Envoyer un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) objet d’événement pour avertir le SDM qu’un nouveau thread est créé pour le processus lancé.

## <a name="see-also"></a>Voir aussi
- [Envoyer les événements requis](../../extensibility/debugger/sending-the-required-events.md)
- [Activer un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
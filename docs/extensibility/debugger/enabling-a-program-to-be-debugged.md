---
title: Permettre la débrille d’un programme . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17c6218cd0b25c0cf0134351fd5efd7490b6a1f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738893"
---
# <a name="enable-a-program-to-be-debugged"></a>Permettre la déboiffée d’un programme
Avant que votre moteur de débogé (DE) puisse déboiffer un programme, vous devez d’abord lancer le DE ou l’attacher à un programme existant.

## <a name="in-this-section"></a>Contenu de cette section
 [Obtenir un port](../../extensibility/debugger/getting-a-port.md) Discute de la façon d’obtenir un port comme première étape pour permettre la débâmation d’un programme.

 [Enregistrer le programme](../../extensibility/debugger/registering-the-program.md) Explique la prochaine étape pour permettre la déboissailler d’un programme : l’enregistrer au port. Une fois inscrit, le programme peut être déboglé soit par le processus d’attachement ou de débogage juste à temps (JIT).

 [Joindre au programme](../../extensibility/debugger/attaching-to-the-program.md) Explique l’étape suivante : attacher le débbuggeur au programme.

 [Fixation basée sur le lancement](../../extensibility/debugger/launch-based-attachment.md) Décrit la pièce jointe basée sur le lancement à un programme, qui est automatique lors du lancement par le SDM.

 [Envoyer les événements requis](../../extensibility/debugger/sending-the-required-events.md) Vous étapes à travers les événements requis lors de la création d’un moteur de débogé (DE) et de l’attacher à un programme.

## <a name="related-sections"></a>Sections connexes
 [Création d’un moteur de débogé personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md) Définit un moteur de débogé (DE), et décrit les services mis en œuvre à travers les interfaces DE et comment ils peuvent provoquer la transition du débbuggeur entre les différents modes opérationnels.

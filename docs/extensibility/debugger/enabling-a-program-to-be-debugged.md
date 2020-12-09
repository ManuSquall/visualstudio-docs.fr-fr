---
title: Activation d’un programme à déboguer | Microsoft Docs
description: Découvrez comment lancer votre moteur de débogage ou attacher le moteur de débogage à un programme existant pour déboguer un programme.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ac9a43a0ec539dd978710c23c9b44f27eac81799
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915256"
---
# <a name="enable-a-program-to-be-debugged"></a>Activer un programme à déboguer
Avant de pouvoir déboguer un programme par votre moteur DE débogage (DE), vous devez d’abord lancer le ou l’attacher à un programme existant.

## <a name="in-this-section"></a>Dans cette section
 [Obtenir un port](../../extensibility/debugger/getting-a-port.md) Explique comment obtenir un port comme première étape pour permettre le débogage d’un programme.

 [Inscrire le programme](../../extensibility/debugger/registering-the-program.md) Explique l’étape suivante de l’activation d’un programme à déboguer : l’inscrire auprès du port. Une fois inscrit, le programme peut être débogué à l’aide du processus d’attachement ou du débogage juste-à-temps (JIT).

 [Attacher au programme](../../extensibility/debugger/attaching-to-the-program.md) Explique l’étape suivante : attachement du débogueur au programme.

 [Attachement basé sur le lancement](../../extensibility/debugger/launch-based-attachment.md) Décrit la pièce jointe basée sur le lancement d’un programme, qui est automatique lors du lancement par le SDM.

 [Envoyer les événements requis](../../extensibility/debugger/sending-the-required-events.md) Vous guide tout au long des événements requis lors de la création d’un moteur de débogage (DE) et de son attachement à un programme.

## <a name="related-sections"></a>Sections connexes
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md) Définit un moteur DE débogage (DE) et décrit les services implémentés via les interfaces DE et la façon dont ils peuvent provoquer la transition du débogueur entre différents modes d’exploitation.

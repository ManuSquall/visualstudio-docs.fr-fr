---
title: Activation d’un programme à déboguer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f301de66421ef1327b86d900305cb4ecbfb5623
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889692"
---
# <a name="enable-a-program-to-be-debugged"></a>Activer un programme à déboguer
Avant votre moteur de débogage (dé) pouvez déboguer un programme, vous devez tout d’abord lancer le DE ou attacher à un programme existant.

## <a name="in-this-section"></a>Dans cette section
 [Obtenir un port](../../extensibility/debugger/getting-a-port.md) explique comment obtenir un port en tant que la première étape de permettre à un programme à déboguer.

 [Enregistrer le programme](../../extensibility/debugger/registering-the-program.md) explique l’étape suivante de l’activation d’un programme à déboguer : l’inscription avec le port. Une fois inscrit, le programme peut être débogué soit par le processus d’attachement ou le débogage juste-à-temps (JIT).

 [Attacher le programme](../../extensibility/debugger/attaching-to-the-program.md) explique l’étape suivante : attacher le débogueur au programme.

 [En fonction du lancement attachement](../../extensibility/debugger/launch-based-attachment.md) décrit basée sur le lancement de pièce jointe à un programme, ce qui est automatique lors de son lancement en le SDM.

 [Envoyer les événements requis](../../extensibility/debugger/sending-the-required-events.md) vous guide à travers les événements requis lors de la création d’un moteur de débogage (DE) et en l’attachant à un programme.

## <a name="related-sections"></a>Rubriques connexes
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md) définit un moteur de débogage (DE) et décrit les services implémentés via les interfaces DE et comment ils peuvent provoquer le débogueur à la transition entre les différents modes de fonctionnement.
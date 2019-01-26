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
ms.openlocfilehash: f8faa677e5893c0737bcd89db5567ef7459f6d07
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953224"
---
# <a name="enable-a-program-to-be-debugged"></a>Activer un programme à déboguer
Avant votre moteur de débogage (dé) pouvez déboguer un programme, vous devez tout d’abord lancer le DE ou attacher à un programme existant.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Obtenir un port](../../extensibility/debugger/getting-a-port.md)  
 Explique comment obtenir un port en tant que la première étape de permettre à un programme à déboguer.  
  
 [Enregistrer le programme](../../extensibility/debugger/registering-the-program.md)  
 Explique l’étape suivante de l’activation d’un programme à déboguer : l’inscription avec le port. Une fois inscrit, le programme peut être débogué soit par le processus d’attachement ou le débogage juste-à-temps (JIT).  
  
 [Attacher le programme](../../extensibility/debugger/attaching-to-the-program.md)  
 Explique l’étape suivante : attacher le débogueur au programme.  
  
 [En fonction du lancement d’attachement](../../extensibility/debugger/launch-based-attachment.md)  
 Décrit en fonction du lancement de pièce jointe à un programme, ce qui est automatique lors de son lancement en le SDM.  
  
 [Envoyer les événements requis](../../extensibility/debugger/sending-the-required-events.md)  
 Vous guide à travers les événements requis lors de la création d’un moteur de débogage (DE) et en l’attachant à un programme.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Définit un moteur de débogage (DE) et décrit les services implémentés via les interfaces DE et comment ils peuvent provoquer le débogueur à la transition entre les différents modes de fonctionnement.
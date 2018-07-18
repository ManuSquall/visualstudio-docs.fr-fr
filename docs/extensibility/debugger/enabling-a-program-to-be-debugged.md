---
title: L’activation d’un programme à déboguer | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f8dc37e5d59738e6ef326be71e773c1e4e57351
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100528"
---
# <a name="enabling-a-program-to-be-debugged"></a>L’activation d’un programme à déboguer
Avant votre moteur de débogage (DE) peut déboguer un programme, vous devez tout d’abord lancer la DE ou attacher à un programme existant.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Obtention d’un port](../../extensibility/debugger/getting-a-port.md)  
 Explique comment obtenir un port de la première étape consiste à activer un programme à déboguer.  
  
 [Inscription du programme](../../extensibility/debugger/registering-the-program.md)  
 Explique l’étape suivante de l’activation d’un programme à déboguer : inscrivant avec le port. Une fois inscrit, le programme peut être débogué soit par le processus d’attachement ou le débogage juste-à-temps (JIT).  
  
 [Lisaison au programme](../../extensibility/debugger/attaching-to-the-program.md)  
 Explique l’étape suivante : attacher le débogueur au programme.  
  
 [Basé sur le lancement d’attachement](../../extensibility/debugger/launch-based-attachment.md)  
 Décrit en fonction de lancement de pièce jointe à un programme, ce qui est automatique lors du lancement par le SDM.  
  
 [Envoi des événements requis](../../extensibility/debugger/sending-the-required-events.md)  
 Vous guide à travers les événements requis lors de la création d’un moteur de débogage (DE) et en l’attachant à un programme.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Définit un moteur de débogage (DE) et décrit les services implémentés via les interfaces DE et comment ils peuvent provoquer le débogueur pour effectuer la transition entre les différents modes de fonctionnement.
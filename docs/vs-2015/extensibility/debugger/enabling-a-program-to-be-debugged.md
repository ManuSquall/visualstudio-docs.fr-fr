---
title: Activation d’un programme à déboguer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0f0331430a1cc625dee2a7029742fd62d67fb56
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952722"
---
# <a name="enabling-a-program-to-be-debugged"></a>Activation d’un programme à déboguer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avant votre moteur de débogage (dé) pouvez déboguer un programme, vous devez tout d’abord lancer le DE ou attacher à un programme existant.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Obtention d’un port](../../extensibility/debugger/getting-a-port.md)  
 Explique comment obtenir un port en tant que la première étape de permettre à un programme à déboguer.  
  
 [Inscription du programme](../../extensibility/debugger/registering-the-program.md)  
 Explique l’étape suivante de l’activation d’un programme à déboguer : l’inscription avec le port. Une fois inscrit, le programme peut être débogué soit par le processus d’attachement ou le débogage juste-à-temps (JIT).  
  
 [Lisaison au programme](../../extensibility/debugger/attaching-to-the-program.md)  
 Explique l’étape suivante : attacher le débogueur au programme.  
  
 [En fonction du lancement d’attachement](../../extensibility/debugger/launch-based-attachment.md)  
 Décrit en fonction du lancement de pièce jointe à un programme, ce qui est automatique lors de son lancement en le SDM.  
  
 [Envoi des événements requis](../../extensibility/debugger/sending-the-required-events.md)  
 Vous guide à travers les événements requis lors de la création d’un moteur de débogage (DE) et en l’attachant à un programme.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Définit un moteur de débogage (DE) et décrit les services implémentés via les interfaces DE et comment ils peuvent provoquer le débogueur à la transition entre les différents modes de fonctionnement.

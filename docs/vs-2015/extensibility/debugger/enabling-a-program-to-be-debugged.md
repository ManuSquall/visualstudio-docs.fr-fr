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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155376"
---
# <a name="enabling-a-program-to-be-debugged"></a>Activation d’un programme à déboguer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avant de pouvoir déboguer un programme par votre moteur DE débogage (DE), vous devez d’abord lancer le ou l’attacher à un programme existant.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Obtention d’un port](../../extensibility/debugger/getting-a-port.md)  
 Explique comment obtenir un port comme première étape pour permettre le débogage d’un programme.  
  
 [Inscription du programme](../../extensibility/debugger/registering-the-program.md)  
 Explique l’étape suivante de l’activation d’un programme à déboguer : l’inscrire auprès du port. Une fois inscrit, le programme peut être débogué à l’aide du processus d’attachement ou du débogage juste-à-temps (JIT).  
  
 [Lisaison au programme](../../extensibility/debugger/attaching-to-the-program.md)  
 Explique l’étape suivante : attachement du débogueur au programme.  
  
 [Attachement basé sur le lancement](../../extensibility/debugger/launch-based-attachment.md)  
 Décrit la pièce jointe basée sur le lancement d’un programme, qui est automatique lors du lancement par le SDM.  
  
 [Envoi des événements requis](../../extensibility/debugger/sending-the-required-events.md)  
 Vous guide tout au long des événements requis lors de la création d’un moteur de débogage (DE) et de son attachement à un programme.  
  
## <a name="related-sections"></a>Sections connexes  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Définit un moteur DE débogage (DE) et décrit les services implémentés via les interfaces DE et la façon dont ils peuvent provoquer la transition du débogueur entre différents modes d’exploitation.

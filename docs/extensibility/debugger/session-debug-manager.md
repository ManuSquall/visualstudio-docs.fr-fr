---
title: "Gestionnaire de session de d&#233;bogage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Gestionnaire de débogage de session, unification des vues de la session"
  - "Gestionnaire de débogage de session, la diffusion"
  - "Gestionnaire de session de débogage [Debugging SDK], le débogage"
  - "Gestionnaire de session de débogage"
  - "Gestionnaire de session de débogage, débogage de multiplexage de moteur"
  - "Gestionnaire de débogage de session, délégation"
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Gestionnaire de session de d&#233;bogage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le gestionnaire de débogage de session \(SDM\) gère un certain nombre de moteurs \(DE\) de débogage déboguez plusieurs programmes dans plusieurs processus sur un certain nombre d'ordinateurs.  En plus de être un multiplexeur du moteur de débogage, le SDM fournit un affichage unifié de la session de débogage à l'IDE.  
  
## opération de gestionnaire de débogage de session  
 le gestionnaire de débogage de session \(SDM\) gère le De.  Il peut exister plusieurs exécution du moteur de débogage sur un ordinateur en même temps.  Pour multiplexer DES, elle se poursuit de SDM un nombre quelconque d'interfaces du les et les expose à l'IDE comme une interface unique.  
  
 Pour améliorer les performances, certaines interfaces ne sont pas multiplexées.  En revanche, ils sont utilisés directement à partir De, et les appels à ces interfaces ne traversent pas le SDM.  Par exemple, les interfaces utilisées avec la mémoire, le code, et les contextes de document ne sont pas multiplexées, car elles font référence à une instruction, à une mémoire, ou à un document spécifique dans un programme spécifique débogué par un ensemble De.  Aucun autre De ne doit être impliqué dans ce niveau de communication.  
  
 Ce n'est pas le cas de tous les contextes.  les appels à l'interface de contexte d'évaluation de l'expression passent par le SDM.  Pendant l'évaluation d'une expression, le SDM enveloppe l'interface d' [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) qu'elle donne à l'IDE car lorsque cette expression est évaluée, il peut impliquer le DES multiples qui débogage des programmes dans le même processus qui peut exécuter sur le même thread.  
  
 Le SDM agit généralement comme un mécanisme de délégation, mais il peut agir comme un mécanisme de diffusion.  Par exemple, pendant l'évaluation d'une expression, le SDM agit comme un mécanisme de diffusion pour notifier tout le DES qu'ils peuvent exécuter du code sur un thread spécifié.  De même, lorsque le SDM reçoit un événement arrêtant, il est diffusé à tous les programmes qu'ils doivent arrêter l'exécution.  Lorsqu'une étape est appelée, le SDM le est diffusé à tous les programmes qu'ils peuvent continuer à s'exécuter.  Les points d'arrêt sont également diffusés à chaque De.  
  
 Le SDM ne suit pas le programme en cours, le thread, ou le frame de pile.  Le processus, le programme, et les informations de threads est envoyé au SDM conjointement avec les événements spécifiques de débogage.  
  
## Voir aussi  
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)   
 [Contextes de débogueur](../../extensibility/debugger/debugger-contexts.md)
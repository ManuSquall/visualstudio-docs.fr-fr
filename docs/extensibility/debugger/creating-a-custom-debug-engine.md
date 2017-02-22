---
title: "Cr&#233;ation d&#39;un moteur de d&#233;bogage personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "l'implémentation des moteurs de débogage"
  - "moteurs de débogage personnalisés"
  - "débogage [Debugging SDK], les moteurs de débogage personnalisés"
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Cr&#233;ation d&#39;un moteur de d&#233;bogage personnalis&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un moteur \(DE\) de débogage est un composant qui autorise le débogage des architectures à l'exécution particulières.  Il y a généralement un seul L'implementation par environnement d'exécution.  
  
> [!NOTE]
>  S'il y a DE implementations distinct pour Transact\-SQL et JScript, VBScript et JScript partagent un De unique.  
  
 Un De fonctions par l'interpréteur ou le système d'exploitation pour fournir des services de débogage tels que le contrôle, les points d'arrêt, et l'évaluation de l'expression d'exécution.  Ces services sont implémentés par le biais DE interfaces et peuvent provoquer le débogueur à la transition entre les différents modes opérationnels.  Pour plus d'informations, consultez [Modes de fonctionnement](../../extensibility/debugger/operational-modes.md).  
  
 Créer un De inclut les étapes suivantes :  
  
1.  enregistrer un De avec Visual Studio  
  
2.  Activation d'un programme à déboguer  
  
3.  exécution de contrôle et évaluation d'état  
  
4.  événements d'émission  
  
5.  arrêt et détacher  
  
## Dans cette section  
 [L’inscription d’un moteur de débogage personnalisé](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Explique les étapes nécessaires pour stocker un moteur de débogage avec Visual Studio afin qu'il puisse être utilisé.  
  
 [L'activation d'un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Explique qu'avant que votre De puisse déboguer un programme, vous devez d'abord exécuter le De ou l'attacher à un programme existant.  
  
 [Contrôle de l'exécution et l'évaluation de l'état](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Explique pourquoi le débogage d'une application requiert implémenter des fonctionnalités de contrôle d'exécution.  
  
 [L'envoi d'événements](../../extensibility/debugger/sending-events.md)  
 Décrit la communication entre le débogueur et le du en tant que modèle d'événement en fonction de DCOM.  
  
 [Arrêt et détachement](../../extensibility/debugger/termination-and-detaching.md)  
 Explique comment effectuer l'arrêt normal, ce qui signifie qu'il n'y a pas de point d'arrêt, exception, erreur d'exécution, ou boucle infinie dans l'application à déboguer.  
  
 [Appeler les événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)  
 Documente l'ordre d'appel des événements qui se produisent dans une session de débogage.  
  
 [Comment : Déboguer un moteur de débogage personnalisé](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Explique comment déboguer un personnalisé pour.  
  
## Voir aussi  
 [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
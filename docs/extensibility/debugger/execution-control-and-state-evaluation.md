---
title: "Contr&#244;le de l’ex&#233;cution et l’&#233;valuation de l’&#233;tat | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage [Debugging SDK], le contrôle d’exécution"
  - "évaluation d’expression, contrôle d’exécution"
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Contr&#244;le de l’ex&#233;cution et l’&#233;valuation de l’&#233;tat
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Débogage d’une application requiert en implémentant des fonctionnalités de contrôle de l’exécution pas à pas détaillé dans les fonctions, l’arrêt des points d’arrêt et poursuivre l’exécution. Bases de débogage Visual Studio son contrôle de l’exécution sur les événements envoyés entre les composants du débogueur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Contrôle du programme](../../extensibility/debugger/program-control.md)  
 Répertorie les routines suivantes se produisent au niveau du programme : définir l’instruction suivante, l’exécution, exécution pas à pas, continuer, la suspension et reprise.  
  
 [Méthodes de point d’arrêt](../../extensibility/debugger/breakpoint-related-methods.md)  
 Définit la limite et en attente de types de points d’arrêt qui prend en charge de Visual Studio.  
  
 [Version d’évaluation de la pile des appels](../../extensibility/debugger/call-stack-evaluation.md)  
 Décrit l’implémentation des méthodes qui permettent d’afficher les frames de pile de la pile des appels en mode arrêt.  
  
 [Évaluation d’expression](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Explique comment le moteur de débogage (DE), Gestionnaire d’expression d’évaluation (EE) et à la session de débogage sont impliqués dans l’analyse et l’évaluation d’une expression entrée dans un des fenêtres de l’IDE.  
  
 [Événements de contrôle](../../extensibility/debugger/control-events.md)  
 Décrit l’interface utilisée pour envoyer des événements pendant l’exécution du programme contrôlée.
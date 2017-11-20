---
title: "Contrôle de l’exécution et l’état d’évaluation | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f2f76f97111f24a7b6b4ea1a7a22004d6867fcd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="execution-control-and-state-evaluation"></a>Contrôle de l’exécution et l’état d’évaluation
Débogage d’une application requiert en implémentant des fonctionnalités de contrôle de l’exécution pas à pas détaillé dans des fonctions, stopper aux points d’arrêt et continuer l’exécution. Bases de débogage Visual Studio son contrôle de l’exécution sur les événements envoyés entre les composants du débogueur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Contrôle du programme](../../extensibility/debugger/program-control.md)  
 Répertorie les routines suivantes qui se produisent au niveau du programme : définir l’instruction suivante, l’exécution, exécution pas à pas, continuer, la suspension et la reprise.  
  
 [Méthodes liées au point d’arrêt](../../extensibility/debugger/breakpoint-related-methods.md)  
 Définit la limite, en attente de types de points d’arrêt qui prend en charge de Visual Studio.  
  
 [Évaluation de la pile des appels](../../extensibility/debugger/call-stack-evaluation.md)  
 Aborde l’implémentation des méthodes qui permettent d’afficher les frames de pile de la pile des appels en mode arrêt.  
  
 [Évaluation des expressions](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Explique comment le moteur de débogage (DE), Gestionnaire d’expression d’évaluation (EE) et la session de débogage sont impliqués dans l’analyse et évaluation d’une expression entrée dans un des fenêtres de l’IDE.  
  
 [Événements de contrôle](../../extensibility/debugger/control-events.md)  
 Décrit l’interface utilisée pour envoyer des événements pendant l’exécution contrôlée du programme.
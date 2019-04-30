---
title: Contrôle d’exécution et évaluation de l’état | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd04cfa1e271f94f1b37aa0fbd62e9b846d9a70d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925710"
---
# <a name="execution-control-and-state-evaluation"></a>Évaluation de contrôle et l’état d’exécution
Débogage d’une application nécessite en implémentant des fonctionnalités de contrôle de l’exécution en tant que détaillé des fonctions, l’arrêt aux points d’arrêt et continuer l’exécution. Bases de débogage Visual Studio son contrôle de l’exécution sur les événements envoyés entre les composants du débogueur.

## <a name="in-this-section"></a>Dans cette section
 [Contrôle du programme](../../extensibility/debugger/program-control.md) répertorie les routines suivantes qui se produisent au niveau du programme : définir l’instruction suivante, l’exécution, exécution pas à pas, continuer, la suspension et la reprise.

 [Méthodes de point d’arrêt](../../extensibility/debugger/breakpoint-related-methods.md) définit la limite et en attente de types de points d’arrêt qui prend en charge de Visual Studio.

 [Appeler l’évaluation de la pile](../../extensibility/debugger/call-stack-evaluation.md) aborde l’implémentation des méthodes qui permettent d’afficher les frames de pile de la pile des appels en mode arrêt.

 [Évaluation de l’expression](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) explique comment le moteur de débogage (DE), évaluation de l’expression (EE) et Gestionnaire de session de débogage sont impliqués dans l’analyse et l’évaluation d’une expression d’entrée dans un des fenêtres de l’IDE.

 [Événements de contrôle](../../extensibility/debugger/control-events.md) décrit l’interface utilisée pour envoyer des événements pendant l’exécution contrôlée du programme.
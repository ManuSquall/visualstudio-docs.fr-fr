---
title: Contrôle d’exécution et évaluation de l’état | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bda531e94bdea07ee37eed2b0b79e6f0667ba28e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315236"
---
# <a name="execution-control-and-state-evaluation"></a>Évaluation de contrôle et l’état d’exécution
Débogage d’une application nécessite en implémentant des fonctionnalités de contrôle de l’exécution en tant que détaillé des fonctions, l’arrêt aux points d’arrêt et continuer l’exécution. Bases de débogage Visual Studio son contrôle de l’exécution sur les événements envoyés entre les composants du débogueur.

## <a name="in-this-section"></a>Dans cette section
 [Contrôle du programme](../../extensibility/debugger/program-control.md) répertorie les routines suivantes qui se produisent au niveau du programme : définir l’instruction suivante, l’exécution, exécution pas à pas, continuer, la suspension et la reprise.

 [Méthodes de point d’arrêt](../../extensibility/debugger/breakpoint-related-methods.md) définit la limite et en attente de types de points d’arrêt qui prend en charge de Visual Studio.

 [Appeler l’évaluation de la pile](../../extensibility/debugger/call-stack-evaluation.md) aborde l’implémentation des méthodes qui permettent d’afficher les frames de pile de la pile des appels en mode arrêt.

 [Évaluation de l’expression](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) explique comment le moteur de débogage (DE), évaluation de l’expression (EE) et Gestionnaire de session de débogage sont impliqués dans l’analyse et l’évaluation d’une expression d’entrée dans un des fenêtres de l’IDE.

 [Événements de contrôle](../../extensibility/debugger/control-events.md) décrit l’interface utilisée pour envoyer des événements pendant l’exécution contrôlée du programme.
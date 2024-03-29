---
title: Contrôle d’exécution et évaluation d’État | Microsoft Docs
description: Découvrez comment le débogage de Visual Studio base son contrôle d’exécution sur les événements envoyés entre les composants du débogueur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 598332ec1e9e1cb270360822ca32792b9a53f5c1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096952"
---
# <a name="execution-control-and-state-evaluation"></a>Contrôle d’exécution et évaluation de l’État
Le débogage d’une application nécessite l’implémentation de fonctionnalités de contrôle d’exécution telles que l’exécution pas à pas des fonctions, l’arrêt des points d’arrêt et la poursuite de l’exécution. Le débogage de Visual Studio base son contrôle d’exécution sur les événements envoyés entre les composants du débogueur.

## <a name="in-this-section"></a>Dans cette section
 [Contrôle du programme](../../extensibility/debugger/program-control.md) Répertorie les routines suivantes qui se produisent au niveau du programme : définition de l’instruction suivante, exécution, exécution pas à pas, poursuite, interruption et reprise.

 [Méthodes liées aux points d’arrêt](../../extensibility/debugger/breakpoint-related-methods.md) Définit les types de points d’arrêt liés et en attente que Visual Studio prend en charge.

 [Évaluation](../../extensibility/debugger/call-stack-evaluation.md) de la pile des appels Traite de l’implémentation des méthodes qui permettent d’afficher les frames de pile de la pile des appels en mode arrêt.

 [Évaluation d’expression](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Explique comment le moteur de débogage (DE), l’évaluation d’expression (EE) et le gestionnaire de débogage de session sont impliqués dans l’analyse et l’évaluation d’une expression entrée dans l’une des fenêtres de l’IDE.

 [Événements de contrôle](../../extensibility/debugger/control-events.md) Présente l’interface utilisée pour envoyer des événements pendant l’exécution contrôlée du programme.

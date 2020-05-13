---
title: Contrôle des exécutions et évaluation de l’État (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc76ae97e8baa6ce78dd4d565109d6a19e2051e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738757"
---
# <a name="execution-control-and-state-evaluation"></a>Contrôle des exécutions et évaluation de l’État
Le débogage d’une application nécessite la mise en œuvre de fonctionnalités de contrôle d’exécution telles que l’entrée dans les fonctions, l’arrêt aux points d’arrêt et la poursuite de l’exécution. Visual Studio débogage base son contrôle d’exécution sur les événements envoyés entre les composants de débogage.

## <a name="in-this-section"></a>Contenu de cette section
 [Contrôle du programme](../../extensibility/debugger/program-control.md) Répertorie les routines suivantes qui se produisent au niveau du programme : établissement de la déclaration suivante, exécution, marche, poursuite, suspension et reprise.

 [Méthodes liées au point de rupture](../../extensibility/debugger/breakpoint-related-methods.md) Définit les types de points de rupture liés et en attente que Visual Studio prend en charge.

 [Évaluation de la pile d’appels](../../extensibility/debugger/call-stack-evaluation.md) Discute de la mise en œuvre des méthodes qui permettent de visualiser les cadres de la pile de la pile d’appel pendant le mode de rupture.

 [Évaluation de l’expression](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Explique comment le moteur de débogé (DE), l’évaluation de l’expression (EE) et le gestionnaire de débbug de session sont impliqués dans l’analyse et l’évaluation d’une expression entrée dans l’une des fenêtres de l’IDE.

 [Événements de contrôle](../../extensibility/debugger/control-events.md) Discute de l’interface utilisée pour envoyer des événements lors de l’exécution contrôlée du programme.

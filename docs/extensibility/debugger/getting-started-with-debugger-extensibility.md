---
title: Prise en main avec l’extensibilité du débogueur | Microsoft Docs
description: Commencez à créer et à personnaliser les composants du débogueur utilisés pour déboguer des programmes dans l’environnement Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6949b9b8a9168915c64bc6183f6b1391a1c79220
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560033"
---
# <a name="get-started-with-debugger-extensibility"></a>Prise en main de l’extensibilité du débogueur
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Fournit les informations dont vous avez besoin pour créer et personnaliser les composants du débogueur utilisés pour déboguer des programmes à partir de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le débogage a ajouté des améliorations dérivées des tests d’utilisabilité étendus effectués sur les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogueurs précédents. Vous pouvez utiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le débogage pour effectuer un pas à pas détaillé dans une application multilingue, ou vous pouvez implémenter une modification à la volée des variables pendant le débogage d’applications et de solutions multilingues.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le débogage est exécuté hors processus avec le programme en cours de débogage et est donc moins intrusif dans l’espace de processus de l’application. Par conséquent, il est plus facile d’écrire des composants qui interagissent avec le débogueur sans affecter votre programme de débogage.

 Pour utiliser au mieux le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , vous devez être familiarisé avec les éléments suivants :

- L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE)

- Langage de programmation C++

- COM ATL

## <a name="in-this-section"></a>Dans cette section
 Feuille [de route pour l’extension du débogueur](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Décrit le processus d’implémentation du débogage dans votre produit, en fonction de votre compilateur et de sa sortie.

 [Composants du débogueur](../../extensibility/debugger/debugger-components.md) Fournit une vue d’ensemble des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] composants de débogage, notamment le moteur de débogage (de), l’évaluateur d’expression (EE) et le gestionnaire de symboles (SH).

 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md) Décrit les principaux concepts architecturaux du débogage.

 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md) Explique comment le moteur DE débogage fonctionne simultanément dans le code, la documentation et les contextes d’évaluation des expressions. Décrit, pour chacun des trois contextes, l’emplacement, la position ou l’évaluation qui s’y rapporte.

 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md) Contient des liens vers différentes tâches de débogage, telles que le lancement d’un programme et l’évaluation d’expressions.

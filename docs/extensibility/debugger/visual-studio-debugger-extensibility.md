---
title: Extensibilité du débogueur Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df9d1bccb2147d8416555099f3493ceac8c21b4b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912905"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilité du débogueur Visual Studio
Visual Studio inclut un débogueur de code source totalement interactives, en fournissant un outil puissant et facile à utiliser pour le suivi des bogues dans votre programme. Le débogueur a prise en charge complète Visual Basic, c#, C/C++ et JavaScript. Toutefois, avec la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], qui est disponible à partir de la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), autres langages de programmation peuvent être pris en charge dans le débogueur avec les mêmes fonctionnalités riches.

 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogueur est le serveur frontal courantes (autrement dit, l’interface utilisateur) pour les composants de débogage qui sont, quant à lui, spécifiques au langage en cours de débogage. De nouveaux langages, tout ce qui est nécessaire pour prendre en charge par le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogueur consiste à créer les composants principaux nécessaires, comme un moteur de débogage (dé). Ce point est là le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] arrive.

 Le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] inclut une référence complète à tous les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] éléments requis pour créer un nouveau DE. En outre, il existe des exemples et didacticiels qui vous aideront à vous aider à démarrer.

 Pour obtenir un exemple complet d’un système de projet de langage avec prise en charge le débogage, consultez le [exemple IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 Les sections suivantes décrivent comment étendre le débogueur à l’aide de la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>Dans cette section
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) décrit ce que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] offres et comment installer le Kit de développement logiciel de débogage.

 [Créer un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md) documente le traitement DE personnalisé, de la préparation de votre programme à un DE détachement de l’Allemagne.

 [Écrire un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) explique si vous devez écrire un évaluateur d’expression.

 [Choisir une stratégie de mise en œuvre de moteur de débogage](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) explique comment implémenter votre DE.

 [Référence](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Documents le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API de débogage.

 [Exemples](../../extensibility/debugger/visual-studio-debugging-samples.md) contient des liens vers un exemple évaluateur expression de common language runtime et un exemple de moteur de débogage.

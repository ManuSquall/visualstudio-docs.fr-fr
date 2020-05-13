---
title: Visual Studio Debugger Extensibility (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff4222b555fab73914776725fc79581f29fa5e53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712501"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio débbugger extensibility
Visual Studio comprend un débbugger de code source entièrement interactif, fournissant un outil puissant et facile à utiliser pour traquer les bogues de votre programme. Le débbuggeur bénéficie d’un support complet pour Visual Basic, C, C/C et JavaScript. Cependant, avec [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]le , qui est disponible à partir du [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=21835), d’autres langages de programmation peuvent être pris en charge dans le débbugger avec les mêmes fonctionnalités riches.

 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage est l’extrémité avant commune (c’est-à-dire l’interface utilisateur) aux composants de débogage qui sont, à leur tour, spécifiques à la langue étant débogé. Pour les nouvelles langues, tout ce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qui est nécessaire pour le soutien par le débbuggeur est de créer les composants back-end nécessaires, tels qu’un moteur de débogé (DE). C’est là [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] que l’on entre en vigueur.

 Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] comprend une référence [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] complète à tous les éléments nécessaires à la création d’un nouveau DE. En outre, il ya des échantillons et des tutoriels qui vous aideront à démarrer.

 Pour un échantillon complet d’un système de projet linguistique avec soutien de débogage, voir [l’échantillon IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 Les sections suivantes décrivent comment étendre le débbuggeur en utilisant le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>Contenu de cette section
 [Démarrer](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Décrit ce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que Debugging offre et comment installer le SDK.

 [Créer un moteur de débogé personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md) Documente le processus DE personnalisé, de la préparation de votre programme pour un DE au détachement de la DE.

 [Écrire un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Explique si vous devez écrire un évaluateur d’expression.

 [Choisissez une stratégie de mise en œuvre d’un moteur de débogé](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Discute de la façon de mettre en œuvre votre DE.

 [Référence](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Documente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’API Debugging.

 [Échantillons](../../extensibility/debugger/visual-studio-debugging-samples.md) Contient des liens vers un échantillon commun d’évaluateur d’expression de temps de course de langue et un échantillon de moteur de débagé.

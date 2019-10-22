---
title: Extensibilité du débogueur Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f8a1c2148f25a1e97cfd1369770e056d1cb907d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568971"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilité du débogueur Visual Studio
Visual Studio comprend un débogueur de code source entièrement interactif, fournissant un outil puissant et facile à utiliser pour le suivi des bogues dans votre programme. Le débogueur est entièrement pris en charge pour C#Visual Basic,,C++C/et JavaScript. Toutefois, avec le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], qui est disponible à partir du [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkId=214453), d’autres langages de programmation peuvent être pris en charge dans le débogueur avec les mêmes fonctionnalités enrichies.

 Le débogueur [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est le serveur frontal commun (autrement dit, l’interface utilisateur) aux composants de débogage qui, à leur tour, sont spécifiques au langage en cours de débogage. Pour les nouveaux langages, tout ce qui est nécessaire pour la prise en charge par le débogueur [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consiste à créer les composants principaux nécessaires, tels qu’un moteur DE débogage (DE). C’est là qu’intervient le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

 Le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] comprend une référence complète à tous les éléments de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] requis pour créer un nouveau. En outre, il existe des exemples et des didacticiels qui vous aideront à démarrer.

 Pour obtenir un exemple complet d’un système de projet de langage avec prise en charge du débogage, consultez l' [exemple IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 Les sections suivantes décrivent comment étendre le débogueur à l’aide de l' [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>Dans cette section
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Décrit ce que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le débogage offre et comment installer le kit de développement logiciel (SDK).

 [Créer un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md) Documente le processus DE détachement personnalisé, de la préparation de votre programme à un DE pour le détachement DE.

 [Écrire un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Explique si vous devez écrire un évaluateur d’expression.

 [Choisir une stratégie d’implémentation du moteur de débogage](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Explique comment implémenter votre DE.

 [Référence](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Documente l’API de débogage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 [Exemples](../../extensibility/debugger/visual-studio-debugging-samples.md) Contient des liens vers un exemple d’évaluateur d’expression common language runtime et un exemple de moteur de débogage.

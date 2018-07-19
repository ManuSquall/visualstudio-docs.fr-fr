---
title: Extensibilité du débogueur Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5bb01c093fda068dfbc7dfa705914a8bdef4d2b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127068"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilité du débogueur Visual Studio
Visual Studio inclut un débogueur de code source entièrement interactif, en fournissant un outil puissant et facile à utiliser pour le suivi des bogues dans votre programme. Le débogueur a prise en charge complète de Visual Basic, c#, C/C++ et JavaScript. Toutefois, avec la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], qui est disponible à partir de la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), autres langages de programmation peuvent être pris en charge dans le débogueur avec les mêmes fonctionnalités.  
  
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogueur est le serveur frontal commun (autrement dit, l’interface utilisateur) pour les composants de débogage qui sont, à son tour, spécifiques au langage en cours de débogage. De nouvelles langues, tout ce qui est nécessaire pour prendre en charge par le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogueur consiste à créer les composants principaux nécessaires, par exemple un moteur de débogage (DE). C’est là la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] arrive.  
  
 Le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] inclut une référence complète à tous les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] éléments requis pour créer un nouveau DE. En outre, il existe des exemples et didacticiels qui vous aideront à vous aider à démarrer.  
  
 Pour un exemple de bout en bout pour un langue du système de projet avec prise en charge le débogage, consultez le [exemple IronPython](http://msdn.microsoft.com/en-us/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 Les sections suivantes décrivent comment étendre le débogueur à l’aide de la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Décrit les actions [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] offres et comment installer le Kit de développement logiciel de débogage.  
  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Décrit le processus DE personnalisé, de la préparation de votre programme pour un DE détachement de la DE.  
  
 [L’écriture d’un évaluateur d’Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Explique que si vous devez écrire un évaluateur d’expression.  
  
 [Choix d’une stratégie de mise en œuvre du moteur de débogage](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Explique comment implémenter votre DE.  
  
 [Référence](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documents le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API de débogage.  
  
 [Exemples](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contient des liens vers un exemple évaluateur de common language runtime expression et un exemple de moteur de débogage.

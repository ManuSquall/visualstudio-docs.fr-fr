---
title: Extensibilité du débogueur Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e337e87d162ac59cc6bb45676c1411692dd1a3bb
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675263"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilité du débogueur de Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio inclut un débogueur de code source totalement interactives, en fournissant un outil puissant et facile à utiliser pour le suivi des bogues dans votre programme. Le débogueur a prise en charge complète Visual Basic, c#, C/C++ et JavaScript. Toutefois, avec la [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], qui est disponible à partir de la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453),, autres langages de programmation peuvent être pris en charge dans le débogueur avec les mêmes fonctionnalités riches.  
  
 Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogueur est le serveur frontal courantes (autrement dit, l’interface utilisateur) pour les composants de débogage qui sont, quant à lui, spécifiques au langage en cours de débogage. De nouveaux langages, tout ce qui est nécessaire pour prendre en charge par le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogueur consiste à créer les composants principaux nécessaires, comme un moteur de débogage (dé). C’est là le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] arrive.  
  
 Le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] inclut une référence complète à tous les [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] éléments requis pour créer un nouveau DE. En outre, il existe des exemples et didacticiels qui vous aideront à vous aider à démarrer.  
  
 Pour obtenir un exemple de bout en bout d’un système de projet de langage avec prise en charge le débogage, consultez le [exemple IronPython](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 Les sections suivantes décrivent comment étendre le débogueur à l’aide de la [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Décrit les éléments [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] offres et comment installer le Kit de développement logiciel de débogage.  
  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Décrit le processus DE personnalisé, de la préparation de votre programme à un DE détachement de l’Allemagne.  
  
 [Écriture d’un évaluateur d’expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Explique que si vous devez écrire un évaluateur d’expression.  
  
 [Choix d’une stratégie de mise en œuvre du moteur de débogage](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Explique comment implémenter votre DE.  
  
 [Référence](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documents le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] API de débogage.  
  
 [Exemples](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contient des liens vers un exemple évaluateur expression de common language runtime et un exemple de moteur de débogage.

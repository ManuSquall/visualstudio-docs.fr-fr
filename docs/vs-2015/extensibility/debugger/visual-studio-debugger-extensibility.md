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
ms.openlocfilehash: 0b8d37954bf238b2ed1323bf021fded94ec0c584
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "73983669"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilité du débogueur de Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio comprend un débogueur de code source entièrement interactif, fournissant un outil puissant et facile à utiliser pour le suivi des bogues dans votre programme. Le débogueur a une prise en charge complète Visual Basic, C#, C/C++ et JavaScript. Toutefois, avec le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , qui est disponible à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), d’autres langages de programmation peuvent être pris en charge dans le débogueur avec les mêmes fonctionnalités enrichies.  
  
 Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogueur est le serveur frontal commun (autrement dit, l’interface utilisateur) aux composants de débogage qui, à leur tour, sont spécifiques au langage en cours de débogage. Pour les nouveaux langages, tout ce qui est nécessaire pour la prise en charge par le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogueur consiste à créer les composants principaux nécessaires, tels qu’un moteur de débogage (de). C’est là qu' [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] intervient.  
  
 Le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] comprend une référence complète à tous les [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] éléments requis pour créer un nouveau de. En outre, il existe des exemples et des didacticiels qui vous aideront à démarrer.  
  
 Pour obtenir un exemple de bout en bout d’un système de projet de langage avec prise en charge du débogage, consultez l' [exemple IronPython](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 Les sections suivantes décrivent comment étendre le débogueur à l’aide de [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Décrit ce que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] propose le débogage et comment installer le kit de développement logiciel (SDK).  
  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Documente le processus DE détachement personnalisé, de la préparation de votre programme à un DE pour le détachement DE.  
  
 [Écriture d’un évaluateur d’expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Explique si vous devez écrire un évaluateur d’expression.  
  
 [Choix d’une stratégie de mise en œuvre du moteur de débogage](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Explique comment implémenter votre DE.  
  
 [Référence](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documente l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] API de débogage.  
  
 [Exemples](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contient des liens vers un exemple d’évaluateur d’expression common language runtime et un exemple de moteur de débogage.

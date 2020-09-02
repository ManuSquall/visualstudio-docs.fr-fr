---
title: Prise en main avec l’extensibilité du débogueur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1c616c7cf8ed90ec3d76046892167b9b742a1b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152701"
---
# <a name="getting-started-with-debugger-extensibility"></a>Bien démarrer avec l’extensibilité du débogueur
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Fournit les informations dont vous devez disposer pour créer et personnaliser les composants du débogueur utilisés pour déboguer des programmes à partir de l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environnement.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] le débogage a ajouté des améliorations dérivées des tests d’utilisabilité étendus effectués sur les [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogueurs précédents. Vous pouvez utiliser [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] le débogage pour effectuer un pas à pas détaillé dans une application multilingue, ou vous pouvez implémenter une modification à la volée des variables pendant le débogage d’applications et de solutions multilingues.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] le débogage est exécuté hors processus avec le programme en cours de débogage et est donc moins intrusif dans l’espace de processus de l’application. Par conséquent, il est plus facile d’écrire des composants qui interagissent avec le débogueur sans affecter votre programme de débogage.  
  
 Pour utiliser au mieux le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , vous devez être familiarisé avec les éléments suivants :  
  
- L' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environnement de développement intégré (IDE)  
  
- Langage de programmation C++  
  
- COM ATL  
  
## <a name="in-this-section"></a>Dans cette section  
 [Feuille de route pour l’extension du débogueur](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Décrit le processus d’implémentation du débogage dans votre produit, en fonction de votre compilateur et de sa sortie.  
  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)  
 Fournit une vue d’ensemble des [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] composants de débogage, notamment le moteur de débogage (de), l’évaluateur d’expression (EE) et le gestionnaire de symboles (SH).  
  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts architecturaux du débogage.  
  
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)  
 Explique comment le moteur DE débogage fonctionne simultanément dans le code, la documentation et les contextes d’évaluation des expressions. Décrit, pour chacun des trois contextes, l’emplacement, la position ou l’évaluation qui lui convient.  
  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers différentes tâches de débogage, telles que le lancement d’un programme et l’évaluation d’expressions.

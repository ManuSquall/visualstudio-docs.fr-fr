---
title: Prise en main d’extensibilité du débogueur | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bafdd45b57a9fe660e97127c2c99c333ead0e60a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721165"
---
# <a name="getting-started-with-debugger-extensibility"></a>Bien démarrer avec l’extensibilité du débogueur
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] fournit les informations dont vous devez disposer pour créer et personnaliser les composants du débogueur permet de déboguer des programmes depuis le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environnement.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogage possède des améliorations dérivée de la facilité d’utilisation complète test effectué sur précédente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogueurs. Vous pouvez utiliser [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogage pour parcourir une application multilingue, ou vous pouvez implémenter à la volée, modification des variables pendant le débogage des applications et des solutions de plusieurs langues.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] le débogage est exécutée out-of-process avec le programme en cours de débogage et est par conséquent moins intrusif dans l’espace de processus de l’application. Par conséquent, il est plus facile d’écrire des composants qui interagissent avec le débogueur sans affecter votre programme de débogage.  
  
 Utiliser au mieux le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], vous devez être familiarisé avec les éléments suivants :  
  
-   Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l’environnement de développement intégré (IDE)  
  
-   Le langage de programmation C++  
  
-   ATL COM  
  
## <a name="in-this-section"></a>Dans cette section  
 [Feuille de route pour l’extension du débogueur](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Décrit le processus d’implémentation dans votre produit, en fonction de votre compilateur et sa sortie de débogage.  
  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)  
 Fournit une vue d’ensemble de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] composants, qui incluent le moteur de débogage (DE), évaluateur d’expression (EE) et le Gestionnaire de symboles (SH) de débogage.  
  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts architectures débogage.  
  
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)  
 Explique comment le moteur de débogage (dé) fonctionne simultanément dans le code, documentation et contextes d’évaluation d’expression. Décrit, pour chacun des trois contextes, emplacement, position ou d’évaluation pertinente à ce dernier.  
  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.


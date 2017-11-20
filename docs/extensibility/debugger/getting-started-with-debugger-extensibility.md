---
title: "Prise en main d’extensibilité du débogueur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1419f4e45aefed59aa36b249568a53a47ad3c459
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-debugger-extensibility"></a>Prise en main d’extensibilité du débogueur
Le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fournit les informations dont vous devez disposer pour créer et personnaliser les composants du débogueur permet de déboguer des programmes depuis le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]le débogage a ajouté des améliorations dérivées de la facilité d’utilisation étendue tests effectués sur précédente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogueurs. Vous pouvez utiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de débogage pour accéder à une application dans plusieurs langue, ou vous pouvez implémenter à la volée modifiant des variables pendant le débogage des applications et des solutions de plusieurs langues.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]le débogage est exécutée out-of-process avec le programme débogué et par conséquent moins gênante dans l’espace de processus de l’application. Par conséquent, il est plus facile d’écrire des composants qui interagissent avec le débogueur sans affecter votre programme de débogage.  
  
 Pour utiliser au mieux le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], vous devez être familiarisé avec les éléments suivants :  
  
-   Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE)  
  
-   Le langage de programmation C++  
  
-   ATL COM  
  
## <a name="in-this-section"></a>Dans cette section  
 [Feuille de route pour l’extension du débogueur](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Décrit le processus d’implémentation de votre produit, selon votre compilateur et sa sortie de débogage.  
  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)  
 Fournit une vue d’ensemble de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage de composants, y comprennent le moteur de débogage (DE), évaluateur d’expression (EE) et le Gestionnaire de symboles (es).  
  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts d’architecture débogage.  
  
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)  
 Explique comment le moteur de débogage (DE) fonctionne simultanément dans le code, la documentation et les contextes d’expression d’évaluation. Décrit, pour chacun des trois contextes, emplacement, position ou d’évaluation appropriée à ce dernier.  
  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.
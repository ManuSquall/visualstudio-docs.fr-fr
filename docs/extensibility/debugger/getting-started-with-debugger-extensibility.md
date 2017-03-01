---
title: "Mise en route du débogueur extensibilité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 258fcfcc97d0a6b1455ec60201527cde3e87f9b8
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-debugger-extensibility"></a>Prise en main d’extensibilité du débogueur
Le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fournit les informations dont vous devez disposer pour créer et personnaliser les composants du débogueur utilisés pour déboguer des programmes à partir du [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]débogage possède des améliorations dérivée de la facilité d’utilisation étendue tests effectués sur précédente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogueurs. Vous pouvez utiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de débogage pour accéder à une application dans plusieurs langue, ou vous pouvez implémenter à la volée, modification des variables pendant le débogage des applications et des solutions multilingues.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]le débogage est exécutée out-of-process avec le programme débogué et par conséquent moins intrusif dans l’espace de processus de l’application. Par conséquent, il est plus facile d’écrire des composants qui interagissent avec le débogueur sans affecter votre programme de débogage.  
  
 Utiliser au mieux le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], vous devez être familiarisé avec les éléments suivants :  
  
-   Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE)  
  
-   Le langage de programmation C++  
  
-   ATL COM  
  
## <a name="in-this-section"></a>Dans cette section  
 [Feuille de route pour l’extension du débogueur](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Décrit le processus de mise en œuvre de votre produit, selon votre compilateur et sa sortie de débogage.  
  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)  
 Fournit une vue d’ensemble de le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage de composants, y comprennent le moteur de débogage (DE), évaluateur d’expression (EE) et le Gestionnaire de symboles (es).  
  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts architecturaux de débogage.  
  
 [Contextes de débogueur](../../extensibility/debugger/debugger-contexts.md)  
 Explique comment le moteur de débogage (DE) fonctionne simultanément dans le code, la documentation et contextes d’évaluation d’expression. Décrit, pour chacun des trois contextes, emplacement, position ou évaluation pertinente pour elle.  
  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers les différentes tâches de débogage, telles que le lancement d’un programme et d’évaluer des expressions.

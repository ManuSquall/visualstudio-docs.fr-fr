---
title: "Feuille de route pour l’extension du débogueur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 16
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
ms.openlocfilehash: 49df627aa42cd6cc6ac1430e4e68694fa51a2fc1
ms.lasthandoff: 02/22/2017

---
# <a name="roadmap-for-extending-the-debugger"></a>Feuille de route pour l’extension du débogueur
Cette documentation fournit des informations manuel de référence pour l’extension de la [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] du débogueur avec les [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]documentation relative au débogage inclut des exemples et une référence complète représentatifs scénarios qui illustrent les méthodes classiques de personnaliser le débogueur.  
  
 Votre compilateur et sa sortie déterminent ce que vous devez faire pour implémenter le débogage de votre produit. Si votre compilateur :  
  
-   Cible le système d’exploitation natif et écrit un. Fichier PDB, vous pouvez déboguer des programmes avec le moteur de débogage de code natif (DE), qui est intégré à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Il est inutile d’implémenter un évaluateur DE ou une expression. L’évaluateur d’expression est écrit pour la syntaxe du langage de programmation C++.  
  
-   Produit Microsoft intermediate language (MSIL) de sortie, vous pouvez déboguer des programmes avec le moteur de débogage de code managé DE, qui est également intégré à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Par conséquent, vous devez implémenter uniquement un évaluateur d’expression. Un évaluateur d’expression exemple est fourni pour vous. Pour plus d’informations, consultez les rubriques suivantes :  
  
     [Évaluation d’expression](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [L’évaluation des Expressions](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contexte d’évaluation d’expression](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Évaluation de l’expression en Mode arrêt](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Écriture d’un évaluateur de Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Objectifs d’un système d’exploitation ou un autre environnement d’exécution de propriétaire, vous devez écrire votre propre DE. Un didacticiel qui crée un simple DE l’aide de ATL COM est fourni. Pour plus d’informations, consultez les rubriques suivantes :  
  
     [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Didacticiel : Création d’un moteur de débogage à l’aide de ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [L’implémentation d’un fournisseur de Port](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Exemples](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

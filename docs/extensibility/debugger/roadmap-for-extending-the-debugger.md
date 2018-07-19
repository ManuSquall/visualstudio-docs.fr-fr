---
title: Feuille de route pour l’extension du débogueur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 46c5a8a995644d6876457836674152eb3b3ccad7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128102"
---
# <a name="roadmap-for-extending-the-debugger"></a>Feuille de route pour l’extension du débogueur
Cette documentation fournit des informations de référence et guide pour étendre le [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] du débogueur avec les [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] documentation relative au débogage inclut plusieurs scénarios représentatifs qui illustrent les méthodes classiques de personnaliser le débogueur, exemples et une référence complète.  
  
 C’est votre compilateur et sa sortie déterminent ce que vous devez faire pour implémenter le débogage de votre produit. Si votre compilateur :  
  
-   Cible le système d’exploitation natif et écrit un. Le fichier PDB, vous pouvez déboguer des programmes avec le moteur de débogage de code natif (DE), qui est intégré à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Vous n’avez pas besoin d’implémenter un évaluateur d’expression ou DE. L’évaluateur d’expression est écrite pour connaître la syntaxe du langage de programmation C++.  
  
-   Produit Microsoft intermediate language (MSIL) de sortie, vous pouvez déboguer des programmes avec le moteur de débogage de code managé DE, qui est également intégré [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Par conséquent, vous devez uniquement implémenter un évaluateur d’expression. Un évaluateur d’expression exemple est fourni pour vous. Pour plus d’informations, consultez les rubriques suivantes :  
  
     [Évaluation des expressions](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Évaluation des expressions](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contexte d’évaluation d’expression](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Évaluation d’expression dans le Mode arrêt](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Écriture d’un évaluateur d’expression Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   La cible est un système d’exploitation ou tout autre environnement d’exécution de propriétaire, vous devez écrire votre propre DE. Un didacticiel qui crée un simple D’à l’aide de ATL COM est fourni. Pour plus d’informations, consultez les rubriques suivantes :  
  
     [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Didacticiel : Création d’un moteur de débogage à l’aide de COM ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implémentation d’un fournisseur de port](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Exemples](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
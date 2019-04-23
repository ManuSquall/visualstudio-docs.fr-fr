---
title: Feuille de route pour l’extension du débogueur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59e12a90d241bf07a53cc98c91eef4cfc6d7d063
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050983"
---
# <a name="roadmap-for-extending-the-debugger"></a>Feuille de route pour l’extension du débogueur
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette documentation fournit des informations de référence et guide permettant d’étendre le [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] du débogueur avec les [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentation relative au débogage inclut des exemples, une référence complète et plusieurs scénarios représentatifs qui illustrent les méthodes classiques de personnaliser le débogueur.  
  
 Votre compilateur et sa sortie déterminent ce que vous devez faire pour implémenter le débogage de votre produit. Si votre compilateur :  
  
- Cible le système d’exploitation natif de Windows et écrit un. Fichier PDB, vous pouvez déboguer des programmes avec le moteur de débogage de code natif (DE), qui est intégré à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Vous n’avez pas besoin d’implémenter un évaluateur DE ou une expression. L’évaluateur d’expression est écrite pour connaître la syntaxe du langage de programmation C++.  
  
- Produit Microsoft intermediate language (MSIL) de la sortie, vous pouvez déboguer des programmes avec le moteur de débogage de code managé DE, qui est également intégré à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Par conséquent, vous devez implémenter uniquement un évaluateur d’expression. Un évaluateur d’expression exemple est fourni pour vous. Pour plus d’informations, consultez les rubriques suivantes :  
  
     [Évaluation des expressions](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Évaluation des expressions](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contexte d’évaluation d’expression](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Évaluation d’expression dans le Mode arrêt](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Écriture d’un évaluateur d’expression Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Cibles un propriétaire de système d’exploitation ou un autre environnement d’exécution, vous devez écrire votre propre DE. Un didacticiel qui crée un simple D’à l’aide de ATL COM est fourni. Pour plus d’informations, consultez les rubriques suivantes :  
  
     [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Tutoriel : Création d’un moteur de débogage à l’aide de ATL COM](http://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implémentation d’un fournisseur de port](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Exemples](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

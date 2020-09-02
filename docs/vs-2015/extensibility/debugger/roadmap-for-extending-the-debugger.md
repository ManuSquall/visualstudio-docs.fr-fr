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
ms.openlocfilehash: 89a07bc5a5c4c8b7a6054b53610325c654355bc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695959"
---
# <a name="roadmap-for-extending-the-debugger"></a>Feuille de route pour l’extension du débogueur
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette documentation fournit des informations de référence et de guide pour l’extension du [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] débogueur avec le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] la documentation sur le débogage comprend des exemples, une référence complète et plusieurs scénarios représentatifs qui illustrent des méthodes typiques de personnalisation du débogueur.  
  
 Votre compilateur et sa sortie déterminent ce que vous devez faire pour implémenter le débogage dans votre produit. Si votre compilateur :  
  
- Cible le système d’exploitation Windows natif et écrit un. Fichier PDB, vous pouvez déboguer des programmes avec le moteur DE débogage DE code natif (DE), qui est intégré dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Vous n’avez pas besoin d’implémenter un évaluateur DE ou d’expression. L’évaluateur d’expression est écrit pour la syntaxe du langage de programmation C++.  
  
- Produit une sortie MSIL (Microsoft Intermediate Language), vous pouvez déboguer des programmes à l’aide du moteur DE débogage du code managé DE, qui est également intégré à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Par conséquent, vous n’avez besoin que d’implémenter un évaluateur d’expression. Un exemple d’évaluateur d’expression est fourni pour vous. Pour plus d'informations, voir les rubriques suivantes :  
  
     [Évaluation d’expression](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Évaluer des expressions](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contexte d’évaluation d’expression](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Évaluation d’expression dans le Mode arrêt](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Écriture d’un évaluateur d’expression Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Cible un système d’exploitation propriétaire ou un autre environnement d’exécution, vous devez écrire votre propre. Un didacticiel qui permet de créer un simple à l’aide d’ATL COM est fourni. Pour plus d'informations, voir les rubriques suivantes :  
  
     [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Didacticiel : création d’un moteur de débogage à l’aide d’ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implémentation d’un fournisseur de port](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Exemples](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

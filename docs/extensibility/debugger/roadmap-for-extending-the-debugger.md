---
title: Feuille de route pour l’extension du débogueur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e02bfd8b528c484518816589f4f3e0e19bfa8c94
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687521"
---
# <a name="roadmap-for-extending-the-debugger"></a>Feuille de route pour l’extension du débogueur
Cette documentation fournit des informations de référence et guide permettant d’étendre le [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] du débogueur avec les [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] documentation relative au débogage inclut des exemples, une référence complète et plusieurs scénarios représentatifs qui illustrent les méthodes classiques de personnaliser le débogueur.

 Votre compilateur et sa sortie déterminent les éléments requis pour configurer le débogage de votre produit. Si votre compilateur :

- Cible le système d’exploitation natif de Windows et écrit un *. PDB* fichier, vous pouvez déboguer des programmes avec le moteur de débogage de code natif (DE), qui est intégré à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Vous n’avez pas besoin d’implémenter un évaluateur DE ou une expression. L’évaluateur d’expression est écrite pour connaître la syntaxe du langage de programmation C++.

- Produit Microsoft intermediate language (MSIL) de la sortie, vous pouvez déboguer des programmes avec le moteur de débogage de code managé DE, qui est également intégré à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Par conséquent, vous devez implémenter uniquement un évaluateur d’expression. Un évaluateur d’expression exemple est fourni pour vous. Pour plus d’informations, consultez les rubriques suivantes :

   [Évaluation de l’expression](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [L’évaluation des expressions](../../extensibility/debugger/evaluating-expressions.md)

   [Contexte d’évaluation d’expression](../../extensibility/debugger/expression-evaluation-context.md)

   [Évaluation de l’expression en mode arrêt](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Écrire un évaluateur de common language runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Cibles un propriétaire de système d’exploitation ou un autre environnement d’exécution, vous devez écrire votre propre DE. Un didacticiel qui crée un simple D’à l’aide de ATL COM est fourni. Pour plus d’informations, consultez les rubriques suivantes :

   [Créer un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Tutoriel : Créer un moteur de débogage à l’aide de ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [Implémenter un fournisseur de port](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Exemples](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Voir aussi
- [Bien démarrer](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
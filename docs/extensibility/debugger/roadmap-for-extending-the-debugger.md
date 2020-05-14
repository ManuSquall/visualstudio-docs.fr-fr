---
title: Feuille de route pour l’extension du Débbugger (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e809eeb6a1a5d2c24368932713d69c7199b5af38
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713146"
---
# <a name="roadmap-for-extending-the-debugger"></a>Feuille de route pour l’extension du débbugger
Cette documentation fournit des informations [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] de guide et [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]de référence pour étendre le débbuggeur avec le .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]La documentation de débogage comprend des échantillons, une référence complète et plusieurs scénarios représentatifs qui démontrent des façons typiques de personnaliser le débogage.

 Votre compilateur et sa sortie déterminent ce qui est nécessaire pour configurer le débogage dans votre produit. Si votre compilateur:

- Cible le système d’exploitation natif de Windows et écrit un *. Fichier PDB,* vous pouvez déboiffer des programmes avec le moteur [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de déboisation de code natif (DE), qui est intégré dans . Vous n’avez pas besoin de mettre en œuvre un DE ou un évaluateur d’expression. L’évaluateur de l’expression est écrit pour la syntaxe du langage de programmation de C.

- Produit Microsoft langue intermédiaire (MSIL) sortie, vous pouvez déboiffer des programmes avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]le code géré debug moteur DE, qui est également intégré dans . Ainsi, vous n’avez qu’à mettre en œuvre un évaluateur d’expression. Un évaluateur d’expression d’échantillon est fourni pour vous. Pour plus d'informations, voir les rubriques suivantes :

   [Évaluation de l’expression](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Évaluation des expressions](../../extensibility/debugger/evaluating-expressions.md)

   [Contexte d’évaluation de l’expression](../../extensibility/debugger/expression-evaluation-context.md)

   [Évaluation de l’expression en mode pause](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Écrire un évaluateur d’expression de course de langue commune](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Cible un système d’exploitation propriétaire ou un autre environnement de temps d’exécution, vous devez écrire votre propre DE. Un tutoriel qui crée un SIMPLE DE en utilisant ATL COM est fourni. Pour plus d'informations, voir les rubriques suivantes :

   [Créer un moteur de débogé personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Tutorial: Construire un moteur de débogé à l’aide d’ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [Mettre en œuvre un fournisseur portuaire](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Exemples](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Voir aussi
- [Bien démarrer](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

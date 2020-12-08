---
title: Feuille de route pour l’extension du débogueur | Microsoft Docs
description: La documentation sur le débogage de Visual Studio comprend des exemples, une référence et plusieurs scénarios qui illustrent des méthodes typiques pour personnaliser le débogueur.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2574fe76faadf4284088c0d47592d0c5ba0d38f9
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848337"
---
# <a name="roadmap-for-extending-the-debugger"></a>Feuille de route pour l’extension du débogueur
Cette documentation fournit des informations de référence et de guide pour l’extension du [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] débogueur avec le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la documentation sur le débogage comprend des exemples, une référence complète et plusieurs scénarios représentatifs qui illustrent des méthodes typiques de personnalisation du débogueur.

 Votre compilateur et sa sortie déterminent ce qui est requis pour configurer le débogage dans votre produit. Si votre compilateur :

- Cible le système d’exploitation Windows natif et écrit un *. Fichier PDB* , vous pouvez déboguer des programmes avec le moteur de débogage de code natif (de), qui est intégré dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Vous n’avez pas besoin d’implémenter un évaluateur DE ou d’expression. L’évaluateur d’expression est écrit pour la syntaxe du langage de programmation C++.

- Produit une sortie MSIL (Microsoft Intermediate Language), vous pouvez déboguer des programmes à l’aide du moteur DE débogage du code managé DE, qui est également intégré à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Par conséquent, vous n’avez besoin que d’implémenter un évaluateur d’expression. Un exemple d’évaluateur d’expression est fourni pour vous. Pour plus d'informations, voir les rubriques suivantes :

   [Évaluation d’expression](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Évaluer des expressions](../../extensibility/debugger/evaluating-expressions.md)

   [Contexte d’évaluation de l’expression](../../extensibility/debugger/expression-evaluation-context.md)

   [Évaluation d’expression en mode arrêt](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Écrire un évaluateur d’expression common language runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Cible un système d’exploitation propriétaire ou un autre environnement d’exécution, vous devez écrire votre propre. Un didacticiel qui permet de créer un simple à l’aide d’ATL COM est fourni. Pour plus d'informations, voir les rubriques suivantes :

   [Créer un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Didacticiel : créer un moteur de débogage à l’aide d’ATL COM](/previous-versions/bb147024(v=vs.90))

   [Implémenter un fournisseur de port](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Exemples](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Voir aussi
- [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
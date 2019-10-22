---
title: 'Comment : activer et désactiver l’analyse complète de la solution pour le code managé | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 72b27bf9dcc1f0ee8a222ac701f2ffae4fc68614
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646290"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Comment : activer et désactiver l’analyse complète de la solution pour le code managé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

REMARQUE]
> Cette rubrique s’applique uniquement à Visual Studio 2015 Update 3 RC et versions ultérieures.

 L' *analyse complète* de la solution est une fonctionnalité de Visual Studio qui vous permet de choisir si vous voyez des problèmes d' C# analyse du code uniquement dans des fichiers Visual ou Visual Basic ouverts dans votre solution C# , ou à la fois dans des fichiers visuels ouverts et fermés ou dans des fichiers Visual Basic de votre elle.

 Bien qu’il soit possible de voir tous les problèmes dans tous les fichiers, il peut être gênant et même ralentir Visual Studio si votre solution est très volumineuse ou si elle contient un grand nombre de fichiers.  Pour limiter le nombre de problèmes affichés et améliorer les performances de Visual Studio, vous pouvez désactiver l’analyse complète de la solution. Vous pouvez facilement réactiver cette fonctionnalité si vous le souhaitez.

#### <a name="to-toggle-full-solution-analysis"></a>Pour activer/désactiver l’analyse complète de la solution

1. Dans le menu principal de Visual Studio, choisissez **Outils** &#124; **options** pour afficher la boîte de dialogue **options** .

2. Dans la boîte de dialogue **options** , **Choisissez éditeur** &#124; **C#** de texte ou **avancé**de **base** &#124; .

3. Cochez la case **activer l’analyse complète** de la solution pour activer l’analyse complète de la solution, ou désactivez la case à cocher pour la désactiver. Lorsque vous avez terminé, choisissez le bouton **OK** .

     ![Case à cocher Activer l’analyse complète de la solution.](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Résultats de l’activation et de la désactivation de l’analyse complète de la solution
 Dans la capture d’écran suivante, vous pouvez voir les résultats lorsque l’analyse complète de la solution est activée. Toutes les erreurs et tous les problèmes liés à l’analyse du code dans *tous* les fichiers de la solution s’affichent, que les fichiers soient ouverts ou non.

 ![Analyse complète de la solution activée.](../code-quality/media/fsa-enabled.png "FSA_Enabled")

 La capture d’écran suivante montre les résultats de la même solution après la désactivation de l’analyse complète de la solution. Seules les erreurs et les problèmes d’analyse du code dans les fichiers solution ouverts apparaissent dans le Liste d’erreurs.

 ![Analyse complète de la solution désactivée.](../code-quality/media/fsa-disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>Désactivation automatique de l’analyse complète de la solution
 Si Visual Studio détecte qu’il n’y a pas plus de 200 Mo de mémoire système disponible, il désactive automatiquement l’analyse complète de la solution (ainsi que d’autres fonctionnalités) si elle est activée. Si cela se produit, une alerte s’affiche pour vous en informer. Un bouton vous permet de réactiver l’analyse complète de la solution si vous le souhaitez.

 ![Texte d’alerte interruption de l’analyse complète de la solution](../code-quality/media/fsa-alert.png "FSA_Alert")

## <a name="additional-details"></a>Détails supplémentaires
 Par défaut, l’analyse complète de la solution est activée pour Visual Basic et C#désactivée pour Visual.

 Visual Studio Update 3 RC comprend un moteur de diagnostic amélioré de l’analyseur de code v2 qui réduit considérablement l’utilisation de la mémoire et réduit le temps processeur à inactif, même si l’analyse complète de la solution est activée.

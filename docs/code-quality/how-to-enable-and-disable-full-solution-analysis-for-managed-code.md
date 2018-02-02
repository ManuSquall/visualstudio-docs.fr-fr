---
title: "Comment : activer et désactiver l’analyse de la Solution complète pour le Code managé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 64b541093aaf1a710976c0f53a3214b5d2a47e0d
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Comment : activer et désactiver l’analyse de solution complète pour le code managé

*L’analyse complète* est une fonctionnalité de Visual Studio qui vous permet de voir les problèmes d’analyse de code uniquement dans des fichiers Visual c# ou Visual Basic ouverts dans votre solution, ou également dans le code des fichiers qui sont fermées. Par défaut, l’analyse complète de la solution est activée pour Visual Basic et désactivée pour Visual c#.

S’il est utile de pouvoir voir tous les problèmes dans tous les fichiers, il peut être perturbante. Il peut également lente Visual Studio vers le bas si votre solution est très volumineux ou possède un grand nombre de fichiers. Pour limiter le nombre de problèmes indiqué et améliorer les performances de Visual Studio, vous pouvez désactiver l’analyse complète de la solution. Vous pouvez facilement réactiver cette fonctionnalité si nécessaire.

## <a name="to-toggle-full-solution-analysis"></a>Pour activer/désactiver l’analyse complète de la solution

1. Pour ouvrir la **Options** choisir de la boîte de dialogue, dans la barre de menus dans Visual Studio **outils** > **Options**.

1. Dans le **Options** boîte de dialogue, choisissez **éditeur de texte** > **c#** ou **base**  >   **Advanced**.

1. Sélectionnez le **activer l’analyse de la solution complète** case à cocher pour activer l’analyse complète de la solution, ou désactivez la case pour le désactiver. Choisissez le **OK** bouton lorsque vous avez terminé.

    ![Activez la case à cocher analyse complète de la solution. ] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Résultats de l’activation et désactivation de l’analyse complète de la solution

Dans la capture d’écran suivante, vous pouvez voir les résultats lorsque l’analyse complète de la solution est activée. Toutes les erreurs et problèmes d’analyse de code dans *tous les* des fichiers dans la solution apparaissent, indépendamment de si les fichiers sont ouverts ou non.

![Analyse de la solution complète activée. ] (../code-quality/media/fsa_enabled.png "FSA_Enabled")

La capture d’écran suivante montre les résultats à partir de la même solution après la désactivation de l’analyse complète de la solution. Uniquement les erreurs et les problèmes d’analyse de code dans ouvrent solution fichiers s’affichent dans la liste d’erreurs.

![Analyse complète de la solution désactivé. ] (../code-quality/media/fsa_disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>Désactivant l’analyse complète de la solution

Si Visual Studio détecte que 200 Mo ou moins de mémoire système disponible à ce dernier, il désactive automatiquement l’analyse complète de la solution (ainsi que d’autres fonctionnalités) s’il est activé. Si cela se produit, une alerte s’affiche pour vous en informe. Un bouton vous permet de réactiver l’analyse complète de la solution si vous le souhaitez.

![Texte d’alerte la suspension de l’analyse complète de la solution](../code-quality/media/fsa_alert.png "FSA_Alert")
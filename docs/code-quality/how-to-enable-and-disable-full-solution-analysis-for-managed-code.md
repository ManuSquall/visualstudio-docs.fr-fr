---
title: 'Comment : activer et désactiver l’analyse de la Solution complète pour le Code managé | Documents Microsoft'
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 5221f2a97f892f272cce33b4f464a9ff223e8824
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Comment : activer et désactiver l’analyse de solution complète pour le code managé

*L’analyse complète* est une fonctionnalité de Visual Studio qui vous permet de voir les problèmes d’analyse de code uniquement dans des fichiers Visual c# ou Visual Basic ouverts dans votre solution, ou également dans le code des fichiers qui sont fermées. Par défaut, l’analyse complète de la solution est *activé* pour Visual Basic, et *désactivé* pour Visual c#.

Il peut être utile voir tous les problèmes dans tous les fichiers, mais il peut également être perturbante. Cela ralentit Visual Studio si votre solution est très volumineux ou de fichiers. Pour limiter le nombre de problèmes indiqué et améliorer les performances de Visual Studio, vous pouvez désactiver l’analyse complète de la solution. Vous pouvez facilement réactiver cette fonctionnalité si nécessaire.

## <a name="to-toggle-full-solution-analysis"></a>Pour activer/désactiver l’analyse complète de la solution

1. Pour ouvrir la **Options** choisir de la boîte de dialogue, dans la barre de menus dans Visual Studio **outils** > **Options**.

1. Dans le **Options** boîte de dialogue, choisissez **éditeur de texte** > **c#** ou **base**  >   **Advanced**.

1. Sélectionnez le **activer l’analyse de la solution complète** case à cocher pour activer l’analyse complète de la solution, ou désactivez la case pour le désactiver. Choisissez **OK** lorsque vous avez terminé.

    ![Activez la case à cocher analyse complète de la solution.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Résultats de l’activation et désactivation de l’analyse complète de la solution

Dans la capture d’écran suivante, vous pouvez voir les résultats lorsque l’analyse complète de la solution est activée. Toutes les erreurs et problèmes d’analyse de code dans *tous les* des fichiers dans la solution apparaissent, indépendamment de si les fichiers sont ouverts ou non.

![Analyse de la solution complète activée.](../code-quality/media/fsa_enabled.png)

La capture d’écran suivante montre les résultats à partir de la même solution après la désactivation de l’analyse complète de la solution. Uniquement les erreurs et les problèmes d’analyse de code dans les fichiers de la solution ouverte s’affichent dans le **liste d’erreurs**.

![Analyse complète de la solution désactivé.](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>La désactivation automatique de l’analyse complète de la solution

Si Visual Studio détecte que 200 Mo ou moins de mémoire système disponible à ce dernier, il désactive automatiquement l’analyse complète de la solution (et autres fonctionnalités) s’il est activé. Si cela se produit, une alerte s’affiche vous informant que Visual Studio a désactivé certaines fonctionnalités. Un bouton vous permet de réactiver l’analyse complète de la solution si vous le souhaitez.

![Texte d’alerte la suspension de l’analyse complète de la solution](../code-quality/media/fsa_alert.png)
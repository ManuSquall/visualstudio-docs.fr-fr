---
title: Activer et désactiver l’analyse complète de la solution pour le code managé
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a445439014e3b1f68b634865265089eb68e790a6
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260878"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Procédure : Activer et désactiver l’analyse complète de la solution pour le code managé

*Complète l’analyse de la solution* est une fonctionnalité de Visual Studio qui vous permet de voir les problèmes d’analyse de code uniquement dans Visual open C# ou des fichiers de Visual Basic dans votre solution, ou également dans les fichiers de code sont fermées. Par défaut, l’analyse complète de la solution est *activé* pour Visual Basic, et *désactivé* pour Visual C#.

Il peut être utile voir tous les problèmes dans tous les fichiers, mais il peut également être perturbant. Elle ralentit Visual Studio si votre solution est très volumineux ou comporte de nombreux fichiers. Pour limiter le nombre de problèmes indiqué et améliorer les performances de Visual Studio, vous pouvez désactiver l’analyse complète de la solution. Vous pouvez facilement réactiver cette fonctionnalité si nécessaire.

## <a name="to-toggle-full-solution-analysis"></a>Pour activer/désactiver l’analyse complète de la solution

1. Pour ouvrir le **Options** boîte de dialogue, dans la barre de menus dans Visual Studio choisir **outils** > **Options**.

1. Dans le **Options** boîte de dialogue, sélectionnez **éditeur de texte**  >  **C#** ou **base**  >  **Advanced**.

1. Sélectionnez le **activer l’analyse complète de la solution** case à cocher pour activer l’analyse complète de la solution, ou désactivez la case pour le désactiver. Choisissez **OK** lorsque vous avez terminé.

    ![Activez la case à cocher analyse complète de la solution.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Résultats de l’activation et désactivation de l’analyse complète de la solution

Dans la capture d’écran suivante, vous pouvez voir les résultats lorsque l’analyse complète de la solution est activée. Toutes les erreurs et problèmes d’analyse de code dans *tous les* des fichiers dans la solution apparaissent, indépendamment de si les fichiers sont ouverts ou non.

![Analyse complète de la solution est activée.](../code-quality/media/fsa_enabled.png)

La capture d’écran suivante montre les résultats à partir de la même solution après la désactivation de l’analyse complète de la solution. Uniquement les erreurs et les problèmes d’analyse de code dans les fichiers de la solution ouverte apparaissent dans le **liste d’erreurs**.

![L’analyse est désactivée.](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>Automatiquement désactiver l’analyse complète de la solution

Si Visual Studio détecte que 200 Mo ou moins de mémoire système disponible à ce dernier, il désactive automatiquement l’analyse complète de la solution (et autres fonctionnalités) s’il est activé. Si cela se produit, une alerte s’affiche vous informant que Visual Studio a désactivé certaines fonctionnalités. Un bouton vous permet de réactiver l’analyse complète de la solution si vous le souhaitez.

![Texte de l’alerte la suspension de l’analyse complète de la solution](../code-quality/media/fsa_alert.png)
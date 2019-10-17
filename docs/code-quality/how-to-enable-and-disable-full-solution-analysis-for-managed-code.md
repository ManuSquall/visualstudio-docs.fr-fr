---
title: Activer & désactiver l’analyse complète de la solution pour le code managé
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 26cd267f80f8c7c220771a5c2220d22b66929051
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448925"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Comment : activer et désactiver l’analyse complète de la solution pour le code managé

L' *analyse complète* de la solution signifie que l’analyse du C# code examine tous les fichiers ou Visual Basic dans la solution, qu’ils soient ouverts ou non dans l’éditeur. Par défaut, l’analyse complète de la solution est *activée* pour Visual Basic C#et *désactivée* pour.

Il peut être utile de voir tous les problèmes dans tous les fichiers, mais cela peut également être gênant. Elle ralentit Visual Studio si votre solution est très volumineuse ou contient de nombreux fichiers. Pour limiter le nombre de problèmes affichés et améliorer les performances de Visual Studio, vous pouvez désactiver l’analyse complète de la solution. Vous pouvez facilement réactiver cette fonctionnalité si nécessaire.

Dans l’image suivante, l’analyse complète de la solution est activée. Les problèmes liés à l’analyse du compilateur et du code dans tous les fichiers de la solution s’affichent, même s’ils ne sont pas ouverts.

![Analyse complète de la solution activée.](../code-quality/media/fsa_enabled.png)

L’illustration suivante montre les résultats de la même solution après la désactivation de l’analyse complète de la solution. Seules les erreurs de compilateur et les problèmes d’analyse du code dans les fichiers solution ouverts apparaissent dans le Liste d’erreurs.

![Analyse complète de la solution désactivée.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Activer/désactiver l’analyse complète de la solution

1. Pour ouvrir la boîte de dialogue **options** , dans la barre de menus de Visual Studio, choisissez **Outils** > **options**.

1. Dans la boîte de dialogue **options** , choisissez **éditeur de texte**@no__t**C#** -2 ou @no__t de **base**-6**avancé**.

1. Cochez la case **activer l’analyse complète** de la solution pour activer l’analyse complète de la solution, ou désactivez la case à cocher pour la désactiver. Lorsque vous avez terminé, choisissez **OK** .

   ![Case à cocher Activer l’analyse complète de la solution.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Désactiver automatiquement l’analyse complète de la solution

Si Visual Studio détecte que 200 Mo ou moins de mémoire système est disponible, il désactive automatiquement l’analyse complète de la solution (et d’autres fonctionnalités) si elle est activée. Dans ce cas, une alerte s’affiche vous informant que Visual Studio a désactivé certaines fonctionnalités. Un bouton vous permet de réactiver l’analyse complète de la solution si vous le souhaitez.

![Texte d’alerte interruption de l’analyse complète de la solution](../code-quality/media/fsa_alert.png)

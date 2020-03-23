---
title: Activez & désactiver l’analyse complète des solutions pour le code géré
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d699dd74315cfc36820c1cdb4120543e0290b1a1
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79428270"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Comment : Activer et désactiver l’analyse complète des solutions pour le code géré

*L’analyse complète* des solutions signifie que l’analyse de code examine tous les fichiers C ou Visual Basic de la solution, qu’ils soient ouverts ou non dans l’éditeur. Par défaut, l’analyse complète des solutions est *activée* pour Visual Basic et *désactivée* pour C.

Il peut être utile de voir toutes les questions dans tous les fichiers, mais il peut également être distrayant. Il ralentit Visual Studio si votre solution est très grande ou a de nombreux fichiers. Pour limiter le nombre de problèmes affichés et améliorer les performances de Visual Studio, vous pouvez désactiver l’analyse complète des solutions. Vous pouvez facilement réenable cette fonctionnalité si nécessaire.

Dans l’image suivante, l’analyse complète de la solution est activée. Les problèmes de compilateur et d’analyse de code dans tous les fichiers de la solution sont affichés, même s’ils ne sont pas ouverts.

![Analyse de solution complète activée.](../code-quality/media/fsa_enabled.png)

L’image suivante montre les résultats de la même solution après avoir désactivé l’analyse complète de la solution. Seules les erreurs de compilation et les problèmes d’analyse de code dans les fichiers de solutions ouvertes apparaissent dans la liste d’erreurs.

![Analyse complète des solutions désactivée.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Analyse complète des solutions de bascule

1. Pour ouvrir la boîte de dialogue **Options,** sur le menu bar de Visual Studio, choisissez **Tools** > **Options**.

1. Dans la boîte de dialogue **Options,** choisissez **Text Editor** > **CMD** ou **Basic** > **Advanced**.

1. Sélectionnez la case à cocher **d’analyse de solution complète Enable** pour permettre l’analyse complète de la solution, ou effacez la case pour la désactiver. Choisissez **OK** quand vous avez terminé.

   ![Activez la case à cocher d’analyse de solution complète.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Désactiver automatiquement l’analyse complète des solutions

Si Visual Studio détecte que 200 Mo ou moins de mémoire système est à sa disposition, il désactive automatiquement l’analyse complète des solutions (et d’autres fonctionnalités) si elle est activée. Si cela se produit, une alerte apparaît vous informant que Visual Studio a désactivé certaines fonctionnalités. Un bouton vous permet d’analyser la solution complète si vous le souhaitez.

![Texte d’alerte suspendant l’analyse complète de solution](../code-quality/media/fsa_alert.png)

---
title: Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code
description: Découvrez comment vous pouvez exécuter des analyseurs sur des cartes de code pour vous aider à identifier le code qui peut être trop complexe ou qui peut nécessiter une amélioration.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8817e50ae96a27f6b3b76e28262390271c1fdf4c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388852"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code

Exécutez des analyseurs sur des cartes de code pour vous aider à identifier le code susceptible d’être trop complexe ou de devoir être amélioré. Vous pouvez par exemple utiliser ces analyseurs :

|**Pour rechercher du code ayant**|**Examinez ces zones pour voir si**|
|-|-|
|Des boucles ou des dépendances circulaires|Vous pouvez les simplifier et envisager de rompre ces cycles.|
|Trop de dépendances|Elles exécutent trop de fonctions ou pour déterminer l’impact de la modification de ces zones. Une carte de code correcte affiche un nombre minimal de dépendances. Pour que le code soit plus facile à tenir à jour, à modifier, à tester et à réutiliser, essayez de refactoriser ces zones pour qu’elles soient plus clairement définies ou de fusionner du code qui exécute des fonctions similaires.|
|Aucune dépendance|Elles sont nécessaires ou si vous devez supprimer ce code.|

## <a name="analyze-code-maps"></a>Analyser les cartes de code

Dans la barre d’outils de la carte, choisissez  >  **analyseurs** de page, puis l’analyseur que vous souhaitez exécuter :

|**Analyseur**|**Pour identifier les nœuds qui**|
|-|-|
|**Analyseur de références circulaires**|Ont des dépendances circulaires les unes envers les autres. **Remarque :**  Les dépendances circulaires qui se trouvent dans le groupe **génériques** ne sont pas affichées sur la carte lorsque vous développez le groupe.|
|**Rechercher l’analyseur de hubs**|Figurent dans les premiers 25 % des nœuds hautement connectés<br /><br /> **Pour masquer tous les autres nœuds de la carte**<br /><br /> -Ouvrez le menu contextuel de la carte, choisissez **avancé**, **Sélectionner**, **Masquer non sélectionné**.<br />     La carte masque les nœuds non sélectionnés et l’analyseur identifie les nouveaux nœuds en tant que hubs.|
|**Analyseur de nœuds non référencés**|N’ont pas de références d’autres nœuds. **Attention :**  Vérifiez chacun de ces cas avant de supposer que le code n’est pas utilisé. Certaines dépendances, telles que les dépendances XAML et d’exécution, sont introuvables statiquement dans le code.|

Les analyseurs de carte de code continuent de s’exécuter après leur application. Si vous modifiez la carte, les analyseurs appliqués retraitent automatiquement la carte mise à jour. Pour arrêter l’exécution d’un analyseur, dans la barre d' outils de la carte, choisissez  >  **analyseurs** de disposition. Désactivez l’analyseur sélectionné.

> [!TIP]
> Si votre carte est très grande, l’exécution d’un analyseur peut provoquer une exception en raison de mémoire insuffisante. Si cela se produit, modifiez la carte pour réduire sa portée ou générez-en une plus petite, puis exécutez l’analyseur.

## <a name="see-also"></a>Voir aussi

- [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)
- [Utiliser des cartes du code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)
- [Mapper les méthodes sur la pile des appels tout en déboguant](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

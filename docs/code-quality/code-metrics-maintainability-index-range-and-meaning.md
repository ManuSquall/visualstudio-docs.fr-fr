---
title: Métriques du code-plage d’index de maintenabilité et signification
ms.date: 1/8/2021
description: En savoir plus sur la métrique de plage d’index de maintenabilité pour les métriques du code dans Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aa825b439b75606da136635d5816ac3e19ea8392
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860462"
---
# <a name="code-metrics---maintainability-index-range-and-meaning"></a>Métriques du code-plage d’index de maintenabilité et signification

Question : l’index de maintenabilité a été réinitialisé à une valeur comprise entre 0 et 100. Comment et pourquoi cela a-t-il été fait ?

La mesure a été calculée à l’origine comme suit : `Maintainability Index = 171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code)`

L’utilisation de cette formule signifiait qu’elle était comprise entre 171 et un nombre négatif illimité.  À mesure que le code était très proche de 0, il était clairement difficile de maintenir le code et la différence entre code 0 et une valeur négative n’était pas utile.  En raison de l’utilité décroissante des nombres négatifs et de la volonté de conserver la mesure aussi claire que possible, nous avons décidé de traiter tous les index de 0 à 0, puis de rebaser la plage 171 ou moins pour être comprise entre 0 et 100. Pour cette raison, la formule que nous utilisons est la suivante :

   `Maintainability Index = MAX(0,(171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code))*100 / 171)`

En outre, nous avons décidé d’être conservateur avec les seuils.  Le souhait était que si l’index avait un rouge, nous aurions pu faire confiance à un problème avec le code.  Cela nous a donné les seuils suivants :

Pour les seuils, nous avons décidé de décomposer cette plage de 0-100 à 80-20 pour maintenir le niveau de bruit faible et nous n’indiquons que le code suspect. Nous avons utilisé les seuils suivants :

- 0-9 = rouge
- 10-19 = jaune
- 20-100 = vert

---
title: Métriques du code-profondeur d’héritage
ms.date: 1/8/2021
description: En savoir plus sur la profondeur de la métrique d’héritage pour les métriques du code dans Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1d6ac085463087fc73aac4429488ab475e91c10f
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2021
ms.locfileid: "109682660"
---
# <a name="code-metrics---depth-of-inheritance-dit"></a>Métriques du code-profondeur de l’héritage (DIT)

Dans cet article, vous allez découvrir l’une des métriques conçues spécifiquement pour l’analyse orientée objet : profondeur d’héritage. La profondeur d’héritage, également appelée profondeur de l’arborescence d’héritage (DIT), est définie comme « longueur maximale du nœud jusqu’à la racine de l’arborescence » [CK](#ck). Vous pouvez le voir avec un exemple simple. Créez un projet de bibliothèque de classes et, avant d’écrire du code, calculez les métriques du code en choisissant **analyser > calculer les métriques du code pour la solution**.

![Exemple 1 de profondeur d’héritage](media/depth-of-inheritance-example-1.png)

Étant donné que toutes les classes héritent de `System.Object` , la profondeur est 1 actuellement. Si vous héritez de cette classe et examinez la nouvelle classe, vous pouvez voir le résultat :

![Exemple 2 de profondeur d’héritage](media/depth-of-inheritance-example-2.png)

Notez que le nœud le plus bas dans l’arborescence ( `Class2` dans ce cas), plus la profondeur d’héritage est élevée. Vous pouvez continuer à créer des enfants et faire en sorte que la profondeur augmente autant que vous le souhaitez.

## <a name="assumptions"></a>Hypothèses

La profondeur d’héritage est prédicat sur [trois hypothèses fondamentales](#ck):

1. Plus une classe de la hiérarchie est profonde, plus le nombre de méthodes qu’elle héritera probablement, plus il est difficile de prédire son comportement.

2. Les arborescences plus approfondies impliquent une complexité de conception supérieure, car davantage de classes et de méthodes sont impliquées.

3. Les classes plus approfondies dans l’arborescence ont un plus grand potentiel pour réutiliser des méthodes héritées.

Les hypothèses 1 et 2 vous indiquent qu’un nombre plus élevé pour la profondeur est incorrect. Si c’est là qu’il se termine, vous seriez en bonne forme ; Toutefois, l’hypothèse 3 indique qu’un nombre plus élevé pour la profondeur est idéal pour la réutilisation potentielle du code.

## <a name="analysis"></a>Analyse

Voici comment lire la mesure de profondeur :

- Nombre faible pour la profondeur

  Un nombre faible pour la profondeur implique moins de complexité, mais également la possibilité de réduire la réutilisation du code par héritage.

- Nombre élevé pour la profondeur

  Un nombre élevé pour la profondeur implique un potentiel de réutilisation du code par héritage, mais également une plus grande complexité avec une probabilité plus élevée d’erreurs dans le code.

## <a name="code-analysis"></a>Analyse du code

L’analyse du code comprend une catégorie de règles de maintenabilité. Pour plus d’informations, consultez [règles de maintenabilité](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). Lors de l’utilisation de l’analyse du code hérité, l’ensemble de règles de l’instruction de conception étendue contient une zone de maintenabilité :

![Profondeur des instructions de conception d’héritage ensembles de règles](media/depth-of-inheritance-design-guidelines.png)

Dans la zone de maintenabilité se trouve une règle d’héritage :

![Règle de maintenance de profondeur d’héritage](media/depth-of-inheritance-maintainability-rule.png)

Cette règle émet un avertissement lorsque la profondeur d’héritage atteint 6 ou plus. il s’agit donc d’une bonne règle pour éviter un héritage excessif. Pour en savoir plus sur la règle, consultez [CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501).

## <a name="putting-it-all-together"></a>Ensemble

Des valeurs élevées pour DIT signifie que le risque d’erreurs est également élevé, les valeurs basses réduisent les risques d’erreurs. Les valeurs élevées pour DIT indiquent un potentiel plus important pour la réutilisation du code par héritage, les valeurs basses suggèrent moins de réutilisation du code que l’héritage pour tirer parti. En raison de l’absence de données suffisantes, il n’existe pas de norme actuellement acceptée pour les valeurs DIT. Même les études effectuées récemment n’ont pas trouvé suffisamment de données pour déterminer un nombre viable pouvant être utilisé comme nombre standard pour cette mesure [Shatnawi](#shatnawi). Bien qu’il n’existe pas de preuve empirique pour la prise en charge, plusieurs ressources suggèrent qu’une DIT environ 5 ou 6 doit être une limite supérieure. Par exemple, consultez [http://www.devx.com/architect/Article/45611](http://www.devx.com/architect/Article/45611) .

## <a name="citations"></a>Citations

### <a name="ck"></a>CK

Chidamber, S. R. & Kemerer, C. F. (1994). Une suite de mesures pour la conception orientée objet (transactions IEEE sur l’ingénierie logicielle, vol. 20, non. 6). Extrait le 14 mai, 2011, à partir du site Web de l’Université du Pittsburgh : [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="krishnan"></a>Krishnan

Subramanyam, R. & Krishnan, M. S. (2003). Analyse empirique de CK métriques pour la complexité de la conception de Object-Oriented : implications pour les défauts logiciels (transactions IEEE sur l’ingénierie logicielle, vol. 29, non. 4). Extrait le 14 mai, 2011, obtenu à l’origine à partir du site Web de l’Université du Massachusetts Dartmouth [https://ieeexplore.ieee.org/abstract/document/1191795](https://ieeexplore.ieee.org/abstract/document/1191795)

### <a name="shatnawi"></a>Shatnawi

Shatnawi, R. (2010). Une investigation quantitative des niveaux de risque acceptables de Object-Oriented métriques dans les systèmes de Open-Source (transactions IEEE sur l’ingénierie logicielle, vol. 36, non. 2).
---
title: Métriques du code-complexité cyclomatic
ms.date: 5/7/2021
description: En savoir plus sur la métrique de complexité cyclomatic pour les métriques du code dans Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1798b0faa1b0cf44ae490f5b27571e5466b82ca9
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2021
ms.locfileid: "109682656"
---
# <a name="code-metrics---cyclomatic-complexity"></a>Métriques du code-complexité cyclomatic

Lorsque vous utilisez des métriques de code, l’un des éléments les moins compriss semble être une complexité cyclomatic. Fondamentalement, avec la complexité cyclomatic, les nombres plus élevés sont mauvais et les nombres inférieurs sont corrects. Vous pouvez utiliser la complexité cyclomatic pour avoir une idée de la manière dont un code donné peut être testé, maintenu ou dépanner, ainsi que d’une indication de la probabilité que le code produise des erreurs. À un niveau élevé, nous déterminons la valeur de la complexité cyclomatic en comptant le nombre de décisions prises dans votre code source. Dans cet article, vous commencez avec un exemple simple de complexité cyclomatic pour comprendre le concept rapidement, puis consultez des informations supplémentaires sur l’utilisation réelle et les limites suggérées. Enfin, il existe une section de citations qui peut être utilisée pour approfondir ce sujet.

## <a name="example"></a>Exemple

La complexité cyclomatic est définie comme la mesure « la quantité de logique de décision dans une fonction de code source » [NIST235](#nist235). En fait, plus vous avez de décisions à faire dans le code, plus elle est complexe.

Voyons-le en action. Créez une application console et calculez immédiatement vos métriques de code en accédant à **analyser > calculer les métriques du code pour la solution**.

![Exemple de complexité cyclomatic 1](media/cyclomatic-complexity-example-1.png)

Notez que la complexité cyclomatic est à 2 (la valeur la plus faible possible). Si vous ajoutez du code sans décision, Notez que la complexité ne change pas :

![Exemple de complexité cyclomatic 2](media/cyclomatic-complexity-example-2.png)

Si vous ajoutez une décision, la valeur de complexité cyclomatic passe de 1 :

![Exemple de complexité cyclomatic 3](media/cyclomatic-complexity-example-3.png)

Lorsque vous modifiez l’instruction if en une instruction switch avec 4 décisions à prendre, elle passe de la version d’origine de 2 à 6 :

![Exemple de complexité cyclomatic 4](media/cyclomatic-complexity-example-4.png)

Jetons un coup d’œil à une base de code (hypothétique) plus grande.

![Exemple de complexité cyclomatic 5](media/cyclomatic-complexity-example-5.png)

Notez que la plupart des éléments, au fur et à mesure que vous descendez dans la classe Products_Related, ont une valeur de 1, mais quelques-uns ont une complexité de 5. Ce n’est peut-être pas un grand problème, mais étant donné que la plupart des autres membres ont un 1 dans la même classe, vous devez absolument vous rapprocher de ces deux éléments et voir ce qu’ils contiennent. Pour ce faire, cliquez avec le bouton droit sur l’élément et choisissez **atteindre le code source** dans le menu contextuel. Examinez de plus près `Product.set(Product)` :

![Exemple de complexité cyclomatic 6](media/cyclomatic-complexity-example-6.png)

Compte tenu de toutes les instructions If, vous pouvez voir pourquoi la complexité cyclomatic est à 5. À ce stade, vous pouvez décider qu’il s’agit d’un niveau de complexité acceptable, ou vous pouvez Refactoriser pour réduire la complexité.

## <a name="the-magic-number"></a>Nombre magique

Comme avec de nombreuses mesures dans ce secteur, il n’existe pas de limite de complexité cyclomatic exacte adaptée à toutes les organisations. Toutefois, [NIST235](#nist235) indique qu’une limite de 10 est un bon point de départ :

«Le nombre précis à utiliser comme limite, cependant, reste un peu controversé. La limite d’origine de 10 comme proposé par McCabe a des preuves significatives, mais les limites maximales de 15 ont également été utilisées avec succès. Les limites supérieures à 10 doivent être réservées aux projets qui présentent plusieurs avantages opérationnels par rapport aux projets classiques, par exemple un personnel expérimenté, une conception formelle, un langage de programmation moderne, une programmation structurée, des procédures pas à pas de code et un plan de test complet. En d’autres termes, une organisation peut choisir une limite de complexité supérieure à 10, mais uniquement si elle est sûr qu’elle connaît ce qu’elle fait et qu’elle est prête à consacrer l’effort de test supplémentaire requis par les modules plus complexes. [NIST235](#nist235)

## <a name="cyclomatic-complexity-and-line-numbers"></a>Complexité et numéros de ligne cyclomatic

Le seul examen du nombre de lignes de code par lui-même est, au mieux, un prédiction très large de la qualité du code. Il existe une certaine vérité à l’idée que plus il y a de lignes de code dans une fonction, plus il est probable qu’il y ait des erreurs. Toutefois, lorsque vous associez la complexité cyclomatic à des lignes de code, vous disposez d’une image plus claire des erreurs potentielles.

Comme décrit dans Software Assurance Technology Center (SATC) à la NASA :

«Le SATC a trouvé que l’évaluation la plus efficace est une combinaison de la taille et de la complexité (cyclomatic). Les modules avec une complexité élevée et une grande taille ont tendance à avoir la fiabilité la plus faible. Les modules avec une faible taille et une complexité élevée sont également un risque de fiabilité, car ils ont tendance à être très succincts, ce qui est difficile à modifier ou à modifier.» [SATC](#satc)

## <a name="code-analysis"></a>Analyse du code

L’analyse du code comprend une catégorie de règles de maintenabilité. Pour plus d’informations, consultez [règles de maintenabilité](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). Lors de l’utilisation de l’analyse du code hérité, l’ensemble de règles de l’instruction de conception étendue contient une zone de maintenabilité :

![Règles de conception de complexité cyclomatic, ensembles de règles](media/cyclomatic-complexity-design-guidelines.png)

L’intérieur de la zone de maintenabilité est une règle de complexité :

![Règle de maintenabilité de complexité cyclomatic](media/cyclomatic-complexity-maintainability-rule.png)

Cette règle émet un avertissement lorsque la complexité cyclomatic atteint 25, ce qui permet d’éviter une complexité excessive. Pour en savoir plus sur la règle, consultez [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)

## <a name="putting-it-all-together"></a>Ensemble

Le résultat est qu’un nombre de complexité élevé signifie une plus grande probabilité d’erreurs avec un temps d’attente accru pour la maintenance et le dépannage. Examinez de plus près les fonctions qui ont une complexité élevée et déterminez si elles doivent être refactorées pour les rendre moins complexes.

## <a name="citations"></a>Citations

### <a name="mccabe5"></a>MCCABE5

McCabe, T. et A. Watson (1994), complexité logicielle (diaphonie : The Journal of Defense Software Engineering).

### <a name="nist235"></a>NIST235

Watson, A. H., & McCabe, T. J. (1996). Tests structurés : méthodologie de test utilisant la mesure de complexité cyclomatic (publication spéciale du NIST 500-235). Récupéré le 14 mai, 2011, à partir du site Web du logiciel McCabe : [http://www.mccabe.com/pdf/mccabe-nist235r.pdf](http://www.mccabe.com/pdf/mccabe-nist235r.pdf)

### <a name="satc"></a>SATC

Rosenberg, L., marteau, T., Shaw, J. (1998). Métriques et fiabilité logicielles (procédures du Congrès international IEEE sur la fiabilité des logiciels). Extrait le 14 mai 2011, du site Web de l’Université d’état de Penn : [http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf)
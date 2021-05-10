---
title: Métriques du code-couplage de classe
ms.date: 1/8/2021
description: En savoir plus sur la mesure de couplage de classe pour les métriques du code dans Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0853b807d3287eb584e76d9640ac98f930edb1a7
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2021
ms.locfileid: "109666807"
---
# <a name="code-metrics---class-coupling"></a>Métriques du code-couplage de classe

Le couplage de classe passe également par le couplage de nom entre les objets (CBO) comme défini initialement par [CK94](#ck94). Fondamentalement, le couplage de classe est une mesure du nombre de classes utilisées par une classe unique. Un nombre élevé est incorrect et un nombre faible est généralement correct avec cette mesure. Le couplage de classe s’est révélé être un prédiction précis de défaillance logicielle et les études récentes ont montré qu’une valeur de limite supérieure de 9 est la [s2010](#s2010)la plus efficace.

Conformément à la documentation Microsoft, le couplage de classe «mesure le couplage à des classes uniques via des paramètres, des variables locales, des types de retour, des appels de méthode, des instanciations génériques ou de modèle, des classes de base, des implémentations d’interface, des champs définis sur des types externes et une décoration d’attribut. Une bonne conception logicielle impose que les types et les méthodes aient une cohésion élevée et un faible couplage. Le couplage élevé indique une conception qui est difficile à réutiliser et à gérer en raison de ses nombreuses interdépendances vis-à-vis d’autres types.»

Les concepts de couplage et de cohésion sont clairement liés. Pour conserver cette discussion, nous n’allons pas vous préoccuper de la cohésion autre que pour obtenir une brève définition de [KKLS2000](#kkls2000):

«La cohésion de module a été introduite par Yourdon et Constantine comme «la manière dont la liaison étroite ou la relation entre les éléments internes d’un module est l’autre [YC79](#yc79). Un module a une cohésion forte s’il représente exactement une tâche [...] et que tous ses éléments contribuent à cette tâche unique. Ils décrivent la cohésion comme un attribut de conception, plutôt que du code, et un attribut qui peut être utilisé pour prédire la réutilisabilité, la maintenabilité et la capacité de modification.»

## <a name="class-coupling-example"></a>Exemple de couplage de classes

Examinons le couplage de classe en action. Tout d’abord, créez une application console et créez une nouvelle classe appelée person avec certaines propriétés, puis calculez immédiatement les métriques du code :

![Exemple de couplage de classes 1](media/class-coupling-example-1.png)

Notez que le couplage de classe est 0, car cette classe n’utilise pas d’autres classes. Créez maintenant une autre classe appelée PersonStuff avec une méthode qui crée une instance Person et définit les valeurs de propriété. Calculez à nouveau les métriques du code :

![Exemple de couplage de classes 2](media/class-coupling-example-2.png)

Voyez comment la valeur de couplage de classe va-t-elle ? Notez également que, quel que soit le nombre de propriétés que vous définissez, la valeur de couplage de classe s’affiche simplement de 1 et non d’une autre valeur. Le couplage de classe ne mesure chaque classe qu’une seule fois pour cette mesure, quelle que soit la quantité utilisée. En outre, pouvez-vous voir que `DoSomething()` a un 1 mais le constructeur, `PersonStuff()` , a 0 comme valeur ? Il n’existe actuellement aucun code dans le constructeur qui utilise une autre classe.

Que se passe-t-il si vous placez du code dans le constructeur qui utilisait une autre classe ? Voici ce que vous pouvez faire :

![Exemple de couplage de classes 3](media/class-coupling-example-3.png)

Désormais, le constructeur a clairement du code qui utilise une autre classe et la mesure de couplage de classe illustre ce fait. Là encore, vous pouvez voir que le couplage de classe global pour `PersonStuff()` est 1 et qu’il `DoSomething()` est également 1 pour montrer qu’une seule classe externe est utilisée, quel que soit le code interne qui l’utilise.

Ensuite, créez une autre nouvelle classe. Donnez un nom à cette classe et créez des propriétés à l’intérieur de celle-ci :

![Exemple de couplage de classes-ajouter une nouvelle classe](media/class-coupling-example-add-new-class.png)

À présent, consommez la classe dans notre `DoSomething()` méthode au sein de la `PersonStuff` classe et calculez à nouveau la métrique du code :

![Exemple de couplage de classes 4](media/class-coupling-example-4.png)

Comme vous pouvez le voir, le couplage de classe pour la classe PersonStuff va jusqu’à 2 et, si vous explorez la classe, vous pouvez voir que la `DoSomething()` méthode a le plus de couplage, mais le constructeur ne consomme toujours que 1 classe.  À l’aide de ces métriques, vous pouvez voir le nombre maximal total d’une classe donnée et examiner en détail les détails d’une base par membre.

## <a name="the-magic-number"></a>Nombre magique

Comme pour la complexité cyclomatic, aucune limite n’est adaptée à toutes les organisations. Toutefois, [s2010](#s2010) indique qu’une limite de 9 est optimale :

«Par conséquent, nous considérons les valeurs de seuil [...] comme le plus efficace. Ces valeurs de seuil (pour un membre unique) sont CBO = 9 [...]. (accentuation ajoutée)

## <a name="code-analysis"></a>Analyse du code

L’analyse du code comprend une catégorie de règles de maintenabilité. Pour plus d’informations, consultez [règles de maintenabilité](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). Lors de l’utilisation de l’analyse du code hérité, l’ensemble de règles de l’instruction de conception étendue contient une zone de maintenabilité :

![Règles de conception étendue de couplage de classe](media/class-coupling-extended-design-guideline-rules.png)

L’intérieur de la zone de maintenabilité est une règle de couplage de classe :

![Règle de couplage de classe](media/class-coupling-maintainability-area-rules.png)

Cette règle émet un avertissement lorsque le couplage de classe est excessif. Pour plus d’informations, consultez [CA1506 : éviter un couplage de classe excessif](/dotnet/fundamentals/code-analysis/quality-rules/ca1506).

## <a name="citations"></a>Citations

### <a name="ck94"></a>CK94

Chidamber, S. R. & Kemerer, C. F. (1994). Une suite de mesures pour la conception orientée objet (transactions IEEE sur l’ingénierie logicielle, vol. 20, non. 6). Extrait le 14 mai, 2011, à partir du site Web de l’Université du Pittsburgh : [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>KKLS2000

Kabaili, H., Keller, R., LUSTMAN, F. et Saint-Denis, G. (2000). Revisitement de la cohésion de classes : étude empirique sur les systèmes industriels (procédures de l’atelier sur les approches quantitatives de Object-Oriented ingénierie logicielle). Récupéré le 20 mai, 2011, à partir du site Web Université de Montréal [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Subramanyam, R. & Krishnan, M. S. (2003). Analyse empirique de CK métriques pour la complexité de la conception de Object-Oriented : implications pour les défauts logiciels (transactions IEEE sur l’ingénierie logicielle, vol. 29, non. 4). Extrait le 14 mai, 2011, du site Web de l’Université du Massachusetts Dartmouth [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi, R. (2010). Une investigation quantitative des niveaux de risque acceptables de Object-Oriented métriques dans les systèmes de Open-Source (transactions IEEE sur l’ingénierie logicielle, vol. 36, non. 2).

### <a name="yc79"></a>YC79

Edward Yourdon et Larry L. Constantine. Conception structurée. Prentice Hall, Englewood Falaises, N.J., 1979.
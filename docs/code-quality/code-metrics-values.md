---
title: Calculer la métrique du code
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b1a9d109b833d17783beb39c5f34cf6b9ed3274
ms.sourcegitcommit: 60315ba949aca1ff06fe431dbcbcfb0fedc1e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85292891"
---
# <a name="code-metrics-values"></a>Valeurs de la métrique du code

L’augmentation de la complexité des applications logicielles modernes augmente également la difficulté de rendre le code fiable et facile à gérer. La métrique du code est un jeu de mesures de logiciel qui fournit aux développeurs plus de détails sur le code qu'ils développent. En tirant parti des métriques du code, les développeurs peuvent comprendre quels types et/ou méthodes doivent être retravaillés ou être testés de manière plus approfondie. Les équipes de développement peuvent identifier les risques potentiels, comprendre l’état actuel d’un projet et suivre la progression pendant le développement de logiciels.

Les développeurs peuvent utiliser Visual Studio pour générer des données de métriques du code qui mesurent la complexité et la facilité de gestion de leur code managé. Les données de métriques du code peuvent être générées pour une solution entière ou un projet unique.

Pour plus d’informations sur la façon de générer des données de métriques du code dans Visual Studio, consultez [Comment : générer des données de métriques du code](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Mesures des logiciels

La liste suivante affiche les résultats de la métrique du code que Visual Studio calcule :

- **Index de maintenabilité** : calcule une valeur d’index comprise entre 0 et 100 qui représente la simplicité relative de la gestion du code. Une valeur élevée signifie une meilleure maintenabilité. Les évaluations codées en couleurs peuvent être utilisées pour identifier rapidement les zones problématiques dans votre code. Une évaluation verte est comprise entre 20 et 100 et indique que le code a une bonne maintenabilité. Une évaluation jaune est comprise entre 10 et 19 et indique que le code peut être géré de façon modérée. Une évaluation rouge est une évaluation comprise entre 0 et 9 et indique une maintenabilité faible. Pour plus d’informations, consultez la [plage d’index de maintenabilité et la signification](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/) du billet de blog.

- **Complexité cyclomatic** : mesure la complexité structurelle du code. Elle est créée en calculant le nombre de chemins de code différents dans le déroulement du programme. Un programme avec un workflow de contrôle complexe nécessite davantage de tests pour obtenir une bonne couverture du code et est moins gérable. Pour plus d’informations, consultez l' [entrée Wikipédia pour la complexité cyclomatic](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Profondeur d’héritage** : indique le nombre de classes différentes qui héritent les unes des autres, jusqu’à la classe de base. La profondeur d’héritage est semblable au couplage de classe dans la mesure où une modification dans une classe de base peut affecter n’importe laquelle de ses classes héritées. Plus cette valeur est élevée, plus l’héritage est profond et plus le risque de modification de la classe de base est élevé, plus il s’agit d’une modification avec rupture. Pour la profondeur d’héritage, une valeur faible est bonne et une valeur élevée est incorrecte.

- **Couplage de classe** : mesure le couplage à des classes uniques via des paramètres, des variables locales, des types de retour, des appels de méthode, des instanciations génériques ou de modèle, des classes de base, des implémentations d’interface, des champs définis sur des types externes et une décoration d’attribut. Une bonne conception logicielle impose que les types et les méthodes aient une cohésion élevée et un faible couplage. Le couplage élevé indique une conception qui est difficile à réutiliser et à gérer en raison de ses nombreuses interdépendances sur d’autres types. Pour plus d’informations, consultez le billet de blog sur la [classe couplage](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/) .

::: moniker range=">=vs-2019"

- **Lignes de code source** -indique le nombre exact de lignes de code source présentes dans votre fichier source, y compris les lignes vides. Cette mesure est disponible à partir de Visual Studio 2019 version 16,4 et Microsoft. CodeAnalysis. Metrics (2.9.5).

- **Lignes de code exécutable** -indique le nombre approximatif de lignes de code ou d’opérations exécutables. Il s’agit du nombre d’opérations dans le code exécutable. Cette mesure est disponible à partir de Visual Studio 2019 version 16,4 et Microsoft. CodeAnalysis. Metrics (2.9.5). La valeur est généralement une correspondance proche de la métrique précédente, **lignes de code**, qui est la métrique basée sur les instructions MSIL utilisée en mode hérité.
::: moniker-end
::: moniker range="vs-2017"

- **Lignes de code** : indique le nombre approximatif de lignes dans le code. Le nombre est basé sur le code IL et n’est donc pas le nombre exact de lignes dans le fichier de code source. Un nombre élevé peut indiquer qu’un type ou une méthode tente de faire trop de travail et doit être fractionné. Il peut également indiquer que le type ou la méthode peut être difficile à gérer.

   > [!NOTE]
   > La [version de ligne de commande](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) de l’outil de métrique du code compte les lignes de code réelles, car il analyse le code source au lieu de il.
::: moniker-end

## <a name="anonymous-methods"></a>Méthodes anonymes

Une *méthode anonyme* est simplement une méthode qui n’a pas de nom. Les méthodes anonymes sont le plus souvent utilisées pour passer un bloc de code en tant que paramètre de délégué. Les résultats de la métrique du code pour une méthode anonyme déclarée dans un membre, tel qu’une méthode ou un accesseur, sont associés au membre qui déclare la méthode. Ils ne sont pas associés au membre qui appelle la méthode.

## <a name="generated-code"></a>Code généré

Certains outils et compilateurs logiciels génèrent du code qui est ajouté à un projet et qui ne sont pas visibles ou ne doivent pas être modifiés par le développeur du projet. En majorité, les métriques du code ignorent le code généré lorsqu’il calcule les valeurs de métriques. Cela permet aux valeurs de métriques de refléter ce que le développeur peut voir et modifier.

Le code généré pour Windows Forms n’est pas ignoré, car il s’agit d’un code que le développeur peut voir et modifier.

## <a name="next-steps"></a>Étapes suivantes

- [Comment : générer des données de métriques du code](../code-quality/how-to-generate-code-metrics-data.md)
- [Utiliser la fenêtre résultats de la métrique du code](../code-quality/working-with-code-metrics-data.md)

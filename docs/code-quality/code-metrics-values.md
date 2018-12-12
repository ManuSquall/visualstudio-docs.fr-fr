---
title: Calculer la métrique du code
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b56db0d54e198e0d6d25b19db528ac979a3d44b4
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056770"
---
# <a name="code-metrics-values"></a>Valeurs de métriques de code

La complexité accrue d’applications modernes augmente également la difficulté de rendre le code fiable et facile à gérer. La métrique du code est un jeu de mesures de logiciel qui fournit aux développeurs plus de détails sur le code qu'ils développent. En tirant parti de la métrique du code, les développeurs peuvent comprendre quels types et/ou les méthodes à retravailler ou à tester de manière plus approfondie. Les équipes de développement peuvent identifier les risques potentiels, comprendre l’état actuel d’un projet et suivre la progression pendant le développement de logiciels.

Les développeurs peuvent utiliser Visual Studio pour générer des données de métrique du code qui mesurent la complexité et la facilité de maintenance de leur code managé. Données de métrique du code peuvent être générées pour une solution entière ou un projet unique.

Pour plus d’informations sur la façon de générer des données de métrique du code dans Visual Studio, consultez [Comment : générer des données de métrique du code](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Dimensions du logiciel

La liste suivante présente le code des résultats de la métrique qui calcule de Visual Studio :

- **Indice de maintenabilité** -calcule une valeur d’index compris entre 0 et 100 qui représente la relative simplicité de gestion du code. Une valeur élevée signifie une meilleure maintenabilité. Des évaluations codées par couleur peuvent servir à identifier rapidement les zones à problème dans votre code. Une meilleure évaluation est compris entre 20 et 100 et indique que le code a bonne maintenabilité. Une évaluation jaune est comprise entre 10 et 19 et indique que le code est relativement facile à gérer. Une évaluation rouge est une évaluation comprise entre 0 et 9 et indique une maintenabilité faible.

- **Complexité cyclomatique** -mesure la complexité structurelle du code. Il est créé en calculant le nombre de chemins de code différents dans le flux du programme. Un programme qui a le flux de contrôle complexe nécessitera plus de tests pour obtenir la couverture du code qui fonctionne bien et sera moins facile à gérer.

- **Profondeur d’héritage** -indique le nombre de définitions de classe qui s’étendent à la racine de la hiérarchie de classes. Plus la hiérarchie est plus difficile qu’il peut être de comprendre où des méthodes et les champs sont définis ou / et redéfini.

- **COUPLAGE de classe** -mesure le couplage avec des classes uniques via des paramètres, variables locales, types de retour, les appels de méthode, des instanciations génériques ou de modèle, classes de base, les implémentations d’interface, champs définis sur les types externes, et décoration de l’attribut. Une bonne conception logicielle détermine les types et méthodes doivent avoir une forte cohésion et un couplage bas. COUPLAGE élevé indique une conception qui est difficile à réutiliser et tenir à jour en raison de ses nombreuses interdépendances sur d’autres types.

- **Lignes de Code** -indique le nombre approximatif de lignes dans le code. Le nombre est basé sur le code de langage intermédiaire et est donc pas le nombre exact de lignes dans le fichier de code source. Un nombre très élevé peut indiquer qu’un type ou méthode essaie d’en faire trop de travail et doit être fractionnée. Cela peut également indiquer que le type ou la méthode peut être difficile à maintenir.

   > [!NOTE]
   > Le [version de ligne de commande](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) du code outil métrique nombre réel de lignes de code, car il analyse le code source au lieu de langage intermédiaire.

## <a name="anonymous-methods"></a>Méthodes anonymes

Un *méthode anonyme* est simplement une méthode qui n’a aucun nom. Méthodes anonymes sont fréquemment utilisés pour passer un bloc de code comme un paramètre de délégué. Résultats de la métrique pour une méthode anonyme qui est déclaré dans un membre, tel qu’une méthode ou un accesseur, sont associés au membre qui déclare la méthode. Ils ne sont pas associés au membre qui appelle la méthode.

Pour plus d’informations sur la manière dont la métrique du Code traite les méthodes anonymes, consultez [méthodes anonymes et analyse du Code](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Code généré

Certains outils logiciels et les compilateurs génèrent le code qui est ajouté à un projet et dont le développeur ne voit pas ou ne doit pas modifier. Essentiellement, la métrique du Code ignore le code généré lorsqu’il calcule les valeurs de mesures. Ainsi, les valeurs de mesures afin de refléter ce que le développeur peut voir ou modifier.

Code généré pour les Windows Forms n’est pas ignoré, car il s’agit de code que le développeur peut voir et modifier.

## <a name="next-steps"></a>Étapes suivantes

- [Comment : générer des données de métrique du code](../code-quality/how-to-generate-code-metrics-data.md)
- [Utiliser la fenêtre Résultats des métriques de Code](../code-quality/working-with-code-metrics-data.md)
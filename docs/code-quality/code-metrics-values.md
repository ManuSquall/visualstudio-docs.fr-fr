---
title: Calculer la métrique du code dans Visual Studio
ms.date: 12/12/2017
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
ms.openlocfilehash: f3d0bf9b0bf689be847e7f16f2ee01db6e3df6d7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="code-metrics-values"></a>Valeurs de métrique de code

La complexité accrue d’applications modernes augmente également la difficulté de rendre le code fiable et facile à gérer. La métrique du code est un jeu de mesures de logiciel qui fournit aux développeurs plus de détails sur le code qu'ils développent. En tirant parti de la métrique du code, les développeurs peuvent comprendre quels types et/ou méthodes doivent être retravaillées ou plus approfondis. Les équipes de développement peuvent identifier les risques potentiels, comprendre l’état actuel d’un projet et suivre la progression pendant le développement de logiciels.

Les développeurs peuvent utiliser Visual Studio pour générer des données de métrique du code qui mesurent la complexité et la facilité de maintenance de leur code managé. Données de métrique du code peuvent être générées pour une solution entière ou un seul projet.

Pour plus d’informations sur la façon de générer des données de métrique du code dans Visual Studio, consultez [Comment : générer des données de métrique du code](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Dimensions du logiciel

La liste suivante montre le code des résultats de la métrique qui calcule de Visual Studio :

- **Indice de maintenabilité** -calcule une valeur d’index compris entre 0 et 100 qui représente la relative simplicité de gestion du code. Une valeur élevée signifie une meilleure facilité de maintenance. Contrôle d’accès codés en couleurs peut servir à identifier rapidement les zones à problème dans votre code. Une évaluation verte est compris entre 20 et 100 et indique que le code a bonne maintenabilité. Une évaluation jaune est comprise entre 10 et 19 et indique que le code est relativement facile à gérer. Une évaluation rouge est une évaluation comprise entre 0 et 9 et indique une maintenabilité basse.

- **La complexité cyclomatique** -mesure la complexité structurelle du code. Il est créé en calculant le nombre de chemins de code différents dans le flux du programme. Un programme qui a des flux de contrôle complexe nécessitera plus de tests pour obtenir la bonne couverture du code et sera moins facile à gérer.

- **Profondeur d’héritage** -indique le nombre de définitions de classe qui s’étendent à la racine de la hiérarchie de classes. Plus la hiérarchie est plus difficile d’avoir comprendre où des méthodes et champs sont définis ou / et redéfini.

- **COUPLAGE de classe** -mesure le couplage avec des classes uniques via des paramètres, variables locales, types de retour, les appels de méthode, des instanciations génériques ou de modèle, des classes de base, des implémentations d’interface, champs définis sur les types externes, et décoration d’attribut. Une bonne conception logicielle détermine les types et les méthodes doivent avoir cohésion haute et faible couplage. Un couplage élevé indique une conception difficile à réutiliser et mettre à jour en raison de ses nombreuses interdépendances sur d’autres types.

- **Lignes de Code** -indique le nombre approximatif de lignes dans le code. Le nombre est basé sur le code IL et n’est donc pas le nombre exact de lignes dans le fichier de code source. Un nombre très élevé peut indiquer qu’un type ou une méthode essaie de faire trop de travail et doit être fractionné. Il peut également indiquer que le type ou la méthode peut être difficile à maintenir.

## <a name="anonymous-methods"></a>Méthodes anonymes

Un *méthode anonyme* est simplement une méthode sans nom. Méthodes anonymes sont fréquemment utilisés pour passer un bloc de code comme un paramètre de délégué. Résultats de la métrique d’une méthode anonyme qui est déclarée dans un membre, tel qu’une méthode ou un accesseur, sont associés au membre qui déclare la méthode. Ils ne sont pas associées au membre qui appelle la méthode.

Pour plus d’informations sur la façon dont la métrique du Code traite les méthodes anonymes, consultez [méthodes anonymes et analyse du Code](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Code généré

Certains outils logiciels et les compilateurs de génèrent du code qui est ajouté à un projet et que le développeur ne voit pas ou ne doit pas modifier. Principalement, la métrique du Code ignore le code généré lorsqu’il calcule les valeurs de mesures. Ainsi, les valeurs de métriques refléter ce que le développeur peut voir et modifier.

Code généré pour les Windows Forms n’est pas ignoré, car il s’agit de code que le développeur peut voir et modifier.

## <a name="next-steps"></a>Étapes suivantes

- [Comment : générer des données de métrique du code](../code-quality/how-to-generate-code-metrics-data.md)
- [Utilisez la fenêtre Résultats des métriques de Code](../code-quality/working-with-code-metrics-data.md)
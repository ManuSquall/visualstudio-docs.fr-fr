---
title: Datasets typés et non typés
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d817938a7611d7390e400cfbf69c6836b9256f3b
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117223"
---
# <a name="typed-vs-untyped-datasets"></a>Datasets typés et non typés
Un dataset typé est un jeu de données est tout d’abord dérivé de la base de <xref:System.Data.DataSet> classe et utilise ensuite les informations à partir de la **Concepteur de Dataset**, qui est stocké dans un fichier .xsd, pour générer un nouveau fortement typée de classe de jeu de données. Informations à partir du schéma (tables, colonnes et ainsi de suite) sont générées et compilées dans cette nouvelle classe de jeu de données comme un ensemble de propriétés et des objets de première classe. Parce qu’un dataset typé hérite de la base de <xref:System.Data.DataSet> (classe), la classe typée suppose que toutes les fonctionnalités de la <xref:System.Data.DataSet> classe et peut être utilisé avec les méthodes qui prennent une instance d’un <xref:System.Data.DataSet> classe en tant que paramètre.

 Un dataset non typé, n’a en revanche, aucun schéma intégré correspondant. Comme dans un dataset typé, il contient des tables, colonnes et ainsi de suite, mais ceux-ci sont exposés uniquement en tant que collections. (Toutefois, une fois que vous créez manuellement les tables et autres éléments de données dans un dataset non typé, vous pouvez exporter la structure du dataset en tant que schéma à l’aide du jeu de données <xref:System.Data.DataSet.WriteXmlSchema%2A> méthode.)

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>Accès aux données de contraste dans les datasets typés et non typés
 La classe d’un dataset typé possède un modèle d’objet dans lequel ses propriétés prennent les noms réels des tables et des colonnes. Par exemple, si vous travaillez avec un dataset typé, vous pouvez référencer une colonne à l’aide de code semblable au suivant :

 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

 En revanche, si vous travaillez avec un dataset non typé, le code équivalent est :

 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

 Accès typé est non seulement plus facile à lire, mais également entièrement pris en charge par IntelliSense dans Visual Studio **éditeur de Code**. En plus d’être plus facile à manipuler, la syntaxe pour le dataset typé fournit la vérification de type au moment de la compilation, en réduisant considérablement le risque d’erreurs en assignant des valeurs aux membres du jeu de données. Si vous modifiez le nom d’une colonne dans votre <xref:System.Data.DataSet> class et puis compilez votre application, vous recevez une erreur de build. En double-cliquant sur l’erreur de build dans le **liste des tâches**, vous pouvez accéder directement à l’ou les lignes de code qui font référence à l’ancien nom de colonne. Accès aux tables et colonnes dans un jeu de données est également légèrement plus rapide lors de l’exécution, car l’accès est déterminé au moment de la compilation, pas par le biais de regroupements lors de l’exécution.

 Même si les datasets typés présentent de nombreux avantages, un dataset non typé est utile dans diverses circonstances. La situation la plus évidente est lorsque aucun schéma n’est disponible pour le jeu de données. Cela peut se produire, par exemple, si votre application interagit avec un composant qui retourne un jeu de données, mais vous ne savez pas à l’avance la structure. De même, voici les heures lorsque vous travaillez avec des données qui n’ont pas d’une structure statique et prévisible. Dans ce cas, il est peu pratique d’utiliser un dataset typé, car vous seriez obligé de régénérer la classe dataset typée pour chaque modification de la structure de données.

 En règle générale, il existe plusieurs fois lorsque vous pouvez créer un jeu de données de manière dynamique sans disposer d’un schéma. Dans ce cas, le jeu de données est simplement une structure pratique dans laquelle vous pouvez conserver des informations, tant que les données peuvent être représentées de manière relationnelle. En même temps, vous pouvez tirer parti des fonctionnalités du jeu de données, telles que la possibilité de sérialiser les informations à passer à un autre processus ou d’écrire un fichier XML.

## <a name="see-also"></a>Voir aussi

- [Outils de jeu de données](../data-tools/dataset-tools-in-visual-studio.md)
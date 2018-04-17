---
title: Typées et les datasets non typés | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7c55b160012997281cd5e7551ea07178b63f0fca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="typed-vs-untyped-datasets"></a>Typées et les datasets non typés
Un dataset typé est un jeu de données qui est tout d’abord dérivé de la base de <xref:System.Data.DataSet> de classe, puis utilise les informations à partir de la **Concepteur de Dataset**, qui est stockée dans un fichier .xsd, pour générer un nouveau fortement typée dataset (classe). Pour plus d’informations à partir du schéma (tables, colonnes et ainsi de suite) sont générés et compilés dans ce nouveau type de jeu de données comme un ensemble de propriétés et des objets de première classe. Car un dataset typé hérite de la base de <xref:System.Data.DataSet> (classe), la classe typée reprend toutes les fonctionnalités de la <xref:System.Data.DataSet> classe et peut être utilisé avec des méthodes qui prennent une instance d’un <xref:System.Data.DataSet> classe en tant que paramètre.  
  
 Un dataset non typé, n’a, en revanche, aucun schéma intégré équivalent. Comme dans un dataset typé, il contient des tables, colonnes et ainsi de suite, mais ceux-ci sont exposés comme des collections. (Toutefois, après avoir créé manuellement les tables et autres éléments de données dans un dataset non typé, vous pouvez exporter la structure du dataset en tant que schéma à l’aide du jeu de données <xref:System.Data.DataSet.WriteXmlSchema%2A> méthode.)  
  
## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>Accès aux données dans les datasets typés et non de contraste  
 La classe d’un dataset typé possède un modèle d’objet dans lequel ses propriétés prennent les noms réels des tables et des colonnes. Par exemple, si vous travaillez avec un dataset typé, vous pouvez référencer une colonne à l’aide de code semblable au suivant :  
  
 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]  
  
 En revanche, si vous travaillez avec un dataset non typé, le code équivalent est :  
  
 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]  
  
 Accès typé est non seulement plus facile à lire, mais il est également entièrement pris en charge par IntelliSense dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **éditeur de Code**. En plus d’être plus facile à manipuler, la syntaxe pour le dataset typé fournit une vérification de type au moment de la compilation, ce qui réduit considérablement le risque d’erreurs en assignant des valeurs aux membres du jeu de données. Si vous modifiez le nom d’une colonne dans votre <xref:System.Data.DataSet> classe et puis le compiler votre application, vous recevez une erreur de build. En double-cliquant sur l’erreur de build dans le **liste des tâches**, vous pouvez accéder directement à l’ou les lignes de code qui font référence à l’ancien nom de colonne. Accès aux tables et colonnes dans un typé dataset est légèrement plus rapide lors de l’exécution, car l’accès est déterminé au moment de la compilation, pas par le biais de regroupements lors de l’exécution.  
  
 Bien que les datasets typés présentent de nombreux avantages, un dataset non typé est utile dans diverses circonstances. La situation la plus évidente est lorsque aucun schéma n’est disponible pour le jeu de données. Cela peut se produire, par exemple, si votre application interagit avec un composant qui retourne un jeu de données, mais vous ne connaissez pas à l’avance quelle est sa structure. De même, il existe des heures lorsque vous travaillez avec des données qui ne dispose pas d’une structure statique et prévisible. Dans ce cas, il est peu pratique d’utiliser un dataset typé, car vous devez régénérer la classe dataset typée pour chaque modification de la structure de données.  
  
 En règle générale, il existe plusieurs fois lorsque vous pouvez créer un jeu de données dynamique sans disposer d’un schéma. Dans ce cas, le jeu de données est simplement une structure pratique dans laquelle vous pouvez conserver les informations, tant que les données peuvent être représentées de manière relationnelle. En même temps, vous pouvez tirer parti des fonctionnalités du jeu de données, telles que la capacité à sérialiser les informations à transmettre à un autre processus ou d’écrire un fichier XML.

## <a name="see-also"></a>Voir aussi
[Outils de jeu de données](../data-tools/dataset-tools-in-visual-studio.md)
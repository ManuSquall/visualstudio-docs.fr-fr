---
title: Interroger des datasets
description: Comprendre les jeux de données de requête. En savoir plus sur le respect de la casse du jeu de données. Rechercher une ligne spécifique dans une table de données, Rechercher des lignes par valeurs de colonne et accéder aux enregistrements associés.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8ccf228b147301eb9fccf41da98f8cc5204971a9
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436066"
---
# <a name="query-datasets"></a>Interroger des datasets
Pour rechercher des enregistrements spécifiques dans un DataSet, utilisez la `FindBy` méthode sur le DataTable, écrivez votre propre instruction foreach pour effectuer une boucle sur la collection de lignes de la table ou utilisez [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>Respect de la casse du DataSet
Dans un jeu de données, les noms de table et de colonne ne respectent pas la casse par défaut, c’est-à-dire qu’une table dans un DataSet appelé « clients » peut également être appelée « clients ». Cela correspond aux conventions d’affectation de noms dans de nombreuses bases de données, y compris SQL Server. Dans SQL Server, le comportement par défaut est que les noms des éléments de données ne peuvent pas être distingués uniquement par la casse.

> [!NOTE]
> Contrairement aux jeux de données, les documents XML respectent la casse, de sorte que les noms des éléments de données définis dans les schémas respectent la casse. Par exemple, le protocole de schéma permet au schéma de définir une table appelée « Customers » (clients) et une autre table appelée « Customers » (clients). Cela peut entraîner des collisions de noms lorsqu’un schéma qui contient des éléments qui diffèrent uniquement par la casse est utilisé pour générer une classe DataSet.

Toutefois, le respect de la casse peut être un facteur déterminant la façon dont les données sont interprétées dans le jeu de données. Par exemple, si vous filtrez des données dans une table de DataSet, les critères de recherche peuvent retourner des résultats différents selon que la comparaison respecte la casse. Vous pouvez contrôler le respect de la casse pour le filtrage, la recherche et le tri en définissant la propriété du DataSet <xref:System.Data.DataSet.CaseSensitive%2A> . Toutes les tables du DataSet héritent par défaut de la valeur de cette propriété. (Vous pouvez remplacer cette propriété pour chaque table individuelle en définissant la propriété de la table <xref:System.Data.DataTable.CaseSensitive%2A> .)

## <a name="locate-a-specific-row-in-a-data-table"></a>Rechercher une ligne spécifique dans une table de données

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Pour rechercher une ligne dans un DataSet typé avec une valeur de clé primaire

- Pour localiser une ligne, appelez la méthode fortement typée `FindBy` qui utilise la clé primaire de la table.

     Dans l’exemple suivant, la `CustomerID` colonne est la clé primaire de la `Customers` table. Cela signifie que la `FindBy` méthode générée est `FindByCustomerID` . L’exemple montre comment assigner un spécifique <xref:System.Data.DataRow> à une variable à l’aide de la `FindBy` méthode générée.

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Pour rechercher une ligne dans un DataSet non typé avec une valeur de clé primaire

- Appelez la <xref:System.Data.DataRowCollection.Find%2A> méthode d’une <xref:System.Data.DataRowCollection> collection, en passant la clé primaire en tant que paramètre.

     L’exemple suivant montre comment déclarer une nouvelle ligne appelée `foundRow` et lui assigner la valeur de retour de la <xref:System.Data.DataRowCollection.Find%2A> méthode. Si la clé primaire est trouvée, le contenu de l’index de colonne 1 s’affiche dans une boîte de message.

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>Rechercher des lignes par valeurs de colonne

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Pour rechercher des lignes en fonction des valeurs d’une colonne

- Les tables de données sont créées à l’aide de la <xref:System.Data.DataTable.Select%2A> méthode, qui retourne un tableau de <xref:System.Data.DataRow> s en fonction de l’expression transmise à la <xref:System.Data.DataTable.Select%2A> méthode. Pour plus d’informations sur la création d’expressions valides, consultez la section « syntaxe des expressions » de la page sur la <xref:System.Data.DataColumn.Expression%2A> propriété.

     L’exemple suivant montre comment utiliser la <xref:System.Data.DataTable.Select%2A> méthode de <xref:System.Data.DataTable> pour rechercher des lignes spécifiques.

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>Accéder aux enregistrements associés
Lorsque les tables d’un jeu de données sont liées, un <xref:System.Data.DataRelation> objet peut rendre les enregistrements associés disponibles dans une autre table. Par exemple, un jeu de données contenant `Customers` des `Orders` tables et peut être mis à disposition.

Vous pouvez utiliser un <xref:System.Data.DataRelation> objet pour localiser des enregistrements connexes en appelant la <xref:System.Data.DataRow.GetChildRows%2A> méthode d’un <xref:System.Data.DataRow> dans la table parente. Cette méthode retourne un tableau d’enregistrements enfants connexes. Ou bien, vous pouvez appeler la <xref:System.Data.DataRow.GetParentRow%2A> méthode d’un <xref:System.Data.DataRow> dans la table enfant. Cette méthode retourne un unique <xref:System.Data.DataRow> à partir de la table parente.

Cette page fournit des exemples à l’aide de datasets typés. Pour plus d’informations sur la navigation dans les relations dans les datasets non typés, consultez [navigation](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations)dans les jeux de données.

> [!NOTE]
> Si vous travaillez dans une application Windows Forms et que vous utilisez les fonctionnalités de liaison de données pour afficher les données, le formulaire généré par le concepteur peut fournir suffisamment de fonctionnalités pour votre application. Pour plus d’informations, consultez [lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Plus précisément, consultez [relations dans les jeux de données](relationships-in-datasets.md).

Les exemples de code suivants montrent comment parcourir les relations vers le haut et vers le haut dans des datasets typés. Les exemples de code utilisent <xref:System.Data.DataRow> des méthodes typées ( `NorthwindDataSet.OrdersRow` ) et les méthodes FindBy *PrimaryKey* () générées `FindByCustomerID` pour localiser une ligne souhaitée et retourner les enregistrements associés. Les exemples se compilent et s’exécutent correctement uniquement si vous disposez des éléments suivants :

- Instance d’un dataset nommé `NorthwindDataSet` avec une `Customers` table.

- Une `Orders` table.

- Une relation nommée qui `FK_Orders_Customers` associe les deux tables.

En outre, les deux tables doivent être remplies de données pour tous les enregistrements à retourner.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Pour retourner les enregistrements enfants d’un enregistrement parent sélectionné

- Appeler la <xref:System.Data.DataRow.GetChildRows%2A> méthode d’une `Customers` ligne de données spécifique et retourner un tableau de lignes de la `Orders` table :

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Pour retourner l’enregistrement parent d’un enregistrement enfant sélectionné

- Appelez la <xref:System.Data.DataRow.GetParentRow%2A> méthode d’une `Orders` ligne de données spécifique et retournez une ligne unique à partir de la `Customers` table :

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Voir aussi

- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)

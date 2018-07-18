---
title: Jeux de données de requête
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0fb1310649a1aeba7fd46acf9277ef7ea5825472
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31926696"
---
# <a name="query-datasets"></a>Jeux de données de requête
Pour rechercher des enregistrements spécifiques dans un jeu de données, utilisez la méthode FindBy sur la table de données, écrire votre propre instruction foreach pour parcourir la collection de lignes de la table, ou utilisez [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>Respect du jeu de données
Dans un jeu de données, les noms de table et de colonne respectent la casse par défaut, autrement dit, une table dans un dataset nommé « Customers » peut également être appelée « customers ». Cela correspond aux conventions d’affectation de noms dans plusieurs bases de données, y compris SQL Server. Dans SQL Server, le comportement par défaut est que les noms des éléments de données ne peut pas être distingués uniquement par la casse.

> [!NOTE]
>  Contrairement aux jeux de données, les documents XML étant la casse, les noms d’éléments de données définis dans les schémas respectent la casse. Par exemple, le protocole de schéma permet au schéma de définir une table appelée « Customers » et une autre table appelée « customers ». Cela peut entraîner des collisions de noms lorsqu’un schéma qui contient les éléments qui diffèrent uniquement par la casse est utilisé pour générer une classe dataset.

Respect de la casse, toutefois, peut être un facteur de l’interprétation des données dans le jeu de données. Par exemple, si vous filtrez des données dans une table de dataset, les critères de recherche peuvent retourner des résultats différents selon que la comparaison respecte la casse. Vous pouvez contrôler le respect de la casse de filtrage, la recherche et le tri en définissant le jeu de données <xref:System.Data.DataSet.CaseSensitive%2A> propriété. Toutes les tables dans le jeu de données héritent de la valeur de cette propriété par défaut. (Vous pouvez substituer cette propriété pour chaque table individuelle en définissant la table <xref:System.Data.DataTable.CaseSensitive%2A> propriété.)

## <a name="locate-a-specific-row-in-a-data-table"></a>Rechercher une ligne spécifique dans une table de données

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Pour rechercher une ligne dans un dataset typé avec une valeur de clé primaire

-   Pour obtenir une ligne, appelez fortement typé `FindBy` méthode qui utilise la clé primaire de la table.

     Dans l’exemple suivant, la `CustomerID` colonne est la clé primaire de la `Customers` table. Cela signifie que le texte généré `FindBy` méthode est `FindByCustomerID`. L’exemple montre comment affecter un spécifique <xref:System.Data.DataRow> à une variable à l’aide de l’élément généré `FindBy` (méthode).

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Pour rechercher une ligne dans un dataset non typé avec une valeur de clé primaire

-   Appelez le <xref:System.Data.DataRowCollection.Find%2A> méthode d’un <xref:System.Data.DataRowCollection> collection, en passant la clé primaire en tant que paramètre.

     L’exemple suivant montre comment déclarer une nouvelle ligne appelée `foundRow` et lui attribuer la valeur de retour de la <xref:System.Data.DataRowCollection.Find%2A> (méthode). Si la clé primaire est trouvée, le contenu de l’index de colonne 1 est affiché dans une boîte de message.

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>Rechercher des lignes par valeurs de colonne

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Pour rechercher les lignes selon les valeurs des colonnes

-   Tables de données sont créées avec le <xref:System.Data.DataTable.Select%2A> (méthode), qui retourne un tableau de <xref:System.Data.DataRow>s basé sur l’expression passée à la <xref:System.Data.DataTable.Select%2A> (méthode). Pour plus d’informations sur la création d’expressions valides, consultez la section « Syntaxe d’Expression » de la page le <xref:System.Data.DataColumn.Expression%2A> propriété.

     L’exemple suivant montre comment utiliser le <xref:System.Data.DataTable.Select%2A> méthode de le <xref:System.Data.DataTable> pour rechercher des lignes spécifiques.

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>Accès des enregistrements associés.
Lorsque les tables dans un jeu de données sont liées, un <xref:System.Data.DataRelation> objet peut rendre les enregistrements connexes disponibles dans une autre table. Par exemple, un jeu de données contenant `Customers` et `Orders` tables peuvent être rendues disponibles.

Vous pouvez utiliser un <xref:System.Data.DataRelation> objet à rechercher des enregistrements connexes en appelant le <xref:System.Data.DataRow.GetChildRows%2A> méthode d’un <xref:System.Data.DataRow> dans la table parente. Cette méthode retourne un tableau d’enregistrements enfants connexes. Ou vous pouvez appeler la <xref:System.Data.DataRow.GetParentRow%2A> méthode d’un <xref:System.Data.DataRow> dans la table enfant. Cette méthode retourne un seul <xref:System.Data.DataRow> à partir de la table parente.

Cette page fournit des exemples d’utilisation de datasets typés. Pour plus d’informations sur l’exploration des relations dans les datasets non typés, consultez [navigation des DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
>  Si vous travaillez dans une application Windows Forms et que vous utilisez les fonctionnalités de liaison de données pour afficher des données, le formulaire généré par le concepteur peut fournir suffisamment de fonctionnalités pour votre application. Pour plus d’informations, consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). En particulier, consultez [des relations dans les jeux de données](relationships-in-datasets.md).

Les exemples de code suivants montrent comment parcourir les relations dans les datasets typés. L’utilisation d’exemples de code typée <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) et le FindBy généré*PrimaryKey* (`FindByCustomerID`) les méthodes pour rechercher une ligne souhaitée et retourner les enregistrements connexes. Les exemples de compiler et exécutent correctement uniquement si vous avez :

-   Une instance d’un dataset nommé `NorthwindDataSet` avec un `Customers` table.

-   Un `Orders` table.

-   Une relation nommée `FK_Orders_Customers`les deux tables.

En outre, les deux tables doivent être remplies avec les données de tous les enregistrements à retourner.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Pour retourner les enregistrements d’un enregistrement parent sélectionné enfants

-   Appelez le <xref:System.Data.DataRow.GetChildRows%2A> spécifiques à une méthode `Customers` données de lignes et de retourner un tableau de lignes à partir de la `Orders` table :

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Pour retourner l’enregistrement parent d’un enregistrement enfant sélectionné

-   Appelez le <xref:System.Data.DataRow.GetParentRow%2A> spécifiques à une méthode `Orders` ligne de données et retourner une seule ligne à partir de la `Customers` table :

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Voir aussi

- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
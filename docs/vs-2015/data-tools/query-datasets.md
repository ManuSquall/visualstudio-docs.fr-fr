---
title: Interroger des jeux de données | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2a5fd14f4cbc07fbd1ebac0eeefaa039dece188d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949443"
---
# <a name="query-datasets"></a>Interroger des datasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Pour rechercher des enregistrements spécifiques dans un jeu de données, utiliser la méthode FindBy sur la table de données, écrire votre propre boucle foreach sur la collection de lignes de la table ou [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17). LINQ to DataSet.  
  
## <a name="dataset-case-sensitivity"></a>Jeu de données respecte la casse  
 Au sein d’un jeu de données, les noms de table et de colonne respectent la casse par défaut, autrement dit, une table dans un dataset nommé « Customers » peut également être appelée « customers ». Cela met en correspondance les conventions d’affectation de noms dans plusieurs bases de données, y compris SQL serveur SQL Server, le comportement par défaut est que les noms des éléments de données ne peut pas être distingués uniquement par la casse.  
  
> [!NOTE]
>  Contrairement aux jeux de données, les documents XML sont la casse, par conséquent, les noms d’éléments de données définis dans les schémas sont respect de la casse. Par exemple, le protocole de schéma permet au schéma de définir une table appelée « Customers » et une autre table appelée « customers ». Cela peut entraîner des collisions de nom lorsqu’un schéma qui contient les éléments qui diffèrent uniquement par la casse est utilisé pour générer une classe de jeu de données.  
  
 Respecte la casse, toutefois, peut être un facteur de l’interprétation des données dans le jeu de données. Par exemple, si vous filtrez des données dans une table de dataset, les critères de recherche peuvent retourner des résultats différents selon que la comparaison respecte la casse. Vous pouvez contrôler le respect de la casse de filtrage, la recherche et le tri en définissant le jeu de données <xref:System.Data.DataSet.CaseSensitive%2A> propriété. Toutes les tables dans le jeu de données héritent de la valeur de cette propriété par défaut. (Vous pouvez remplacer cette propriété pour chaque table individuelle en définissant la table <xref:System.Data.DataTable.CaseSensitive%2A> propriété.)  
  
## <a name="locate-a-specific-row-in-a-data-table"></a>Rechercher une ligne spécifique dans une table de données  
  
#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Pour rechercher une ligne dans un dataset typé avec une valeur de clé primaire  
  
-   Pour obtenir une ligne, appelez fortement typée `FindBy` méthode qui utilise la clé primaire de la table.  
  
     Dans l’exemple suivant, le `CustomerID` colonne est la clé primaire de la `Customers` table. Cela signifie que le texte généré `FindBy` méthode est `FindByCustomerID`. L’exemple montre comment affecter un spécifique <xref:System.Data.DataRow> à une variable à l’aide de l’élément généré `FindBy` (méthode).  
  
     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]  
  
#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Pour rechercher une ligne dans un dataset non typé avec une valeur de clé primaire  
  
-   Appelez le <xref:System.Data.DataRowCollection.Find%2A> méthode d’un <xref:System.Data.DataRowCollection> collection, en passant la clé primaire en tant que paramètre.  
  
     L’exemple suivant montre comment déclarer une nouvelle ligne appelée `foundRow` et attribuez-lui la valeur de retour de la <xref:System.Data.DataRowCollection.Find%2A> (méthode). Si la clé primaire est trouvée, le contenu de l’index de colonne 1 est affiché dans une boîte de message.  
  
     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]  
  
## <a name="findrows-by-column-values"></a>FindRows par les valeurs de colonne  
  
#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Pour rechercher les lignes en fonction des valeurs dans n’importe quelle colonne  
  
-   Tables de données sont créées avec le<xref:System.Data.DataTable.Select%2A> (méthode), qui retourne un tableau de <xref:System.Data.DataRow>s basé sur l’expression passée à la <xref:System.Data.DataTable.Select%2A> (méthode). Pour plus d’informations sur la création d’expressions valides, consultez la section « Syntaxe d’Expression » de la page le <xref:System.Data.DataColumn.Expression%2A> propriété.  
  
     L’exemple suivant montre comment utiliser le <xref:System.Data.DataTable.Select%2A> méthode de la <xref:System.Data.DataTable> pour rechercher des lignes spécifiques.  
  
     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]  
  
## <a name="access-related-records"></a>Accès des enregistrements associés.  
 Lorsque les tables dans un jeu de données sont liées, un <xref:System.Data.DataRelation> objet peut proposer les enregistrements associés dans une autre table. Par exemple, un jeu de données contenant `Customers` et `Orders` tables peuvent être rendues disponibles.  
  
 Vous pouvez utiliser un <xref:System.Data.DataRelation> objet à localiser les enregistrements connexes en appelant le <xref:System.Data.DataRow.GetChildRows%2A> méthode d’un <xref:System.Data.DataRow> dans la table parente. Cette méthode retourne un tableau d’enregistrements enfants connexes. Ou vous pouvez appeler la <xref:System.Data.DataRow.GetParentRow%2A> méthode d’un <xref:System.Data.DataRow> dans la table enfant. Cette méthode retourne un seul <xref:System.Data.DataRow> à partir de la table parente.  
  
 Cette page fournit des exemples d’utilisation de datasets typés. Pour plus d’informations sur l’exploration des relations dans les datasets non typés, consultez [DataRelations accédant](http://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e).  
  
> [!NOTE]
> Si vous travaillez dans une application Windows Forms et en utilisant les fonctionnalités de liaison de données pour afficher des données, le formulaire généré par le concepteur peut fournir suffisamment de fonctionnalités pour votre application. Pour plus d’informations, consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Les exemples de code suivants montrent comment parcourir les relations dans les datasets typés. L’utilisation d’exemples de code typée <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) et le texte généré `FindBy` *PrimaryKey* (`FindByCustomerID`) méthodes permettant de rechercher une ligne souhaitée et retourner les enregistrements connexes. Les exemples de compiler et exécutent correctement uniquement si vous avez :  
  
- Une instance d’un dataset nommé `NorthwindDataSet` avec un `Customers` table.  
  
- Un `Orders` table.  
  
- Une relation nommée `FK_Orders_Customers`associant les deux tables disponibles à la portée de votre code  
  
En outre, les deux tables doivent être remplies avec des données pour tous les enregistrements à retourner.  
  
#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Pour retourner des enregistrements d’un enregistrement parent sélectionné de l’enfant  
  
-   Appeler le <xref:System.Data.DataRow.GetChildRows%2A> méthode d’une spécifique `Customers` données de ligne et renvoie un tableau de lignes à partir de la `Orders` table :  
  
     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]  
  
#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Pour retourner l’enregistrement parent d’un enregistrement enfant sélectionné  
  
-   Appelez le <xref:System.Data.DataRow.GetParentRow%2A> méthode d’une spécifique `Orders` ligne de données et retournent une seule ligne de la `Customers` table :  
  
     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]

---
title: Remplir des datasets à l’aide de TableAdapters
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a79f7b781944bb93a60794e748eefb9375723384
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408741"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Remplir des datasets à l’aide de TableAdapters

Un composant TableAdapter remplit un DataSet avec des données de la base de données, en fonction d’une ou de plusieurs requêtes ou procédures stockées que vous spécifiez. Les TableAdapters peuvent également effectuer des ajouts, des mises à jour et des suppressions dans la base de données pour conserver les modifications que vous apportez au DataSet. Vous pouvez également émettre des commandes globales qui ne sont pas liées à une table spécifique.

> [!NOTE]
> Les TableAdapters sont générés par les concepteurs Visual Studio. Si vous créez des jeux de données par programme, utilisez DataAdapter, qui est une classe .NET.

Pour plus d’informations sur les opérations TableAdapter, vous pouvez passer directement à l’une des rubriques suivantes :

|Rubrique|Description|
|-----------|-----------------|
|[Créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Comment utiliser les concepteurs pour créer et configurer des TableAdapters|
|[Guide pratique pour créer des requêtes TableAdapter paramétrées](../data-tools/create-parameterized-tableadapter-queries.md)|Comment permettre aux utilisateurs de fournir des arguments à des procédures ou des requêtes TableAdapter|
|[Accéder directement à la base de données avec un TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Comment utiliser les méthodes DBDirect des TableAdapters|
|[Désactiver les contraintes pendant le remplissage d’un dataset](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Comment utiliser des contraintes de clé étrangère lors de la mise à jour de données|
|[Guide pratique pour étendre les fonctionnalités d’un TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Comment ajouter du code personnalisé à des TableAdapters|
|[Lire les données XML dans un dataset](../data-tools/read-xml-data-into-a-dataset.md)|Utilisation de XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Vue d’ensemble de TableAdapter

Les TableAdapters sont des composants générés par le concepteur qui se connectent à une base de données, exécutent des requêtes ou des procédures stockées et remplissent leur DataTable avec les données retournées. Les TableAdapters renvoient également les données mises à jour de votre application à la base de données. Vous pouvez exécuter autant de requêtes que vous le souhaitez sur un TableAdapter tant qu’elles retournent des données qui se conforment au schéma de la table à laquelle le TableAdapter est associé. Le diagramme suivant montre comment les TableAdapters interagissent avec les bases de données et d’autres objets en mémoire :

![Flux de données dans une application cliente](../data-tools/media/clientdatadiagram.gif)

Alors que les TableAdapters sont conçus avec l' **Concepteur de DataSet**, les classes TableAdapter ne sont pas générées en tant que classes imbriquées de <xref:System.Data.DataSet>. Ils se trouvent dans des espaces de noms distincts qui sont spécifiques à chaque jeu de données. Par exemple, si vous avez un dataset nommé `NorthwindDataSet`, les TableAdapters associés à <xref:System.Data.DataTable>s dans le `NorthwindDataSet` se trouvent dans l’espace de noms `NorthwindDataSetTableAdapters`. Pour accéder à un TableAdapter particulier par programme, vous devez déclarer une nouvelle instance du TableAdapter. Par exemple :

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Schéma DataTable associé

Lorsque vous créez un TableAdapter, vous utilisez la requête ou la procédure stockée initiale pour définir le schéma de la <xref:System.Data.DataTable>associée du TableAdapter. Vous exécutez cette requête ou procédure stockée initiale en appelant la méthode `Fill` du TableAdapter (qui remplit le <xref:System.Data.DataTable>associé du TableAdapter). Toutes les modifications apportées à la requête principale du TableAdapter sont reflétées dans le schéma de la table de données associée. Par exemple, la suppression d’une colonne de la requête principale supprime également la colonne de la table de données associée. Si des requêtes supplémentaires sur le TableAdapter utilisent des instructions SQL qui retournent des colonnes qui ne sont pas dans la requête principale, le concepteur tente de synchroniser les modifications de colonne entre la requête principale et les requêtes supplémentaires.

## <a name="tableadapter-update-commands"></a>Commandes de mise à jour de TableAdapter

La fonctionnalité de mise à jour d’un TableAdapter dépend de la quantité d’informations disponibles dans la requête principale de l' **Assistant TableAdapter**. Par exemple, les TableAdapters configurés pour récupérer des valeurs à partir de plusieurs tables (à l’aide d’une `JOIN`), de valeurs scalaires, de vues ou de résultats de fonctions d’agrégation ne sont pas créés initialement avec la possibilité d’envoyer des mises à jour à la base de données sous-jacente. Toutefois, vous pouvez configurer manuellement les commandes `INSERT`, `UPDATE`et `DELETE` dans la fenêtre **Propriétés** .

## <a name="tableadapter-queries"></a>requêtes TableAdapter

![TableAdapter avec plusieurs requêtes](../data-tools/media/tableadapter.gif)

Les TableAdapters peuvent contenir plusieurs requêtes pour remplir les tables de données qui leur sont associées. Vous pouvez définir autant de requêtes pour un TableAdapter que votre application le requiert, à condition que chaque requête retourne des données qui se conforment au même schéma que la table de données qui lui est associée. Cette fonctionnalité permet à un TableAdapter de charger différents résultats en fonction de critères différents.

Par exemple, si votre application contient une table avec des noms de clients, vous pouvez créer une requête qui remplit la table avec chaque nom de client qui commence par une certaine lettre, et une autre qui remplit la table avec tous les clients qui se trouvent dans le même État. Pour remplir une table de `Customers` avec des clients dans un État donné, vous pouvez créer une requête `FillByState` qui accepte un paramètre pour la valeur d’État comme suit : `SELECT * FROM Customers WHERE State = @State`. Vous exécutez la requête en appelant la méthode `FillByState` et en passant la valeur de paramètre comme suit : `CustomerTableAdapter.FillByState("WA")`.

En plus d’ajouter des requêtes qui retournent des données du même schéma que la table de données du TableAdapter, vous pouvez ajouter des requêtes qui retournent des valeurs scalaires (uniques). Par exemple, une requête qui retourne le nombre de clients (`SELECT Count(*) From Customers`) est valide pour un `CustomersTableAdapter,` même si les données retournées ne sont pas conformes au schéma de la table.

## <a name="clearbeforefill-property"></a>Propriété ClearBeforeFill

Par défaut, chaque fois que vous exécutez une requête pour remplir la table de données d’un TableAdapter, les données existantes sont effacées et seuls les résultats de la requête sont chargés dans la table. Affectez à la propriété `ClearBeforeFill` du TableAdapter la valeur `false` si vous souhaitez ajouter ou fusionner les données retournées par une requête aux données existantes dans une table de données. Que vous effaciez ou non les données, vous devez envoyer explicitement des mises à jour à la base de données, si vous souhaitez les rendre persistantes. N’oubliez pas d’enregistrer les modifications apportées aux données de la table avant d’exécuter une autre requête qui remplit la table. Pour plus d’informations, consultez [mettre à jour des données à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Héritage de TableAdapter

Les TableAdapters étendent les fonctionnalités des adaptateurs de données standard en encapsulant une classe <xref:System.Data.Common.DataAdapter> configurée. Par défaut, le TableAdapter hérite de la classe <xref:System.ComponentModel.Component> et ne peut pas être casté en classe <xref:System.Data.Common.DataAdapter>. Le cast d’un TableAdapter en classe <xref:System.Data.Common.DataAdapter> entraîne une erreur <xref:System.InvalidCastException>. Pour modifier la classe de base d’un TableAdapter, vous pouvez spécifier une classe qui dérive de <xref:System.ComponentModel.Component> dans la propriété de **classe de base** du TableAdapter dans le **Concepteur de DataSet**.

## <a name="tableadapter-methods-and-properties"></a>Méthodes et propriétés TableAdapter

La classe TableAdapter n’est pas un type .NET. Cela signifie que vous ne pouvez pas le Rechercher dans la documentation ou dans l' **Explorateur d’objets**. Il est créé au moment de la conception lorsque vous utilisez l’un des assistants mentionnés précédemment. Le nom assigné à un TableAdapter lorsque vous le créez est basé sur le nom de la table que vous utilisez. Par exemple, lorsque vous créez un TableAdapter basé sur une table dans une base de données nommée `Orders`, le TableAdapter est nommé `OrdersTableAdapter`. Le nom de classe du TableAdapter peut être modifié à l’aide de la propriété **Name** dans l' **Concepteur de DataSet**.

Voici les méthodes et propriétés couramment utilisées des TableAdapters :

|Membre|Description|
|------------|-----------------|
|`TableAdapter.Fill`|Remplit la table de données associée du TableAdapter avec les résultats de la commande `SELECT` du TableAdapter.|
|`TableAdapter.Update`|Renvoie les modifications à la base de données et retourne un entier qui représente le nombre de lignes affectées par la mise à jour. Pour plus d’informations, consultez [mettre à jour des données à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Retourne une nouvelle <xref:System.Data.DataTable> remplie avec des données.|
|`TableAdapter.Insert`|Crée une nouvelle ligne dans la table de données. Pour plus d’informations, consultez [Insérer de nouveaux enregistrements dans une base de données](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Détermine si une table de données est vidée avant d’appeler l’une des méthodes `Fill`.|

## <a name="tableadapter-update-method"></a>Méthode de mise à jour de TableAdapter

Les TableAdapters utilisent des commandes de données pour lire et écrire à partir de la base de données. Utilisez la requête de `Fill` initiale du TableAdapter comme base pour créer le schéma de la table de données associée, ainsi que les commandes `InsertCommand`, `UpdateCommand`et `DeleteCommand` associées à la méthode `TableAdapter.Update`. L’appel de la méthode `Update` d’un TableAdapter exécute les instructions qui ont été créées lors de la configuration initiale du TableAdapter, pas l’une des requêtes supplémentaires que vous avez ajoutées à l’aide de l' **Assistant Configuration de requêtes TableAdapter**.

Quand vous utilisez un TableAdapter, il effectue les mêmes opérations avec les commandes que vous exécutez généralement. Par exemple, lorsque vous appelez la méthode `Fill` de l’adaptateur, l’adaptateur exécute la commande de données dans sa propriété `SelectCommand` et utilise un lecteur de données (par exemple, <xref:System.Data.SqlClient.SqlDataReader>) pour charger le jeu de résultats dans la table de données. De même, lorsque vous appelez la méthode `Update` de l’adaptateur, il exécute la commande appropriée (dans les propriétés `UpdateCommand`, `InsertCommand`et `DeleteCommand`) pour chaque enregistrement modifié dans la table de données.

> [!NOTE]
> S’il y a suffisamment d’informations dans la requête principale, les commandes `InsertCommand`, `UpdateCommand`et `DeleteCommand` sont créées par défaut lors de la génération du TableAdapter. Si la requête principale du TableAdapter est plus qu’une seule table `SELECT` instruction, il est possible que le concepteur ne soit pas en mesure de générer `InsertCommand`, `UpdateCommand`et `DeleteCommand`. Si ces commandes ne sont pas générées, vous risquez de recevoir une erreur lors de l’exécution de la méthode `TableAdapter.Update`.

## <a name="tableadapter-generatedbdirectmethods"></a>GenerateDbDirectMethods de TableAdapter

Outre `InsertCommand`, `UpdateCommand`et `DeleteCommand`, les TableAdapters sont créés avec des méthodes que vous pouvez exécuter directement sur la base de données. Vous pouvez appeler ces méthodes (`TableAdapter.Insert`, `TableAdapter.Update`et `TableAdapter.Delete`) directement pour manipuler les données dans la base de données. Cela signifie que vous pouvez appeler ces méthodes individuelles à partir de votre code au lieu d’appeler `TableAdapter.Update` pour gérer les insertions, les mises à jour et les suppressions en attente pour la table de données associée.

Si vous ne souhaitez pas créer ces méthodes directes, définissez la propriété **GenerateDBDirectMethods** du TableAdapter sur `false` (dans la fenêtre **Propriétés** ). Les requêtes supplémentaires ajoutées au TableAdapter sont des requêtes autonomes, elles ne génèrent pas ces méthodes.

## <a name="tableadapter-support-for-nullable-types"></a>Prise en charge de TableAdapter pour les types Nullable

Les TableAdapters prennent en charge les types Nullable `Nullable(Of T)` et `T?`. Pour plus d’informations sur les types Nullable dans Visual Basic, consultez [Types valeur Nullable](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Pour plus d’informations sur les types C#Nullable dans, consultez [utiliser des types Nullable](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>Référence TableAdapterManager

Par défaut, une classe TableAdapterManager est générée lorsque vous créez un DataSet qui contient des tables associées. Pour empêcher la génération de la classe, remplacez la valeur de la propriété `Hierarchical Update` du jeu de données par false. Quand vous faites glisser une table qui a une relation sur l’aire de conception d’un Windows Form ou d’une page WPF, Visual Studio déclare une variable membre de la classe. Si vous n’utilisez pas DataBinding, vous devez déclarer la variable manuellement.

La classe TableAdapterManager n’est pas un type .NET. Par conséquent, vous ne pouvez pas le Rechercher dans la documentation. Il est créé au moment du design dans le cadre du processus de création du jeu de données.

Voici les méthodes et les propriétés fréquemment utilisées de la classe `TableAdapterManager` :

|Membre|Description|
|------------|-----------------|
|Méthode`UpdateAll`|Enregistre toutes les données de toutes les tables de données.|
|Propriété `BackUpDataSetBeforeUpdate`|Détermine si une copie de sauvegarde du DataSet doit être créée avant l’exécution de la méthode `TableAdapterManager.UpdateAll`. Expression.|
|propriété `TableAdapter` *TableName*|Représente un TableAdapter. Le TableAdapterManager généré contient une propriété pour chaque `TableAdapter` qu’il gère. Par exemple, un jeu de données avec une table Customers et Orders génère avec un TableAdapterManager qui contient des propriétés `CustomersTableAdapter` et `OrdersTableAdapter`.|
|Propriété `UpdateOrder`|Contrôle l’ordre des commandes INSERT, Update et DELETE individuelles. Définissez cette valeur sur l’une des valeurs de l’énumération `TableAdapterManager.UpdateOrderOption`.<br /><br /> Par défaut, le `UpdateOrder` est défini sur **InsertUpdateDelete**. Cela signifie que les insertions, les mises à jour, puis les suppressions sont effectuées pour toutes les tables du DataSet.|

## <a name="security"></a>Sécurité

Quand vous utilisez des commandes de données avec une propriété CommandType définie sur <xref:System.Data.CommandType.Text>, vérifiez attentivement les informations envoyées à partir d’un client avant de les transmettre à votre base de données. Des utilisateurs malveillants peuvent tenter d’envoyer (injecter) des instructions SQL modifiées ou supplémentaires afin d’accéder à la base de données ou de l’endommager. Avant de transférer une entrée d’utilisateur à une base de données, vérifiez toujours que les informations sont valides. Une meilleure pratique consiste à toujours utiliser des requêtes paramétrables ou des procédures stockées lorsque cela est possible.

## <a name="see-also"></a>Voir aussi

- [Outils de jeu de données](../data-tools/dataset-tools-in-visual-studio.md)

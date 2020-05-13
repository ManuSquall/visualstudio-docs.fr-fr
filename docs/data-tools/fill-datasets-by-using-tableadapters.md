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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302237"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Remplir des datasets à l’aide de TableAdapters

Un composant TableAdapter remplit un ensemble de données avec des données de la base de données, en fonction d’une ou de plusieurs requêtes ou procédures stockées que vous spécifiez. TableAdapters peut également effectuer des ajouts, des mises à jour et des suppressions sur la base de données pour persister les modifications que vous apportez à l’ensemble de données. Vous pouvez également émettre des commandes globales qui ne sont pas liées à une table spécifique.

> [!NOTE]
> TableAdapters sont générés par visual Studio designers. Si vous créez des jeux de données programmatiquement, utilisez DataAdapter, qui est une classe .NET.

Pour obtenir des informations détaillées sur les opérations de TableAdapter, vous pouvez passer directement à l’un de ces sujets :

|Rubrique|Description|
|-----------|-----------------|
|[Créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Comment utiliser les concepteurs pour créer et configurer TableAdapters|
|[Guide pratique pour créer des requêtes TableAdapter paramétrées](../data-tools/create-parameterized-tableadapter-queries.md)|Comment permettre aux utilisateurs de fournir des arguments aux procédures ou requêtes TableAdapter|
|[Accéder directement à la base de données avec un TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Comment utiliser les méthodes Dbdirect de TableAdapters|
|[Désactiver les contraintes pendant le remplissage d’un dataset](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Comment travailler avec des contraintes clés à l’étranger lors de la mise à jour des données|
|[Guide pratique pour étendre les fonctionnalités d’un TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Comment ajouter du code personnalisé à TableAdapters|
|[Lire les données XML dans un dataset](../data-tools/read-xml-data-into-a-dataset.md)|Comment travailler avec XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Vue d’ensemble de TableAdapter

Les tableadapters sont des composants générés par des concepteurs qui se connectent à une base de données, exécutent des requêtes ou des procédures stockées, et remplissent leur DataTable avec les données retournées. TableAdapters envoie également les données mises à jour de votre application vers la base de données. Vous pouvez exécuter autant de requêtes que vous voulez sur un TableAdapter tant qu’ils retournent des données qui se conforment au schéma de la table avec laquelle le TableAdapter est associé. Le diagramme suivant montre comment TableAdapters interagissent avec les bases de données et d’autres objets en mémoire :

![Flux de données dans une application cliente](../data-tools/media/clientdatadiagram.gif)

Alors que TableAdapters sont conçus avec le **Dataset Designer**, les classes <xref:System.Data.DataSet>TableAdapter ne sont pas générées comme classes imbriquées de . Ils sont situés dans des espaces de nom distincts qui sont spécifiques à chaque jeu de données. Par exemple, si vous avez `NorthwindDataSet`un jeu de données nommé, les TableAdapters qui sont associés <xref:System.Data.DataTable>à s dans le `NorthwindDataSet` serait dans l’espace de `NorthwindDataSetTableAdapters` nom. Pour accéder à un programme TableAdapter particulier, vous devez déclarer une nouvelle instance de la TableAdapter. Par exemple :

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Schéma Associé DataTable

Lorsque vous créez un TableAdapter, vous utilisez la requête initiale ou la procédure stockée <xref:System.Data.DataTable>pour définir le schéma de la TableAdapter associée . Vous exécutez cette requête initiale ou procédure stockée en `Fill` appelant la méthode de la TableAdapter (qui remplit la TableAdapter associée <xref:System.Data.DataTable>). Toute modification apportée à la requête principale du TableAdapter est reflétée dans le schéma du tableau de données associé. Par exemple, la suppression d’une colonne de la requête principale supprime également la colonne du tableau de données associé. Si des requêtes supplémentaires sur le TableAdapter utilisent des déclarations SQL qui renvoient des colonnes qui ne sont pas dans la requête principale, le concepteur tente de synchroniser les changements de colonne entre la requête principale et les requêtes supplémentaires.

## <a name="tableadapter-update-commands"></a>TableAdapter mise à jour des commandes

La fonctionnalité de mise à jour d’un TableAdapter dépend de la quantité d’informations disponibles dans la requête principale dans le **TableAdapter Wizard**. Par exemple, les tableadapters qui sont configurés `JOIN`pour récupérer des valeurs à partir de plusieurs tables (à l’aide d’une ), valeurs scalaires, vues, ou les résultats des fonctions agrégées ne sont pas initialement créés avec la possibilité d’envoyer des mises à jour à la base de données sous-jacente. Cependant, vous pouvez `INSERT` `UPDATE`configurer `DELETE` le , , et commande manuellement dans la fenêtre **Propriétés.**

## <a name="tableadapter-queries"></a>requêtes TableAdapter

![TableAdapter avec plusieurs requêtes](../data-tools/media/tableadapter.gif)

TableAdapters peut contenir plusieurs requêtes pour remplir leurs tableaux de données associés. Vous pouvez définir autant de requêtes pour un TableAdapter que votre application l’exige, tant que chaque requête renvoie des données conformes au même schéma que son tableau de données associé. Cette capacité permet à un TableAdapter de charger différents résultats en fonction de critères différents.

Par exemple, si votre application contient une table avec les noms des clients, vous pouvez créer une requête qui remplit la table avec chaque nom de client qui commence par une certaine lettre, et une autre qui remplit la table avec tous les clients qui sont situés dans le même état. Pour remplir `Customers` une table avec des clients dans `FillByState` un état donné, vous pouvez créer `SELECT * FROM Customers WHERE State = @State`une requête qui prend un paramètre pour la valeur de l’État comme suit: . Vous exécutez la requête `FillByState` en appelant la méthode et `CustomerTableAdapter.FillByState("WA")`en passant dans la valeur de paramètre comme ceci: .

En plus d’ajouter des requêtes qui renvoient les données du même schéma que le tableau de données de tableAdapter, vous pouvez ajouter des requêtes qui retournent des valeurs scalar (unique). Par exemple, une requête qui renvoie`SELECT Count(*) From Customers`un nombre `CustomersTableAdapter,` de clients ( ) est valable pour un même si les données retournées ne sont pas conformes au schéma de la table.

## <a name="clearbeforefill-property"></a>Propriété ClearBeforeFill

Par défaut, chaque fois que vous exécutez une requête pour remplir la table de données d’un TableAdapter, les données existantes sont effacées, et seuls les résultats de la requête sont chargés dans la table. Définissez la propriété de `ClearBeforeFill` TableAdapter `false` si vous souhaitez ajouter ou fusionner les données qui sont retournées d’une requête aux données existantes dans une table de données. Que vous effacez ou non les données, vous devez envoyer explicitement des mises à jour à la base de données, si vous souhaitez les persister. N’oubliez pas d’enregistrer les modifications apportées aux données dans le tableau avant d’exécuter une autre requête qui remplit la table. Pour plus d’informations, voir [Les données de mise à jour à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Héritage TableAdapter

TableAdapters étend la fonctionnalité des adaptateurs de données standard <xref:System.Data.Common.DataAdapter> en encapsulant une classe configurée. Par défaut, le TableAdapter <xref:System.ComponentModel.Component> hérite de la classe <xref:System.Data.Common.DataAdapter> et ne peut pas être jeté à la classe. Le fait de jeter <xref:System.Data.Common.DataAdapter> un TableAdapter à la classe entraîne une <xref:System.InvalidCastException> erreur. Pour changer la classe de base d’un TableAdapter, <xref:System.ComponentModel.Component> vous pouvez spécifier une classe qui dérive de la propriété de la **classe de base** de la TableAdapter dans le **Dataset Designer**.

## <a name="tableadapter-methods-and-properties"></a>Méthodes et propriétés TableAdapter

La classe TableAdapter n’est pas un type .NET. Cela signifie que vous ne pouvez pas le chercher dans la documentation ou le **navigateur d’objets**. Il est créé au moment de la conception lorsque vous utilisez l’un des sorciers mentionnés plus tôt. Le nom qui est attribué à un TableAdapter lorsque vous le créez est basé sur le nom de la table avec laquelle vous travaillez. Par exemple, lorsque vous créez un TableAdapter basé `Orders`sur une table dans `OrdersTableAdapter`une base de données nommée , le TableAdapter est nommé . Le nom de classe de la TableAdapter peut être changé en utilisant la propriété **Name** dans le **concepteur Dataset**.

Voici les méthodes et les propriétés couramment utilisées de TableAdapters :

|Membre|Description|
|------------|-----------------|
|`TableAdapter.Fill`|Remplit le tableau de données associé de TableAdapter avec les `SELECT` résultats de la commande de La TableAdapter.|
|`TableAdapter.Update`|Renvoie les modifications à la base de données et renvoie un élément qui représente le nombre de lignes touchées par la mise à jour. Pour plus d’informations, voir [Les données de mise à jour à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Retourne un <xref:System.Data.DataTable> nouveau qui est rempli de données.|
|`TableAdapter.Insert`|Crée une nouvelle ligne dans la table de données. Pour plus d’informations, voir [Insérez de nouveaux enregistrements dans une base de données](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Détermine si une table de données est vidée avant d’appeler l’une `Fill` des méthodes.|

## <a name="tableadapter-update-method"></a>Méthode de mise à jour TableAdapter

TableAdapters utiliser des commandes de données pour lire et écrire à partir de la base de données. Utilisez `Fill` la requête initiale (principale) du TableAdapter comme base pour créer le schéma de `InsertCommand` `UpdateCommand`la `DeleteCommand` table de données associée, ainsi que le , et les commandes qui sont associées à la `TableAdapter.Update` méthode. Appeler la méthode d’un `Update` TableAdapter exécute les déclarations qui ont été créées lorsque le TableAdapter a été configuré à l’origine, pas l’une des requêtes supplémentaires que vous avez ajouté avec le **TableAdapter Query Configuration Wizard**.

Lorsque vous utilisez un TableAdapter, il effectue efficacement les mêmes opérations avec les commandes que vous effectuez généralement. Par exemple, lorsque vous appelez `Fill` la méthode de l’adaptateur, l’adaptateur exécute la commande de données dans sa `SelectCommand` propriété et utilise un lecteur de données (par exemple, <xref:System.Data.SqlClient.SqlDataReader>) pour charger le résultat défini dans la table de données. De même, lorsque vous `Update` appelez la méthode de l’adaptateur, il exécute la commande appropriée (dans le `UpdateCommand`, `InsertCommand`, et `DeleteCommand` les propriétés) pour chaque enregistrement modifié dans le tableau de données.

> [!NOTE]
> S’il y a suffisamment d’informations `UpdateCommand`dans `DeleteCommand` la requête principale, le `InsertCommand`, et les commandes sont créés par défaut lorsque le TableAdapter est généré. Si la requête principale du TableAdapter est `SELECT` plus qu’une seule déclaration de table, `InsertCommand`il `UpdateCommand`est `DeleteCommand`possible que le concepteur ne sera pas en mesure de générer , , et . Si ces commandes ne sont pas générées, vous `TableAdapter.Update` pourriez recevoir une erreur lors de l’exécution de la méthode.

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods

En plus `InsertCommand` `UpdateCommand`de `DeleteCommand`, , et , TableAdapters sont créés avec des méthodes que vous pouvez exécuter directement contre la base de données. Vous pouvez appeler`TableAdapter.Insert`ces `TableAdapter.Update`méthodes `TableAdapter.Delete`( , , et ) directement pour manipuler les données dans la base de données. Cela signifie que vous pouvez appeler ces `TableAdapter.Update` méthodes individuelles à partir de votre code au lieu d’appeler pour gérer les inserts, mises à jour et supprimes qui sont en attente pour la table de données associée.

Si vous ne voulez pas créer ces méthodes directes, définissez la propriété **GenerateDbDirectMethods** de La TableAdapter `false` (dans la fenêtre **Propriétés).** D’autres requêtes qui sont ajoutées à la TableAdapter sont des requêtes autonomes — elles ne génèrent pas ces méthodes.

## <a name="tableadapter-support-for-nullable-types"></a>TableAdapter support pour les types nuls

TableAdapters soutenir les `Nullable(Of T)` `T?`types nuls et . Pour plus d’informations sur les types Nullable dans Visual Basic, consultez [Types valeur Nullable](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Pour plus d’informations sur les types nuls dans C, voir [Utilisez les types nuls](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>TableAdapterManager référence

Par défaut, une classe TableAdapterManager génère lorsque vous créez un jeu de données qui contient des tables connexes. Pour éviter que la classe ne soit `Hierarchical Update` générée, modifiez la valeur de la propriété de l’ensemble de données en faux. Lorsque vous faites glisser une table qui a une relation sur la surface de conception d’une page formulaire Windows ou WPF, Visual Studio déclare une variable membre de la classe. Si vous n’utilisez pas la databinding, vous devez déclarer manuellement la variable.

La classe TableAdapterManager n’est pas un type .NET. Par conséquent, vous ne pouvez pas le chercher dans la documentation. Il est créé au moment de la conception dans le cadre du processus de création de jeux de données.

Voici les méthodes et les propriétés fréquemment utilisées de la `TableAdapterManager` classe :

|Membre|Description|
|------------|-----------------|
|Méthode `UpdateAll`|Enregistre toutes les données de toutes les tables de données.|
|Propriété `BackUpDataSetBeforeUpdate`|Détermine s’il convient de créer une copie `TableAdapterManager.UpdateAll` de sauvegarde de l’ensemble de données avant d’exécuter la méthode. Boolean.|
|*tableName* `TableAdapter` propriété|Représente un TableAdapter. La TableAdapterManager générée contient `TableAdapter` une propriété pour chacune qu’elle gère. Par exemple, un jeu de données avec un tableau clients et commandes `CustomersTableAdapter` `OrdersTableAdapter` génère avec un TableAdapterManager qui contient et propriétés.|
|Propriété `UpdateOrder`|Contrôle l’ordre de l’insert individuel, mise à jour et supprimez les commandes. Définissez ceci à l’une des valeurs dans l’énumération. `TableAdapterManager.UpdateOrderOption`<br /><br /> Par défaut, `UpdateOrder` le est configuré à **InsertUpdateDelete**. Cela signifie que les inserts, puis les mises à jour, puis les suppressions sont effectuées pour toutes les tables dans le jeu de données.|

## <a name="security"></a>Sécurité

Lorsque vous utilisez des commandes de données <xref:System.Data.CommandType.Text>avec une propriété CommandType définie à , vérifiez soigneusement les informations qui sont envoyées à partir d’un client avant de les transmettre à votre base de données. Des utilisateurs malveillants peuvent tenter d’envoyer (injecter) des instructions SQL modifiées ou supplémentaires afin d’accéder à la base de données ou de l’endommager. Avant de transférer l’entrée de l’utilisateur vers une base de données, vérifiez toujours que les informations sont valides. Une pratique exemplaire consiste à toujours utiliser des requêtes paramétrisées ou des procédures stockées lorsque cela est possible.

## <a name="see-also"></a>Voir aussi

- [Outils Dataset](../data-tools/dataset-tools-in-visual-studio.md)

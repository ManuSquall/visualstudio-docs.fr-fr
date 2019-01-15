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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 260ea65af041e6a50afb163f697d5ff366cff825
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835982"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Remplir des datasets à l’aide de TableAdapters

Un composant du TableAdapter remplit un dataset avec des données à partir de la base de données, selon une ou plusieurs requêtes ou des procédures stockées que vous spécifiez. Les TableAdapters peuvent également effectuer ajoute, met à jour et suppressions sur la base de données pour conserver les modifications que vous apportez au jeu de données. Vous pouvez également émettre des commandes globales qui ne sont pas liées à une table spécifique.

> [!NOTE]
> Les TableAdapters sont générées par les concepteurs de Visual Studio. Si vous créez des jeux de données par programmation, utilisez DataAdapter, qui est une classe .NET Framework.

Pour plus d’informations sur les opérations du TableAdapter, vous pouvez ignorer directement à une des rubriques suivantes :

|Rubrique|Description|
|-----------|-----------------|
|[Créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Comment utiliser les concepteurs pour créer et configurer des TableAdapters|
|[Guide pratique pour créer des requêtes TableAdapter paramétrées](../data-tools/create-parameterized-tableadapter-queries.md)|Comment permettre aux utilisateurs de fournir des arguments à des procédures de TableAdapter ou des requêtes|
|[Accéder directement à la base de données avec un TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Comment utiliser les méthodes Dbdirect des TableAdapters|
|[Désactiver les contraintes pendant le remplissage d’un dataset](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|L’utilisation des contraintes foreign key lors de la mise à jour des données|
|[Guide pratique pour étendre les fonctionnalités d’un TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Comment ajouter du code personnalisé à des TableAdapters|
|[Lire les données XML dans un dataset](../data-tools/read-xml-data-into-a-dataset.md)|Comment travailler avec XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Vue d’ensemble de TableAdapter

Les TableAdapters sont des composants générés par le concepteur qui se connectent à une base de données, exécuter des requêtes ou des procédures stockées, remplir son DataTable avec les données retournées. TableAdapters également envoyer des données mises à jour à partir de votre application dans la base de données. Vous pouvez exécuter autant de requêtes que vous le souhaitez sur un TableAdapter tant qu’elles retournent des données qui est conforme au schéma de la table à laquelle le TableAdapter est associé. Le diagramme suivant montre comment les TableAdapters interagissent avec les bases de données et d’autres objets en mémoire :

![Flux de données dans une application cliente](../data-tools/media/clientdatadiagram.gif)

Alors que les TableAdapters sont conçus avec le **Concepteur de Dataset**, les classes TableAdapter ne sont pas générés en tant que classes imbriquées de <xref:System.Data.DataSet>. Ils se trouvent dans des espaces de noms distincts qui sont spécifiques à chaque jeu de données. Par exemple, si vous disposez d’un dataset nommé `NorthwindDataSet`, les TableAdapters associés <xref:System.Data.DataTable>s dans le `NorthwindDataSet` serait dans le `NorthwindDataSetTableAdapters` espace de noms. Pour accéder par programmation à un TableAdapter particulier, vous devez déclarer une nouvelle instance du TableAdapter. Par exemple :

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Schéma du DataTable associé

Lorsque vous créez un TableAdapter, vous utilisez la requête initiale ou une procédure stockée pour définir le schéma du TableAdapter associé au <xref:System.Data.DataTable>. Exécutez cette requête initiale ou de la procédure stockée en appelant le TableAdapter `Fill` (méthode) (qui remplit le TableAdapter associé au <xref:System.Data.DataTable>). Toutes les modifications sont apportées à la requête principale du TableAdapter sont répercutées dans le schéma de la table de données associée. Par exemple, la suppression d’une colonne de la requête principale supprime également la colonne à partir de la table de données associée. Si toutes les requêtes supplémentaires sur le TableAdapter utilisent des instructions SQL qui retournent les colonnes qui ne sont pas dans la requête principale, le concepteur tente de synchroniser les modifications de colonne entre la requête principale et les requêtes supplémentaires.

## <a name="tableadapter-update-commands"></a>Commandes de mise à jour de TableAdapter

La fonctionnalité de mise à jour d’un TableAdapter est dépendante de la quantité d’informations est disponible dans la requête principale dans le **Assistant TableAdapter**. Par exemple, les TableAdapters configurés pour extraire des valeurs provenant de plusieurs tables (à l’aide un `JOIN`), des valeurs scalaires, des vues ou les résultats des fonctions d’agrégation ne sont pas créés initialement avec la possibilité de renvoyer des mises à jour à la base de données sous-jacente. Toutefois, vous pouvez configurer le `INSERT`, `UPDATE`, et `DELETE` commandes manuellement dans le **propriétés** fenêtre.

## <a name="tableadapter-queries"></a>requêtes TableAdapter

![TableAdapter avec plusieurs requêtes](../data-tools/media/tableadapter.gif)

Les TableAdapters peuvent contenir plusieurs requêtes pour remplir leurs tables de données associées. Vous pouvez définir autant de requêtes pour un TableAdapter que nécessaire pour votre application, tant que chaque requête retourne des données qui sont conformes dans le même schéma que la table de données associée. Cette fonctionnalité permet à un TableAdapter charger des résultats différents selon différents critères.

Par exemple, si votre application contient une table avec les noms des clients, vous pouvez créer une requête qui remplit la table avec tous les noms de client qui commence par une lettre et une autre qui remplit la table avec tous les clients qui sont trouvent dans le même état. Pour remplir un `Customers` table avec les clients dans un état donné, vous pouvez créer un `FillByState` requête qui accepte un paramètre pour la valeur d’état comme suit : `SELECT * FROM Customers WHERE State = @State`. Vous exécutez la requête en appelant le `FillByState` (méthode) et en passant la valeur du paramètre comme suit : `CustomerTableAdapter.FillByState("WA")`.

Outre l’ajout de requêtes qui retournent des données d’un même schéma en tant que table de données du TableAdapter, vous pouvez ajouter des requêtes qui retournent des valeurs scalaires (uniques). Par exemple, une requête qui retourne le nombre de clients (`SELECT Count(*) From Customers`) est valide pour un `CustomersTableAdapter,` même si les données retournées ne sont pas conformes au schéma de la table.

## <a name="clearbeforefill-property"></a>Propriété ClearBeforeFill

Par défaut, chaque fois que vous exécutez une requête pour remplir la table de données d’un TableAdapter, les données existantes sont désactivées, et que les résultats de la requête sont chargées dans la table. Affectez à la `ClearBeforeFill` propriété `false` si vous souhaitez ajouter ou fusionner les données qui sont retournées à partir d’une requête aux données existantes dans une table de données. Vous devez explicitement envoyer des mises à jour vers la base de données, indépendamment de si vous effacez les données, si vous souhaitez les conserver. Par conséquent, n’oubliez pas d’enregistrer les modifications aux données dans la table avant d’exécuter une autre requête qui remplit la table. Pour plus d’informations, consultez [mettre à jour des données à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Héritage de TableAdapter

Les TableAdapters étendent les fonctionnalités des adaptateurs de données standard en encapsulant un configuré <xref:System.Data.Common.DataAdapter> classe. Par défaut, le TableAdapter hérite de la <xref:System.ComponentModel.Component> classe et ne peut pas être casté en la <xref:System.Data.Common.DataAdapter> classe. Conversion d’un TableAdapter à la <xref:System.Data.Common.DataAdapter> classe les résultats dans un <xref:System.InvalidCastException> erreur. Pour modifier la classe de base d’un TableAdapter, vous pouvez spécifier une classe qui dérive de <xref:System.ComponentModel.Component> dans le **classe de Base** propriété du TableAdapter dans le **Concepteur de Dataset**.

## <a name="tableadapter-methods-and-properties"></a>Propriétés et méthodes du TableAdapter

La classe TableAdapter n’est pas dans le cadre de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Cela signifie que vous ne pouvez pas rechercher dans la documentation ou le **Explorateur d’objets**. Il est créé au moment du design lorsque vous utilisez un des Assistants mentionnés précédemment. Le nom assigné à un TableAdapter lors de sa création est basé sur le nom de la table que vous travaillez. Par exemple, lorsque vous créez un TableAdapter basé sur une table dans une base de données nommée `Orders`, le TableAdapter est nommé `OrdersTableAdapter`. Le nom de classe du TableAdapter peut être modifié à l’aide de la **nom** propriété dans le **Concepteur de Dataset**.

Voici les méthodes couramment utilisées et les propriétés des TableAdapters :

|Membre|Description|
|------------|-----------------|
|`TableAdapter.Fill`|Remplit la table de données associée du TableAdapter avec les résultats du TableAdapter `SELECT` commande.|
|`TableAdapter.Update`|Renvoie les modifications à la base de données et retourne un entier qui représente le nombre de lignes affectées par la mise à jour. Pour plus d’informations, consultez [mettre à jour des données à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Retourne un nouveau <xref:System.Data.DataTable> qui est rempli avec des données.|
|`TableAdapter.Insert`|Crée une nouvelle ligne dans la table de données. Pour plus d’informations, consultez [insérer de nouveaux enregistrements dans une base de données](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Détermine si une table de données doit être vidée avant d’appeler une de la `Fill` méthodes.|

## <a name="tableadapter-update-method"></a>Méthode de mise à jour de TableAdapter

Les TableAdapters utilisent des commandes de données pour lire et écrire à partir de la base de données. Utiliser les initial du TableAdapter `Fill` requête (principale) comme base pour la création du schéma de la table de données associées, ainsi que le `InsertCommand`, `UpdateCommand`, et `DeleteCommand` commandes qui sont associés le `TableAdapter.Update` (méthode). Appel d’un TableAdapter `Update` méthode exécute les instructions qui ont été créées lorsque le TableAdapter a été configuré à l’origine, pas un des autres requêtes que vous avez ajouté avec le **Assistant Configuration de requêtes TableAdapter**.

Lorsque vous utilisez un TableAdapter, il effectue les mêmes opérations avec les commandes que vous exécuteriez généralement. Par exemple, lorsque vous appelez l’adaptateur `Fill` (méthode), l’adaptateur s’exécute la commande de données son `SelectCommand` propriété et utilise un lecteur de données (par exemple, <xref:System.Data.SqlClient.SqlDataReader>) pour charger le jeu de résultats dans la table de données. De même, lorsque vous appelez l’adaptateur `Update` (méthode), elle s’exécute la commande appropriée (dans le `UpdateCommand`, `InsertCommand`, et `DeleteCommand` propriétés) pour chaque enregistrement dans la table de données modifié.

> [!NOTE]
> S’il existe suffisamment d’informations dans la requête principale, le `InsertCommand`, `UpdateCommand`, et `DeleteCommand` commandes sont créés par défaut lors de la génération du TableAdapter. Si principal du TableAdapter requête est supérieure à une seule table `SELECT` instruction, il est possible du concepteur ne pourrez pas générer `InsertCommand`, `UpdateCommand`, et `DeleteCommand`. Si ces commandes ne sont pas générées, vous pouvez recevoir une erreur lors de l’exécution le `TableAdapter.Update` (méthode).

## <a name="tableadapter-generatedbdirectmethods"></a>GenerateDbDirectMethods de TableAdapter

En plus de `InsertCommand`, `UpdateCommand`, et `DeleteCommand`, les TableAdapters sont créés avec les méthodes que vous pouvez exécuter directement sur la base de données. Vous pouvez appeler ces méthodes (`TableAdapter.Insert`, `TableAdapter.Update`, et `TableAdapter.Delete`) directement pour manipuler des données dans la base de données. Cela signifie que vous pouvez appeler ces méthodes individuelles à partir de votre code au lieu d’appeler `TableAdapter.Update` pour gérer les insertions, mises à jour et suppressions en attente pour la table de données associée.

Si vous ne souhaitez pas créer ces méthodes directes, affectez à la **GenerateDbDirectMethods** propriété `false` (dans le **propriétés** fenêtre). Les requêtes supplémentaires sont ajoutées au TableAdapter sont des requêtes autonomes : ils ne génèrent pas ces méthodes.

## <a name="tableadapter-support-for-nullable-types"></a>Prise en charge du TableAdapter pour les types nullables

Les TableAdapters prennent en charge les types nullables `Nullable(Of T)` et `T?`. Pour plus d’informations sur les types Nullable dans Visual Basic, consultez [Types valeur Nullable](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Pour plus d’informations sur les types nullable dans C#, consultez [utiliser des types nullables](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>Référence de TableAdapterManager

Par défaut, une classe TableAdapterManager génère lorsque vous créez un dataset qui contient les tables associées. Pour éviter que la classe en cours de génération, modifiez la valeur de la `Hierarchical Update` propriété du jeu de données sur false. Lorsque vous faites glisser une table qui possède une relation sur l’aire de conception d’un Windows Form ou d’une page WPF, Visual Studio déclare une variable membre de la classe. Si vous n’utilisez la liaison de données, vous devez manuellement déclarer la variable.

La classe TableAdapterManager n’est pas dans le cadre de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Par conséquent, vous ne pouvez pas chercher dans la documentation. Il est créé au moment du design dans le cadre du processus de création de jeu de données.

Les éléments suivants sont les méthodes fréquemment utilisées et les propriétés de la `TableAdapterManager` classe :

|Membre|Description|
|------------|-----------------|
|Méthode `UpdateAll`|Enregistre toutes les données de toutes les tables de données.|
|Propriété`BackUpDataSetBeforeUpdate` |Détermine s’il faut créer une copie de sauvegarde du jeu de données avant d’exécuter le `TableAdapterManager.UpdateAll` (méthode). Valeur booléenne.|
|*tableName* `TableAdapter` propriété|Représente un TableAdapter. Le composant TableAdapterManager généré contient une propriété pour chaque `TableAdapter` qu’il gère. Par exemple, un jeu de données avec une table Customers et Orders génère avec un TableAdapterManager contienne `CustomersTableAdapter` et `OrdersTableAdapter` propriétés.|
|Propriété`UpdateOrder` |Contrôler l’ordre de l’individuel insert, update et les commandes delete. Définissez ce paramètre à une des valeurs dans le `TableAdapterManager.UpdateOrderOption` énumération.<br /><br /> Par défaut, le `UpdateOrder` a la valeur **InsertUpdateDelete**. Cela signifie que les insertions, puis met à jour et supprime ensuite sont effectuées pour toutes les tables dans le jeu de données.|

## <a name="security"></a>Sécurité

Lorsque vous utilisez des commandes de données avec une propriété CommandType avec <xref:System.Data.CommandType.Text>, soigneusement vérifier les informations qui sont envoyées à partir d’un client avant de le transmettre à votre base de données. Des utilisateurs malveillants peuvent tenter d’envoyer (injecter) des instructions SQL modifiées ou supplémentaires afin d’accéder à la base de données ou de l’endommager. Avant de transférer l’entrée utilisateur et une base de données, vérifiez toujours que les informations sont valides. Une bonne pratique consiste à toujours utiliser des requêtes paramétrables ou les procédures stockées lorsque cela est possible.

## <a name="see-also"></a>Voir aussi

- [Outils de jeu de données](../data-tools/dataset-tools-in-visual-studio.md)

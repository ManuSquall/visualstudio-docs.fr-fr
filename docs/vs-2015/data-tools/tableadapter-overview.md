---
title: Vue d’ensemble de TableAdapter | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DataAccessor
- vbdata.Microsoft.VSDesigner.DataSource.DataAccessor
- TableAdapter
- vs.data.TableAdapter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], table adapters
- TableAdapters, queries
- data [Visual Studio], TableAdapters
- query data in Visual Studio
- TableAdapter.GetData
- TableAdapter.Fill
- data [Visual Studio], datasets
- TableAdapters
- table adapters
ms.assetid: a87c46a0-52ab-432a-a864-9ba55069f9eb
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1d5aabd4892011aa5c59abafc5d08840d1c8f5a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506161"
---
# <a name="tableadapter-overview"></a>Vue d'ensemble de TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les TableAdapters sont des composants générés par le concepteur qui se connectent à une base de données, exécuter des requêtes ou des procédures stockées et remplir son DataTable avec les données retournées. Les TableAdapters sont également utilisés pour envoyer des données mises à jour à partir de votre application dans la base de données. Vous pouvez avoir autant de requêtes que vous le souhaitez sur un TableAdapter tant qu’elles retournent des données qui est conforme au schéma de la table à laquelle le TableAdapter est associé. Le diagramme suivant montre comment les TableAdapters interagissent avec les bases de données et d’autres objets en mémoire :  
  
 ![Flux de données dans une application cliente](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Alors que les TableAdapters sont conçus avec le **Concepteur de Dataset**, les classes TableAdapter générées ne sont pas générés en tant que classes imbriquées de la <xref:System.Data.DataSet>. Ils se trouvent dans un espace de noms distinct spécifique à chaque jeu de données. Par exemple, si vous disposez d’un dataset nommé `NorthwindDataSet`, les TableAdapters associés le <xref:System.Data.DataTable>s dans le `NorthwindDataSet` serait dans le `NorthwindDataSetTableAdapters` espace de noms. Pour accéder par programmation à un TableAdapter particulier, vous devez déclarer une nouvelle instance du TableAdapter. Exemple :  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>Schéma du DataTable associé  
 Lorsque la création d’un TableAdapter, la requête initiale ou la procédure stockée est utilisé pour définir le schéma du TableAdapter associé au <xref:System.Data.DataTable>. Vous exécutez cette requête initiale ou une procédure stockée en appelant le TableAdapter `Fill` (méthode) (qui remplit le TableAdapter associé au <xref:System.Data.DataTable>). Toutes les modifications apportées à la requête principale du TableAdapter sont répercutées dans le schéma de la table de données associée. Par exemple, la suppression d’une colonne de la requête principale supprime la colonne de la table de données associée. Si toutes les requêtes supplémentaires sur le TableAdapter utilisent des instructions SQL retournant des colonnes qui ne sont pas dans la requête principale, le concepteur tente de synchroniser les modifications de colonne entre la requête principale et toutes les requêtes supplémentaires. Pour plus d’informations, consultez [Comment : modifier des TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
## <a name="tableadapter-update-commands"></a>Commandes de mise à jour du TableAdapter  
 La fonctionnalité de mise à jour d’un TableAdapter est dépendante de la quantité d’informations est disponible en fonction de la requête principale fournie dans l’Assistant TableAdapter. Par exemple, les TableAdapters configurés pour extraire des valeurs provenant de plusieurs tables (jointures), des valeurs scalaires, vues ou les résultats des fonctions d’agrégation ne sont pas initialement créées avec la possibilité de renvoyer des mises à jour à la base de données sous-jacente. Toutefois, vous pouvez configurer les commandes INSERT, UPDATE et DELETE manuellement dans le **propriétés** fenêtre.  
  
## <a name="tableadapter-queries"></a>Requêtes TableAdapter  
 ![TableAdapter avec plusieurs requêtes](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Les TableAdapters peuvent contenir plusieurs requêtes pour remplir leurs tables de données associées. Vous pouvez définir autant de requêtes pour un TableAdapter que nécessaire pour votre application, tant que chaque requête retourne des données qui sont conformes dans le même schéma que la table de données associée. Cela permet le chargement des données qui répondent à différents critères. Par exemple, si votre application contient une table de clients, vous pouvez créer une requête qui remplit la table avec tous les clients dont le nom commence par une lettre et une autre requête qui remplit la table avec tous les clients situés dans le même état. Pour remplir un `Customers` table avec les clients dans un état donné, vous pouvez créer un `FillByState` requête qui accepte un paramètre pour la valeur d’état : `SELECT * FROM Customers WHERE State = @State`. Vous exécutez la requête en appelant le `FillByState` (méthode) et en passant la valeur du paramètre comme suit : `CustomerTableAdapter.FillByState("WA")`. Pour plus d’informations, consultez [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
 Outre les requêtes qui retournent des données d’un même schéma en tant que table de données du TableAdapter, vous pouvez ajouter des requêtes qui retournent des valeurs scalaires (uniques). Par exemple, la création d’une requête qui retourne un nombre de clients (`SELECT Count(*) From Customers`) est valide pour un `CustomersTableAdapter` même si les données renvoyées n’est pas conforme au schéma de la table.  
  
## <a name="clearbeforefill-property"></a>Propriété ClearBeforeFill  
 Par défaut, chaque fois que vous exécutez une requête pour remplir la table de données d’un TableAdapter, les données sont désactivées et que les résultats de la requête sont chargées dans la table. Affectez à la `ClearBeforeFill` propriété `false` si vous souhaitez ajouter ou fusionner les données retournées par une requête aux données existantes dans une table de données. Vous devez explicitement envoyer des mises à jour vers la base de données, indépendamment de si vous effacez les données, si vous le souhaitez. Par conséquent, n’oubliez pas d’enregistrer les modifications apportées aux données dans la table avant d’exécuter une autre requête qui remplit la table. Pour plus d’informations, consultez [mettre à jour des données à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>Héritage de TableAdapter  
 Les TableAdapters étendent les fonctionnalités des adaptateurs de données standard en encapsulant un configuré <xref:System.Data.Common.DataAdapter>. Par défaut, dont hérite le TableAdapter <xref:System.ComponentModel.Component> et ne peut pas être casté en la <xref:System.Data.Common.DataAdapter> classe. Conversion d’un TableAdapter à un <xref:System.Data.Common.DataAdapter> entraîne une <xref:System.InvalidCastException>. Pour modifier la classe de base d’un TableAdapter, vous pouvez taper une classe qui dérive de <xref:System.ComponentModel.Component> dans le **classe de Base** propriété du TableAdapter dans le **Concepteur de Dataset**.  
  
## <a name="tableadapter-methods-and-properties"></a>Propriétés et méthodes du TableAdapter  
 La classe TableAdapter n’est pas dans le cadre de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], et vous ne pouvez pas le rechercher dans la documentation ou le **Explorateur d’objets**. Il est créé au moment du design lorsque vous utilisez un des Assistants mentionnés ci-dessus. Le nom attribué à un TableAdapter lors de sa création est basé sur le nom de la table que vous travaillez. Par exemple, lorsque la création d’un TableAdapter basé sur une table dans une base de données nommée `Orders`, le TableAdapter est nommé `OrdersTableAdapter`. Le nom de classe du TableAdapter peut être modifié à l’aide de la **nom** propriété dans le **Concepteur de Dataset**.  
  
 Voici les méthodes couramment utilisées et les propriétés des TableAdapters :  
  
|Membre|Description|  
|------------|-----------------|  
|`TableAdapter.Fill`|Remplit la table de données associée du TableAdapter avec les résultats de la commande SELECT du TableAdapter. Pour plus d’informations, consultez [Comment : remplir un dataset avec des données](../data-tools/how-to-fill-a-dataset-with-data.md).|  
|`TableAdapter.Update`|Renvoie les modifications à la base de données et retourne un entier représentant le nombre de lignes affectées par la mise à jour. Pour plus d’informations, consultez [mettre à jour des données à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Retourne un nouvel <xref:System.Data.DataTable> rempli avec des données.|  
|`TableAdapter.Insert`|Crée une nouvelle ligne dans la table de données. Pour plus d’informations, consultez [Comment : ajouter des lignes à un DataTable](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).|  
|`TableAdapter.ClearBeforeFill`|Détermine si une table de données doit être vidée avant d’appeler une de la `Fill` méthodes.|  
  
## <a name="tableadapter-update-method"></a>Méthode de mise à jour du TableAdapter  
 Les TableAdapters utilisent des commandes de données pour lire et écrire à partir de la base de données. Initiale du TableAdapter `Fill` requête (principal) est utilisé comme base pour la création du schéma de la table de données associées, ainsi que le `InsertCommand`, `UpdateCommand`, et `DeleteCommand` commandes associées à la `TableAdapter.Update` (méthode). Cela signifie que l’appel d’un TableAdapter `Update` méthode exécute les instructions créées lorsque le TableAdapter a été configuré à l’origine, et pas une des requêtes supplémentaires ajoutées avec la **Assistant Configuration de requêtes TableAdapter**.  
  
 Lorsque vous utilisez un TableAdapter, il effectue les mêmes opérations avec les commandes que vous pourriez effectuer. Par exemple, lorsque vous appelez l’adaptateur `Fill` (méthode), l’adaptateur exécute la commande de données dans son `SelectCommand` propriété et utilise un lecteur de données (par exemple, <xref:System.Data.SqlClient.SqlDataReader>) pour charger le jeu de résultats dans la table de données. De même, lorsque vous appelez l’adaptateur `Update` (méthode), il exécute la commande appropriée (dans le `UpdateCommand`, `InsertCommand`, et `DeleteCommand` propriétés) pour chaque enregistrement dans la table de données modifié.  
  
> [!NOTE]
>  S’il existe suffisamment d’informations dans la requête principale, le `InsertCommand`, `UpdateCommand`, et `DeleteCommand` commandes sont créés par défaut lors de la génération du TableAdapter. Si principal du TableAdapter requête est supérieur à une instruction SELECT de table unique, il est possible que le concepteur ne sera pas en mesure de générer le `InsertCommand`, `UpdateCommand`, et `DeleteCommand`. Si ces commandes ne sont pas générés, vous pouvez recevoir une erreur lors de l’exécution le `TableAdapter.Update` (méthode).  
  
## <a name="tableadapter-generatedbdirectmethods"></a>GenerateDbDirectMethods de TableAdapter  
 Outre le `InsertCommand`, `UpdateCommand`, et `DeleteCommand`, les TableAdapters sont créés avec des méthodes qui peuvent être exécutées directement sur la base de données. Ces méthodes (`TableAdapter.Insert`, `TableAdapter.Update`, et `TableAdapter.Delete`) peut être appelé directement pour manipuler des données dans la base de données. Cela signifie que vous pouvez appeler ces méthodes individuelles à partir de votre code au lieu d’appeler TableAdapter.Update pour gérer les insertions, mises à jour et suppressions en attente pour la table de données associée.  
  
 Si vous ne souhaitez pas créer ces méthodes directes, affectez à la **GenerateDbDirectMethods** propriété `false` (dans le **propriétés** fenêtre). Les requêtes supplémentaires ajoutées au TableAdapter sont des requêtes autonomes : ils ne génèrent pas de ces méthodes.  
  
## <a name="tableadapter-support-for-nullable-types"></a>Prise en charge du TableAdapter pour les Types nullables  
 Les TableAdapters prennent en charge les types nullables `Nullable(Of T)` et `T?`. Pour plus d’informations sur les types nullable dans Visual Basic, consultez [des Types valeur Nullable](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). Pour plus d’informations sur les types nullable en c#, consultez [à l’aide des Types Nullable](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Comment : établir une connexion à des données d’une base de données](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Procédure pas à pas : Connexion aux données dans une base de données (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Enregistrer des données](../data-tools/saving-data.md)
---
title: Insérer de nouveaux enregistrements dans une base de données
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8ec5ee4a56e36696ca88f032c3e2cf2622170f96
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="insert-new-records-into-a-database"></a>Insérer de nouveaux enregistrements dans une base de données
Pour insérer des enregistrements dans une base de données, vous pouvez utiliser la `TableAdapter.Update` méthode ou l’une des méthodes DBDirect du TableAdapter (en particulier le `TableAdapter.Insert` (méthode)). Pour plus d’informations, consultez [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

 Si votre application n’utilise pas les TableAdapters, vous pouvez utiliser les objets de commande (par exemple, <xref:System.Data.SqlClient.SqlCommand>) pour insérer de nouveaux enregistrements dans votre base de données.

 Si votre application utilise des groupes de données pour stocker les données, utilisez le `TableAdapter.Update` (méthode). Le `Update` méthode envoie toutes les modifications (mises à jour, insertions et suppressions) à la base de données.

 Si votre application utilise des objets pour stocker des données, ou si vous souhaitez mieux contrôler la création de nouveaux enregistrements dans la base de données, utilisez le `TableAdapter.Insert` (méthode).

 Si votre TableAdapter n’a pas un `Insert` (méthode), cela signifie que le TableAdapter est configuré pour utiliser des procédures stockées ou son `GenerateDBDirectMethods` est définie sur `false`. Essayez de définir du TableAdapter `GenerateDBDirectMethods` propriété `true` depuis le **Concepteur de Dataset**, puis enregistrez le jeu de données. Cette opération régénère le TableAdapter. Si le TableAdapter n’est pas encore un `Insert` (méthode), puis la table ne fournit probablement pas suffisamment d’informations pour faire la distinction entre des lignes individuelles schéma (par exemple, il ne peut être aucun jeu de clé primaire sur la table).

## <a name="insert-new-records-by-using-tableadapters"></a>Insérer de nouveaux enregistrements à l’aide des TableAdapters
 TableAdapters offrent des moyens différents pour insérer de nouveaux enregistrements dans une base de données, selon les besoins de votre application.

 Si votre application utilise des datasets pour stocker des données, vous pouvez simplement ajouter de nouveaux enregistrements à l’élément <xref:System.Data.DataTable> dans le jeu de données, puis appelez le `TableAdapter.Update` (méthode). Le `TableAdapter.Update` méthode envoie toutes les modifications le <xref:System.Data.DataTable> à la base de données (y compris les enregistrements modifiés et supprimés).

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Pour insérer de nouveaux enregistrements dans une base de données à l’aide de la méthode TableAdapter.Update

1.  Ajouter des enregistrements à l’élément <xref:System.Data.DataTable> en créant un <xref:System.Data.DataRow> et en l’ajoutant à la <xref:System.Data.DataTable.Rows%2A> collection.

2.  Une fois que les nouvelles lignes sont ajoutées à la <xref:System.Data.DataTable>, appelez le `TableAdapter.Update` (méthode). Vous pouvez contrôler la quantité de données à mettre à jour en passant l’intégralité d’un <xref:System.Data.DataSet>, un <xref:System.Data.DataTable>, un tableau de <xref:System.Data.DataRow>s ou un seul <xref:System.Data.DataRow>.

 Le code suivant montre comment ajouter un nouvel enregistrement à un <xref:System.Data.DataTable> , puis appelez le `TableAdapter.Update` méthode pour enregistrer la nouvelle ligne à la base de données. (Cet exemple utilise le `Region` table dans la base de données Northwind.)

 [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
 [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Pour insérer de nouveaux enregistrements dans une base de données à l’aide de la méthode TableAdapter.Insert
Si votre application utilise des objets pour stocker les données, vous pouvez utiliser la `TableAdapter.Insert` méthode pour créer des lignes directement dans la base de données. Le `Insert` méthode accepte les valeurs individuelles pour chaque colonne en tant que paramètres. Appel de la méthode insère un nouvel enregistrement dans la base de données avec les valeurs de paramètre passées.

- Appelez la `Insert` méthode, en passant les valeurs pour chaque colonne en tant que paramètres.

 La procédure suivante illustre l’utilisation de la `TableAdapter.Insert` méthode pour insérer des lignes. Cet exemple insère des données dans le `Region` table dans la base de données Northwind.

 > [!NOTE]
 >  Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

 [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
 [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Insérer de nouveaux enregistrements à l’aide d’objets de commande
Vous pouvez insérer de nouveaux enregistrements directement dans une base de données à l’aide d’objets de commande.

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Pour insérer de nouveaux enregistrements dans une base de données à l’aide d’objets de commande

-   Créer un nouvel objet de commande, puis définissez son `Connection`, `CommandType`, et `CommandText` propriétés.

 L’exemple suivant illustre l’insertion d’enregistrements dans une base de données à l’aide d’objet de commande. Il insère des données dans le `Region` table dans la base de données Northwind.

 [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
 [!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-framework-security"></a>Sécurité .NET Framework
 Vous devez avoir accès à la base de données que vous essayez de vous connecter à, ainsi que des autorisations pour effectuer des insertions dans la table souhaitée.

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
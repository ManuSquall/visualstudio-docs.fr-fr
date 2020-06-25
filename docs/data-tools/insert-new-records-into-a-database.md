---
title: Insérer de nouveaux enregistrements dans une base de données
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b703d3ccc6ffbd5e2449a1768071b930f606f37f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281992"
---
# <a name="insert-new-records-into-a-database"></a>Insérer de nouveaux enregistrements dans une base de données

Pour insérer de nouveaux enregistrements dans une base de données, vous pouvez utiliser la `TableAdapter.Update` méthode ou l’une des méthodes DBDirect du TableAdapter (en particulier la `TableAdapter.Insert` méthode). Pour plus d’informations, consultez [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Si votre application n’utilise pas de TableAdapters, vous pouvez utiliser des objets de commande (par exemple, <xref:System.Data.SqlClient.SqlCommand> ) pour insérer de nouveaux enregistrements dans votre base de données.

Si votre application utilise des jeux de données pour stocker des données, utilisez la `TableAdapter.Update` méthode. La `Update` méthode envoie toutes les modifications (mises à jour, insertions et suppressions) à la base de données.

Si votre application utilise des objets pour stocker des données, ou si vous souhaitez un contrôle plus fin sur la création d’enregistrements dans la base de données, utilisez la `TableAdapter.Insert` méthode.

Si votre TableAdapter n’a pas de `Insert` méthode, cela signifie que le TableAdapter est configuré pour utiliser des procédures stockées ou que sa `GenerateDBDirectMethods` propriété a la valeur `false` . Essayez de définir la propriété du TableAdapter `GenerateDBDirectMethods` à `true` partir de dans le **Concepteur de DataSet**, puis enregistrez le jeu de données. Cela permet de régénérer le TableAdapter. Si le TableAdapter n’a toujours `Insert` pas de méthode, il est probable que la table ne fournisse pas suffisamment d’informations de schéma pour faire la distinction entre des lignes individuelles (par exemple, il se peut qu’il n’y ait pas de clé primaire définie sur la table).

## <a name="insert-new-records-by-using-tableadapters"></a>Insérer de nouveaux enregistrements à l’aide de TableAdapters

Les TableAdapters offrent différentes façons d’insérer de nouveaux enregistrements dans une base de données, en fonction des exigences de votre application.

Si votre application utilise des datasets pour stocker des données, vous pouvez simplement ajouter de nouveaux enregistrements aux souhaités <xref:System.Data.DataTable> dans le DataSet, puis appeler la `TableAdapter.Update` méthode. La `TableAdapter.Update` méthode envoie toutes les modifications apportées <xref:System.Data.DataTable> à la base de données (y compris les enregistrements modifiés et supprimés).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Pour insérer de nouveaux enregistrements dans une base de données à l’aide de la méthode TableAdapter. Update

1. Ajoutez de nouveaux enregistrements au souhaité <xref:System.Data.DataTable> en créant un nouveau <xref:System.Data.DataRow> et en l’ajoutant à la <xref:System.Data.DataTable.Rows%2A> collection.

2. Une fois les nouvelles lignes ajoutées au <xref:System.Data.DataTable> , appelez la `TableAdapter.Update` méthode. Vous pouvez contrôler la quantité de données à mettre à jour en passant une valeur entière <xref:System.Data.DataSet> , un <xref:System.Data.DataTable> , un tableau de ou <xref:System.Data.DataRow> un unique <xref:System.Data.DataRow> .

   Le code suivant montre comment ajouter un nouvel enregistrement à un <xref:System.Data.DataTable> , puis appeler la `TableAdapter.Update` méthode pour enregistrer la nouvelle ligne dans la base de données. (Cet exemple utilise la `Region` table de la base de données Northwind.)

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Pour insérer de nouveaux enregistrements dans une base de données à l’aide de la méthode TableAdapter. Insert

Si votre application utilise des objets pour stocker des données, vous pouvez utiliser la `TableAdapter.Insert` méthode pour créer des lignes directement dans la base de données. La `Insert` méthode accepte les valeurs individuelles pour chaque colonne en tant que paramètres. L’appel de la méthode insère un nouvel enregistrement dans la base de données avec les valeurs de paramètres passées.

- Appelez la méthode du TableAdapter en `Insert` passant les valeurs de chaque colonne en tant que paramètres.

La procédure suivante montre comment utiliser la `TableAdapter.Insert` méthode pour insérer des lignes. Cet exemple insère des données dans la `Region` table de la base de données Northwind.

> [!NOTE]
> Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Insérer de nouveaux enregistrements à l’aide d’objets de commande

Vous pouvez insérer de nouveaux enregistrements directement dans une base de données à l’aide d’objets de commande.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Pour insérer de nouveaux enregistrements dans une base de données à l’aide d’objets de commande

- Créez un nouvel objet de commande, puis définissez ses `Connection` `CommandType` Propriétés, et `CommandText` .

L’exemple suivant illustre l’insertion d’enregistrements dans une base de données à l’aide d’un objet Command. Elle insère des données dans la `Region` table de la base de données Northwind.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-security"></a>Sécurité .NET

Vous devez avoir accès à la base de données à laquelle vous essayez de vous connecter, ainsi qu’à l’autorisation d’effectuer des insertions dans la table souhaitée.

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)

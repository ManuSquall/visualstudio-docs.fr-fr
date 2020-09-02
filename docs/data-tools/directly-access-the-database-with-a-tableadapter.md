---
title: Accéder directement à la base de données avec un TableAdapter
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 22d84e9b4beafd64cc629a295bcfa7f9f67afb6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282564"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Accéder directement à la base de données avec un TableAdapter

Outre les `InsertCommand` `UpdateCommand` TableAdapters, et, les `DeleteCommand` TableAdapters sont créés avec des méthodes qui peuvent être exécutées directement sur la base de données. Vous pouvez appeler ces méthodes ( `TableAdapter.Insert` , `TableAdapter.Update` et `TableAdapter.Delete` ) pour manipuler les données directement dans la base de données.

Si vous ne souhaitez pas créer ces méthodes directes, affectez à la propriété du TableAdapter la valeur `GenerateDbDirectMethods` `false` dans la fenêtre **Propriétés** . Si des requêtes sont ajoutées à un TableAdapter en plus de la requête principale du TableAdapter, il s’agit de requêtes autonomes qui ne génèrent pas ces `DbDirect` méthodes.

## <a name="send-commands-directly-to-a-database"></a>Envoyer des commandes directement à une base de données

Appelez la `DbDirect` méthode TableAdapter qui effectue la tâche que vous essayez d’accomplir.

### <a name="to-insert-new-records-directly-into-a-database"></a>Pour insérer de nouveaux enregistrements directement dans une base de données

- Appelez la méthode du TableAdapter en `Insert` passant les valeurs de chaque colonne en tant que paramètres. La procédure suivante utilise la `Region` table de la base de données Northwind comme exemple.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Pour mettre à jour des enregistrements directement dans une base de données

- Appelez la méthode du TableAdapter `Update` , en passant les valeurs nouvelles et originales pour chaque colonne en tant que paramètres.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Pour supprimer des enregistrements directement d’une base de données

- Appelez la méthode du TableAdapter en `Delete` passant les valeurs de chaque colonne comme paramètres de la `Delete` méthode. La procédure suivante utilise la `Region` table de la base de données Northwind comme exemple.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Voir aussi

- [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

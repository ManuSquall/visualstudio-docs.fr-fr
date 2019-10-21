---
title: Accéder directement à la base de données avec un TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e8d5d8e3091b464084df065bb7b889db9fc2194f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648516"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Accéder directement à la base de données avec un TableAdapter

En plus des `InsertCommand`, `UpdateCommand` et `DeleteCommand`, les TableAdapters sont créés avec des méthodes qui peuvent être exécutées directement sur la base de données. Vous pouvez appeler ces méthodes (`TableAdapter.Insert`, `TableAdapter.Update` et `TableAdapter.Delete`) pour manipuler les données directement dans la base de données.

Si vous ne souhaitez pas créer ces méthodes directes, définissez la propriété `GenerateDbDirectMethods` du TableAdapter sur `false` dans la fenêtre **Propriétés** . Si des requêtes sont ajoutées à un TableAdapter en plus de la requête principale du TableAdapter, il s’agit de requêtes autonomes qui ne génèrent pas ces `DbDirect` des méthodes.

## <a name="send-commands-directly-to-a-database"></a>Envoyer des commandes directement à une base de données

Appelez la méthode `DbDirect` TableAdapter qui effectue la tâche que vous essayez d’accomplir.

### <a name="to-insert-new-records-directly-into-a-database"></a>Pour insérer de nouveaux enregistrements directement dans une base de données

- Appelez la méthode `Insert` du TableAdapter, en passant les valeurs de chaque colonne en tant que paramètres. La procédure suivante utilise la table `Region` de la base de données Northwind comme exemple.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Pour mettre à jour des enregistrements directement dans une base de données

- Appelez la méthode `Update` du TableAdapter, en passant les valeurs nouvelles et originales pour chaque colonne en tant que paramètres.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Pour supprimer des enregistrements directement d’une base de données

- Appelez la méthode `Delete` du TableAdapter, en passant les valeurs de chaque colonne en tant que paramètres de la méthode `Delete`. La procédure suivante utilise la table `Region` de la base de données Northwind comme exemple.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Voir aussi

- [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
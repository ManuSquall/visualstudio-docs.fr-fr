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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f120f29494b8c519253c98f889496189e7e2594f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931622"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Accéder directement à la base de données avec un TableAdapter

Outre le `InsertCommand`, `UpdateCommand`, et `DeleteCommand`, les TableAdapters sont créés avec des méthodes qui peuvent être exécutées directement sur la base de données. Vous pouvez appeler ces méthodes (`TableAdapter.Insert`, `TableAdapter.Update`, et `TableAdapter.Delete`) pour manipuler des données directement dans la base de données.

Si vous ne souhaitez pas créer ces méthodes directes, affectez à la `GenerateDbDirectMethods` propriété `false` dans le **propriétés** fenêtre. Si toutes les requêtes sont ajoutés à un TableAdapter en plus de la requête principale du TableAdapter, ils sont des requêtes autonomes qui ne génèrent pas ces `DbDirect` méthodes.

## <a name="send-commands-directly-to-a-database"></a>Envoyer des commandes directement à une base de données

Appelez le TableAdapter `DbDirect` méthode qui effectue la tâche que vous essayez d’accomplir.

### <a name="to-insert-new-records-directly-into-a-database"></a>Pour insérer de nouveaux enregistrements directement dans une base de données

-   Appelez le TableAdapter `Insert` méthode, en passant les valeurs pour chaque colonne en tant que paramètres. La procédure suivante utilise le `Region` table dans la base de données Northwind comme exemple.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Pour mettre à jour des enregistrements directement dans une base de données

-   Appelez le TableAdapter `Update` méthode, en passant les valeurs nouvelles et originale pour chaque colonne en tant que paramètres.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Pour supprimer des enregistrements directement à partir d’une base de données

-   Appelez le TableAdapter `Delete` méthode, en passant les valeurs pour chaque colonne en tant que paramètres de la `Delete` (méthode). La procédure suivante utilise le `Region` table dans la base de données Northwind comme exemple.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Voir aussi

- [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
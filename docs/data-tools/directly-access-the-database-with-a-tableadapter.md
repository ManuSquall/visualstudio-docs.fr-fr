---
title: Accéder directement à la base de données avec un TableAdapter
description: Accédez directement à une base de données avec un TableAdapter, à l’aide de méthodes telles que Insert, Update et Delete pour manipuler les données directement dans la base de données.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 30248632eacde07cfcc94213aeeb75ecac8dcf70
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215914"
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

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

### <a name="to-update-records-directly-in-a-database"></a>Pour mettre à jour des enregistrements directement dans une base de données

- Appelez la méthode du TableAdapter `Update` , en passant les valeurs nouvelles et originales pour chaque colonne en tant que paramètres.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet18":::

### <a name="to-delete-records-directly-from-a-database"></a>Pour supprimer des enregistrements directement d’une base de données

- Appelez la méthode du TableAdapter en `Delete` passant les valeurs de chaque colonne comme paramètres de la `Delete` méthode. La procédure suivante utilise la `Region` table de la base de données Northwind comme exemple.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet21":::

## <a name="see-also"></a>Voir aussi

- [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

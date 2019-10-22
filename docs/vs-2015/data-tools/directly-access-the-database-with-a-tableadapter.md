---
title: Accéder directement à la base de données avec un TableAdapter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 58500e59a624dac55824033b8b9667754a9040c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657371"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Accéder directement à la base de données avec un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En plus des `InsertCommand`, `UpdateCommand` et `DeleteCommand`, les TableAdapters sont créés avec des méthodes qui peuvent être exécutées directement sur la base de données. Ces méthodes (`TableAdapter.Insert`, `TableAdapter.Update` et `TableAdapter.Delete`) peuvent être appelées pour manipuler les données directement dans la base de données.

 Si vous ne souhaitez pas créer ces méthodes directes, définissez la propriété `GenerateDbDirectMethods` du TableAdapter sur `false` dans la fenêtre **Propriétés** . Si des requêtes sont ajoutées à un TableAdapter en plus de la requête principale du TableAdapter, il s’agit de requêtes autonomes qui ne génèrent pas ces méthodes DbDirect.

## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly à une base de données
 Appelez la méthode DbDirect du TableAdapter qui effectue la tâche que vous essayez d’accomplir.

#### <a name="to-insert-new-records-directly-into-a-database"></a>Pour insérer de nouveaux enregistrements directement dans une base de données

- Appelez la méthode `Insert` du TableAdapter, en passant les valeurs de chaque colonne en tant que paramètres. La procédure suivante utilise la table `Region` de la base de données Northwind en est un exemple.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

#### <a name="to-update-records-directly-in-a-database"></a>Pour mettre à jour des enregistrements directement dans une base de données

- Appelez la méthode `Update` du TableAdapter, en passant les valeurs nouvelles et originales pour chaque colonne en tant que paramètres.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]

#### <a name="to-delete-records-directly-from-a-database"></a>Pour supprimer des enregistrements directement d’une base de données

- Appelez la méthode `Delete` du TableAdapter, en passant les valeurs de chaque colonne en tant que paramètres de la méthode `Delete`. La procédure suivante utilise la table `Region` de la base de données Northwind en est un exemple.

    > [!NOTE]
    > Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.

     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]

## <a name="see-also"></a>Voir aussi
 [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5226f5c235b3af10fba4fd0fab3ee44ceb72a93e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654098"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Accéder directement à la base de données avec un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Outre le `InsertCommand`, `UpdateCommand`, et `DeleteCommand`, les TableAdapters sont créés avec des méthodes qui peuvent être exécutées directement sur la base de données. Ces méthodes (`TableAdapter.Insert`, `TableAdapter.Update`, et `TableAdapter.Delete`) peut être appelé pour manipuler des données directement dans la base de données.  
  
 Si vous ne souhaitez pas créer ces méthodes directes, affectez à la `GenerateDbDirectMethods` propriété `false` dans le **propriétés** fenêtre. Si toutes les requêtes sont ajoutés à un TableAdapter en plus de la requête principale du TableAdapter, ils sont des requêtes autonomes qui ne génèrent pas ces méthodes DbDirect.  
  
## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly à une base de données  
 Appelez la méthode DbDirect du TableAdapter qui effectue la tâche que vous essayez d’accomplir.  
  
#### <a name="to-insert-new-records-directly-into-a-database"></a>Pour insérer de nouveaux enregistrements directement dans une base de données  
  
-   Appelez le TableAdapter `Insert` méthode, en passant les valeurs pour chaque colonne en tant que paramètres. La procédure suivante utilise le `Region` de table dans le databaseas Northwind un exemple.  
  
    > [!NOTE]
    >  Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
#### <a name="to-update-records-directly-in-a-database"></a>Pour mettre à jour des enregistrements directement dans une base de données  
  
-   Appelez le TableAdapter `Update` méthode, en passant les valeurs nouvelles et originale pour chaque colonne en tant que paramètres.  
  
    > [!NOTE]
    >  Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
#### <a name="to-delete-records-directly-from-a-database"></a>Pour supprimer des enregistrements directement à partir d’une base de données  
  
-   Appelez le TableAdapter `Delete` méthode, en passant les valeurs pour chaque colonne en tant que paramètres de la `Delete` (méthode). La procédure suivante utilise le `Region` de table dans le databaseas Northwind un exemple.  
  
    > [!NOTE]
    >  Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Voir aussi  
 [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

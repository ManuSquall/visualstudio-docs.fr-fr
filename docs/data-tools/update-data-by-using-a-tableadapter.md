---
title: "Mettre à jour des données à l’aide d’un TableAdapter | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 4968eab5e1d355543a8658e72540bc66fa2543b9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="update-data-by-using-a-tableadapter"></a>Mettre à jour des données à l’aide d’un TableAdapter
Une fois que les données dans votre jeu de données a été modifiées et validées, vous pouvez envoyer les données mises à jour à une base de données en appelant le `Update` méthode d’un [TableAdapter](../data-tools/create-and-configure-tableadapters.md). Le `Update` méthode met à jour une table de données unique et exécute la commande correcte (INSERT, UPDATE ou DELETE), selon le <xref:System.Data.DataRow.RowState%2A> de chaque ligne de données dans la table. Lorsque les tables sont liées à un jeu de données, Visual Studio génère une classe TableAdapterManager que vous utilisez pour les mises à jour. La classe TableAdapterManager garantit que les mises à jour sont effectuées dans l’ordre approprié selon les contraintes de clé étrangère sont définies dans la base de données. Lorsque vous utilisez des contrôles liés aux données, l’architecture de liaison de données crée une variable membre de la classe TableAdapterManager appelée tableAdapterManager. 
  
> [!NOTE]
>  Lorsque vous essayez de mettre à jour une source de données avec le contenu d’un dataset, vous pouvez obtenir des erreurs. Pour éviter les erreurs, nous vous recommandons de placer le code qui appelle l’adaptateur `Update` méthode à l’intérieur d’un `try` / `catch` bloc.  
  
 La procédure exacte de mise à jour d’une source de données peut varier en fonction des besoins, mais il inclut les étapes suivantes :  
  
1.  Appeler l’adaptateur `Update` méthode dans un `try` / `catch` bloc.  
  
2.  Si une exception est interceptée, recherchez la ligne de données qui a provoqué l’erreur. 
  
3.  Résolvez le problème dans les données de ligne (par programmation si possible, ou à l’aide de la ligne non valide pour l’utilisateur), puis essayez à nouveau la mise à jour (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).  
  
## <a name="save-data-to-a-database"></a>Enregistrer des données dans une base de données  
 Appelez le `Update` méthode d’un TableAdapter. Passez le nom de la table de données qui contient les valeurs à écrire dans la base de données.  
  
#### <a name="to-update-a-database-by-using-a-tableadapter"></a>Pour mettre à jour une base de données à l’aide d’un TableAdapter  
  
-   Placez du TableAdapter`Update` méthode dans un `try` / `catch` bloc. L’exemple suivant montre comment mettre à jour le contenu de la `Customers` table `NorthwindDataSet` à partir d’un `try` / `catch` bloc.  
  
     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
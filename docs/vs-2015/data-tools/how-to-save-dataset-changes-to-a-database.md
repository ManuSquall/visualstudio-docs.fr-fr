---
title: 'Comment : enregistrer les modifications de jeu de données dans une base de données | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DbDataAdapter.Update
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- databases, updating
- updating datasets, writing changes to data source
ms.assetid: c9970150-b71b-4c9d-a355-5efb6b510dca
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 60bb855202cfb333820fe2292fedc0b31608c5c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949017"
---
# <a name="how-to-save-dataset-changes-to-a-database"></a>Comment : enregistrer les modifications apportées à un groupe de données dans une base de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une fois que les données dans votre jeu de données a été modifiées et validées, vous souhaitez probablement renvoyer les données mises à jour à une base de données. Pour envoyer les données modifiées pour une base de données, vous appelez le `Update` méthode d’un [TableAdapter](../data-tools/tableadapter-overview.md) ou adaptateur de données. L’adaptateur `Update` méthode met à jour une table de données unique et exécute la commande correcte (INSERT, UPDATE ou DELETE), selon le <xref:System.Data.DataRow.RowState%2A> de chaque ligne de données dans la table.  
  
 Lors de l’enregistrement des données dans les tables associées, Visual Studio fournit un composant TableAdapterManager qui aide à effectuer des enregistrements dans l’ordre approprié selon les contraintes de clé étrangère définies dans la base de données. Pour plus d’informations, consultez [vue d’ensemble de mise à jour hiérarchique](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).  
  
> [!NOTE]
>  Étant donné que d’essayer de mettre à jour une source de données avec le contenu d’un dataset peut engendrer des erreurs, vous devez placer le code qui appelle l’adaptateur `Update` méthode à l’intérieur d’un `try` / `catch` bloc.  
  
 La procédure exacte pour mettre à jour une source de données peut varier en fonction des besoins de votre entreprise, mais votre application doit inclure les étapes suivantes :  
  
1.  Exécuter du code qui tente d’envoyer des mises à jour à la base de données au sein d’un `try` / `catch` bloc.  
  
2.  Si une exception est interceptée, recherchez la ligne de données qui a provoqué l’erreur. Pour plus d’informations, consultez [Comment : localiser les lignes qui ont les erreurs](http://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).  
  
3.  Résolvez le problème dans les données de ligne (par programmation si possible, ou à l’aide de la ligne non valide pour que l’utilisateur), puis retentez la mise à jour (<xref:System.Data.DataRow.HasErrors%2A> propriété, <xref:System.Data.DataTable.GetErrors%2A> méthode).  
  
## <a name="saving-data-to-a-database"></a>L’enregistrement des données à une base de données  
 Appelez le `Update` méthode d’un adaptateur de données ou du TableAdapter, en passant le nom de la table de données qui contient les valeurs à écrire dans la base de données. Pour plus d’informations sur l’enregistrement des données à partir d’une table de données unique dans une base de données, consultez [procédure pas à pas : enregistrement de données à une base de données (Table unique)](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-tableadapter"></a>Mettre à jour une base de données avec un jeu de données à l’aide d’un TableAdapter  
  
-   Placez le `TableAdapter.Update` méthode à l’intérieur d’un `try` / `catch` bloc. L’exemple suivant montre comment tenter une mise à jour avec le contenu de la `Customers` table dans le `NorthwindDataSet`.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-data-adapter"></a>Mettre à jour une base de données avec un jeu de données à l’aide d’un adaptateur de données  
  
-   Placez le `DataAdapter.Update` méthode à l’intérieur d’un `try` / `catch` bloc. L’exemple suivant montre comment tenter une mise à jour à une source de données avec le contenu de `Table1` dans `DataSet1`.  
  
     [!code-csharp[VbRaddataSaving#26](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#26)]
     [!code-vb[VbRaddataSaving#26](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#26)]  
  
## <a name="updating-two-related-tables-in-a-dataset"></a>La mise à jour deux Tables associées dans un jeu de données  
 Lors de la mise à jour des tables associées dans un jeu de données, il est important de mettre à jour dans l’ordre correct pour réduire le risque de violer les contraintes d’intégrité référentielle. L’ordre d’exécution des commandes respectera également les indices de la <xref:System.Data.DataRowCollection> dans le jeu de données. Pour empêcher les erreurs d’intégrité des données de déclenchement, la meilleure solution consiste à mettre à jour de la base de données dans l’ordre suivant :  
  
1. Table enfant : supprimer des enregistrements.  
  
2. Table parente : insérer, mettre à jour et supprimer des enregistrements.  
  
3. Table enfant : insérer et mettre à jour des enregistrements.  
  
   Pour plus d’informations sur l’enregistrement des données provenant de plusieurs tables, consultez [enregistrer les données dans une base de données (plusieurs tables)](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
   Si vous mettez à jour deux ou plusieurs tables connexes, vous devez inclure toute la logique de mise à jour dans une transaction. Une transaction est un processus qui garantit que toutes les modifications associées apportées à une base de données sont réussies avant de les valider. Pour plus d’informations, consultez [Transactions et la concurrence](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-update-two-related-tables-using-a-tableadapter"></a>Pour mettre à jour deux tables connexes à l’aide d’un TableAdapter  
  
1.  Créer trois temporaire <xref:System.Data.DataTable>destiné à contenir les enregistrements qui diffèrent.  
  
2.  Appelez le `Update` méthode pour chaque sous-ensemble de lignes à partir d’un `try` / `catch` bloc. En cas d’erreurs de mise à jour, au cours d’action suggéré consiste à créer des branches et de les résoudre.  
  
3.  Valider les modifications du jeu de données sur la base de données.  
  
4.  Supprimer les tables de données temporaires pour libérer les ressources.  
  
     [!code-csharp[VbRaddataSaving#27](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#27)]
     [!code-vb[VbRaddataSaving#27](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#27)]  
  
#### <a name="to-update-two-related-tables-using-a-data-adapter"></a>Pour mettre à jour deux tables connexes à l’aide d’un adaptateur de données  
  
-   Appelez le `Update` (méthode) de chaque adaptateur de données.  
  
     L’exemple suivant montre comment mettre à jour une source de données avec un jeu de données qui contient les tables associées. Pour pouvoir suivre la séquence utilisée ci-dessus, trois temporaire <xref:System.Data.DataTable>s sera créée pour contenir les enregistrements qui diffèrent. Le `Update` méthode sera appelée pour chaque sous-ensemble de lignes à partir d’un `try` / `catch` bloc. En cas d’erreurs de mise à jour, au cours d’action suggéré consiste à créer des branches et de les résoudre. Ensuite, le jeu de données valide les modifications. Enfin, supprimez les tables de données temporaires pour libérer les ressources.  
  
     [!code-csharp[VbRaddataSaving#28](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#28)]
     [!code-vb[VbRaddataSaving#28](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Enregistrer des données](../data-tools/saving-data.md)
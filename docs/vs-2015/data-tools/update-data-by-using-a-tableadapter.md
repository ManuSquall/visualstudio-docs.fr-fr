---
title: Mettre à jour des données à l’aide d’un TableAdapter | Microsoft Docs
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
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30d1fd3ee211d6b30f435104a2e2f9b42ed100c0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692343"
---
# <a name="update-data-by-using-a-tableadapter"></a>Mettre à jour les données à l’aide d’un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une fois que les données dans votre jeu de données a été modifiées et validées, vous pouvez envoyer les données mises à jour à un appel databaseby le `Update` méthode d’un TableAdapter. Le `Update` méthode met à jour une table de données unique et exécute la commande correcte (INSERT, UPDATE ou DELETE), selon le <xref:System.Data.DataRow.RowState%2A> de chaque ligne de données dans la table. Lorsque les tables sont liées à un jeu de données, Visual Studio génère une classe TableAdapterManager qui vous permet d’effectuer les mises à jour. La classe TableAdapterManager garantit que les mises à jour sont effectuées dans l’ordre approprié selon les contraintes de clé étrangère sont définies dans la base de données. Lorsque vous utilisez des contrôles liés aux données, l’architecture de liaison de données crée une variable de membre de la classe de TableAdapterManager appelée tableAdapterManager. Pour plus d’informations, consultez [vue d’ensemble de mise à jour hiérarchique](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).  
  
> [!NOTE]
> Lorsque vous essayez de mettre à jour d’une source de données avec le contenu d’un dataset, vous pouvez obtenir des erreurs. Pour éviter les erreurs, nous vous recommandons d’informer placer le code qui appelle l’adaptateur `Update` méthode à l’intérieur d’un `try` / `catch` bloc.  
  
 La procédure exacte de mise à jour d’une source de données peut varier en fonction des besoins de l’entreprise, mais il comprend les étapes suivantes :  
  
1. Appeler l’adaptateur `Update` méthode dans un `try` / `catch` bloc.  
  
2. Si une exception est interceptée, recherchez la ligne de données qui a provoqué l’erreur. Pour plus d'informations, voir [Procédure : Recherchez les lignes qui contiennent des erreurs](https://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).  
  
3. Résolvez le problème dans les données de ligne (par programmation si possible, ou à l’aide de la ligne non valide pour que l’utilisateur), puis réessayez la mise à jour (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).  
  
## <a name="savedata-to-a-database"></a>SaveData à une base de données  
 Appelez le `Update` méthode d’un TableAdapter. Passez le nom de la table de données qui contient les valeurs à écrire dans la base de données.  
  
#### <a name="to-update-a-database-by-using-a-tableadapter"></a>Pour mettre à jour une base de données à l’aide d’un TableAdapter  
  
- Placez le TableAdapter`Update` méthode dans un `try` / `catch` bloc. L’exemple suivant montre comment mettre à jour le contenu de la `Customers` table `NorthwindDataSet` depuis un `try` / `catch` bloc.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)

---
title: Mettre à jour les données à l’aide d’un TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: bcdf4c798960dacca6cfc11aaacd66c64b3a725e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036769"
---
# <a name="update-data-by-using-a-tableadapter"></a>Mettre à jour les données à l’aide d’un TableAdapter

Une fois que les données dans votre jeu de données a été modifiées et validées, vous pouvez envoyer les données mises à jour vers une base de données en appelant le `Update` méthode d’un [TableAdapter](../data-tools/create-and-configure-tableadapters.md). Le `Update` méthode met à jour une table de données unique et exécute la commande correcte (INSERT, UPDATE ou DELETE), selon le <xref:System.Data.DataRow.RowState%2A> de chaque ligne de données dans la table. Lorsque les tables sont liées à un jeu de données, Visual Studio génère une classe TableAdapterManager qui vous permet d’effectuer les mises à jour. La classe TableAdapterManager garantit que les mises à jour sont effectuées dans l’ordre approprié selon les contraintes de clé étrangère sont définies dans la base de données. Lorsque vous utilisez des contrôles liés aux données, l’architecture de liaison de données crée une variable de membre de la classe de TableAdapterManager appelée tableAdapterManager.

> [!NOTE]
> Lorsque vous essayez de mettre à jour d’une source de données avec le contenu d’un dataset, vous pouvez obtenir des erreurs. Pour éviter les erreurs, nous vous recommandons de placer le code qui appelle l’adaptateur `Update` méthode à l’intérieur d’un `try` / `catch` bloc.

 La procédure exacte de mise à jour d’une source de données peut varier en fonction des besoins de l’entreprise, mais il comprend les étapes suivantes :

1.  Appeler l’adaptateur `Update` méthode dans un `try` / `catch` bloc.

2.  Si une exception est interceptée, recherchez la ligne de données qui a provoqué l’erreur.

3.  Résolvez le problème dans les données de ligne (par programmation si possible, ou à l’aide de la ligne non valide pour que l’utilisateur), puis réessayez la mise à jour (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).

## <a name="save-data-to-a-database"></a>Enregistrer les données dans une base de données

Appelez le `Update` méthode d’un TableAdapter. Passez le nom de la table de données qui contient les valeurs à écrire dans la base de données.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Pour mettre à jour une base de données à l’aide d’un TableAdapter

-   Placez le TableAdapter`Update` méthode dans un `try` / `catch` bloc. L’exemple suivant montre comment mettre à jour le contenu de la `Customers` table `NorthwindDataSet` depuis un `try` / `catch` bloc.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 312bf75100d2b9b270b45776c5f7ded21ab6ac52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72602335"
---
# <a name="update-data-by-using-a-tableadapter"></a>Mettre à jour les données à l’aide d’un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une fois que les données de votre jeu de données ont été modifiées et validées, vous pouvez renvoyer les données mises à jour à un databaseby appelant la `Update` méthode d’un TableAdapter. La `Update` méthode met à jour une table de données unique et exécute la commande correcte (Insert, Update ou Delete) en fonction du <xref:System.Data.DataRow.RowState%2A> de chaque ligne de données dans la table. Quand un DataSet a des tables associées, Visual Studio génère une classe TableAdapterManager que vous utilisez pour effectuer les mises à jour. La classe TableAdapterManager garantit que les mises à jour sont effectuées dans l’ordre correct en fonction des contraintes de clé étrangère définies dans la base de données. Lorsque vous utilisez des contrôles liés aux données, l’architecture DataBinding crée une variable membre de la classe TableAdapterManager appelée tableAdapterManager. Pour plus d’informations, consultez [vue d’ensemble des mises à jour hiérarchiques](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).

> [!NOTE]
> Lorsque vous essayez de mettre à jour une source de données avec le contenu d’un DataSet, vous pouvez obtenir des erreurs. Pour éviter les erreurs, nous vous recommandons de thatyou placer le code qui appelle la méthode de l’adaptateur `Update` à l’intérieur d’un `try` / `catch` bloc.

 La procédure exacte pour la mise à jour d’une source de données peut varier en fonction des besoins de l’entreprise, mais elle comprend les étapes suivantes :

1. Appelez la méthode de l’adaptateur `Update` dans un `try` / `catch` bloc.

2. Si une exception est interceptée, localisez la ligne de données à l’origine de l’erreur. Pour plus d’informations, consultez [Comment : localiser des lignes qui contiennent des erreurs](https://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).

3. Rapprochez le problème dans la ligne de données (par programmation si vous le pouvez, ou en présentant la ligne non valide à l’utilisateur pour le modifier), puis recommencez la mise à jour ( <xref:System.Data.DataRow.HasErrors%2A> , <xref:System.Data.DataTable.GetErrors%2A> ).

## <a name="savedata-to-a-database"></a>SaveData à une base de données
 Appelez la `Update` méthode d’un TableAdapter. Transmettez le nom de la table de données qui contient les valeurs à écrire dans la base de données.

#### <a name="to-update-a-database-by-using-a-tableadapter"></a>Pour mettre à jour une base de données à l’aide d’un TableAdapter

- Placez la méthode du TableAdapter `Update` dans un `try` / `catch` bloc. L’exemple suivant montre comment mettre à jour le contenu de la `Customers` table dans `NorthwindDataSet` à partir d’un `try` / `catch` bloc.

     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]

## <a name="see-also"></a>Voir aussi
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)

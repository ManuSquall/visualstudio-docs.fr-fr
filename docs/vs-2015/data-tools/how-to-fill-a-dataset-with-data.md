---
title: 'Comment : remplir un dataset avec des données | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapter.GetData
- TableAdapter.Fill
- datasets [Visual Basic], filling
- DataTable objects, loading
- data [Visual Basic], loading into datasets
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f36aa2dac656f6fd27b656d0ddfb58a758eb6487
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295995"
---
# <a name="how-to-fill-a-dataset-with-data"></a>Comment : remplir un dataset avec des données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’expression « remplissage d’un dataset avec des données » fait référence au chargement des données dans les <xref:System.Data.DataTable> objets qui composent le jeu de données. Vous remplissez les tables de données en exécutant des requêtes TableAdapter ou en exécutant l’adaptateur de données (par exemple, <xref:System.Data.SqlClient.SqlDataAdapter>) commandes.  
  
 Si vous devez utiliser des adaptateurs TableAdapters ou des données dépend de la façon dont vous avez créé le jeu de données. Si vous avez utilisé les outils de conception dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], telles que la [Assistant de Configuration de Source de données](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f), votre jeu de données contient des TableAdapters. Pour plus d’informations sur les TableAdapters, consultez [vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md). Si vous avez créé votre jeu de données par programmation, vous devrez généralement créer des adaptateurs de données pour charger des données dans les tables de données.  
  
> [!NOTE]
>  Lorsque vous faites glisser des éléments à partir de la [fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) sur un formulaire, le code pour remplir la table de données avec des données est automatiquement ajouté à la `Form_Load` Gestionnaire d’événements. Ouvrir votre formulaire dans l’éditeur de code pour afficher la syntaxe exacte pour remplir vos tables spécifiques. Si vous ne souhaitez pas remplir la table lors du chargement du formulaire, vous pouvez déplacer ce code vers une autre méthode ou supprimez-le entièrement.  
  
## <a name="filling-a-dataset-using-a-tableadapter"></a>Remplissage d’un Dataset à l’aide d’un TableAdapter  
 Vous pouvez appeler une requête sur le TableAdapter pour charger des données dans les tables de données d’un jeu de données. Passer le <xref:System.Data.DataTable> à remplir à la requête TableAdapter. Si votre requête accepte des paramètres, transférer ces informations à la méthode également. Si le jeu de données contient plusieurs tables, vous devez avoir des TableAdapters distincts pour chaque table et donc de remplir chaque table séparément.  
  
> [!NOTE]
>  Par défaut, chaque fois que vous exécutez une requête TableAdapter, les données dans la table sont effacées avant les résultats de la requête en cours de chargement dans la table. Vous pouvez conserver les données existantes dans la table et ajouter les résultats en définissant le TableAdapter `ClearBeforeFill` propriété `false`.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-tableadapter"></a>Pour remplir un dataset avec des données à l’aide d’un TableAdapter  
  
1.  Ouvrez votre formulaire ou composant dans le **éditeur de Code**.  
  
2.  Ajoutez le code n’importe où dans votre application où vous devez charger une table de données avec des données. Si votre requête ne prend pas de paramètres, passez le <xref:System.Data.DataTable> vous souhaitez remplir. Le code doit ressembler à ce qui suit :  
  
     [!code-csharp[VbRaddataFillingAndExecuting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#4)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#4)]  
  
3.  Si votre requête accepte des paramètres, passez le <xref:System.Data.DataTable> vous souhaitez remplir et les paramètres attendus par la requête. Selon les paramètres réels dans votre requête, le code ressemblerait similaire aux exemples suivants :  
  
     [!code-csharp[VbRaddataFillingAndExecuting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#5)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#5)]  
  
## <a name="filling-a-dataset-using-a-dataadapter"></a>Remplissage d’un Dataset à l’aide d’un DataAdapter  
 Vous appelez l’adaptateur de données `Fill` (méthode). Cela entraîne l’adaptateur exécuter l’instruction SQL ou procédure stockée référencé dans son `SelectCommand` propriété et placer les résultats dans une table dans le jeu de données. Si le jeu de données contient plusieurs tables, vous devez avoir des adaptateurs de données distinct pour chaque table et donc de remplir chaque table séparément.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-dataadapter"></a>Pour remplir un dataset avec des données à l’aide d’un DataAdapter  
  
-   Appelez le <xref:System.Data.Common.DataAdapter.Fill%2A> méthode de la <xref:System.Data.Common.DataAdapter>, en passant le <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> pour charger les données dans. Exemple :  
  
     [!code-csharp[VbRaddataFillingAndExecuting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#6)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#6)]  
  
     Vous devez généralement fournir le nom de la <xref:System.Data.DataTable> pour charger les données dans. Si vous passez le nom d’un <xref:System.Data.DataSet> au lieu d’une table de données spécifique, un <xref:System.Data.DataTable> nommé `Table1` est ajoutée au jeu de données et chargé avec les résultats à partir de la base de données (plutôt que de charger les données dans une existante <xref:System.Data.DataTable> dans le jeu de données). Pour plus d’informations, consultez [remplissage d’un DataSet à partir d’un DataAdapter](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
## <a name="see-also"></a>Voir aussi  
 [Remplir des jeux de données à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Enregistrer des données](../data-tools/saving-data.md)
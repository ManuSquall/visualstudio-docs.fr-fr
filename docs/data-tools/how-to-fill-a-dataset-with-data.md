---
title: "Comment&#160;: remplir de donn&#233;es un groupe de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "données (Visual Basic), charger dans les groupes de données"
  - "groupes de données (Visual Basic), remplir"
  - "objets DataTable, charger"
  - "TableAdapter.Fill"
  - "TableAdapter.GetData"
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Comment&#160;: remplir de donn&#233;es un groupe de donn&#233;es
L'expression « remplissage d'un groupe de données avec des données » fait référence au chargement de données dans les objets <xref:System.Data.DataTable> qui composent le groupe de données.  Pour remplir les tables de données, vous devez exécuter des requêtes TableAdapter, ou des commandes d'adaptateur de données \(par exemple, des commandes <xref:System.Data.SqlClient.SqlDataAdapter>\).  
  
 Le choix d'utiliser des TableAdapters ou des adaptateurs de données dépend de la manière dont vous avez créé le groupe de données.  Si vous avez utilisé les outils de conception dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], tel que l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png), votre groupe de données contient des TableAdapters.  Pour plus d'informations sur les TableAdapters, consultez [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md).  Si vous avez créé votre groupe de données par programmation, vous devez généralement créer des adaptateurs de données pour charger des données dans les tables de données.  
  
> [!NOTE]
>  Lorsque vous faites glisser des éléments de la [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md) sur un formulaire, le code permettant de remplir la table de données est ajouté automatiquement au gestionnaire d'événements `Form_Load`.  Ouvrez votre formulaire dans l'éditeur de code pour afficher la syntaxe exacte permettant de remplir vos tables spécifiques.  Si vous ne souhaitez pas remplir la table lors du chargement du formulaire, vous pouvez déplacer ce code vers une autre méthode ou le supprimer intégralement.  
  
## Remplissage d'un groupe de données à l'aide d'un TableAdapter  
 Vous pouvez appeler une requête sur le TableAdapter pour charger des données dans des tables de données d'un groupe de données.  Passez le <xref:System.Data.DataTable> que vous souhaitez remplir à la requête TableAdapter.  Si votre requête prend des paramètres, vous devez les passer également à la méthode.  Si le groupe de données contient plusieurs tables, vous devez posséder des TableAdapters distincts pour chaque table et il est donc nécessaire de remplir chaque table séparément.  
  
> [!NOTE]
>  Par défaut, à chaque exécution d'une requête TableAdapter, les données contenues dans la table sont effacées avant que les résultats de la requête soient chargés dans la table.  Vous pouvez conserver les données existantes dans la table et ajouter les résultats en affectant à la propriété `ClearBeforeFill` du TableAdapter la valeur `false`.  
  
#### Pour remplir de données un groupe de données à l'aide d'un TableAdapter  
  
1.  Ouvrez votre formulaire ou composant dans l'**éditeur de code**.  
  
2.  Ajoutez du code à tout endroit de votre application où vous devez charger une table de données avec des données.  Si votre requête ne prend pas de paramètre, passez le <xref:System.Data.DataTable> que vous souhaitez remplir.  Le code doit se présenter comme suit :  
  
     [!code-cs[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_1.vb)]  
  
3.  Si votre requête prend des paramètres, passez le <xref:System.Data.DataTable> que vous souhaitez remplir et les paramètres attendus par la requête.  Selon les paramètres réels contenus dans votre requête, le code peut se présenter comme dans les exemples suivants :  
  
     [!code-cs[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_2.vb)]  
  
## Remplissage d'un groupe de données à l'aide d'un DataAdapter  
 Vous devez appeler la méthode `Fill` de l'adaptateur de données.  Dans ce cas, l'adaptateur exécute l'instruction SQL ou la procédure stockée référencée dans sa propriété `SelectCommand` et insère les résultats dans une table du groupe de données.  Si le groupe de données contient plusieurs tables, vous devez disposer d'adaptateurs de table distincts pour chaque table et il est donc nécessaire de remplir chaque table séparément.  
  
#### Pour remplir de données un groupe de données à l'aide d'un DataAdapter  
  
-   Appelez la méthode <xref:System.Data.Common.DataAdapter.Fill%2A> du <xref:System.Data.Common.DataAdapter>, en passant dans le <xref:System.Data.DataSet> ou le <xref:System.Data.DataTable> dans lequel charger les données.  Par exemple :  
  
     [!code-cs[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_3.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_3.vb)]  
  
     Vous devez généralement fournir le nom du <xref:System.Data.DataTable> dans lequel charger les données.  Si vous passez le nom d'un <xref:System.Data.DataSet> et non d'une table de données spécifique, un <xref:System.Data.DataTable> nommé `Table1` est ajouté au groupe de données et chargé avec les résultats de la base de données \(plutôt que de charger les données dans un <xref:System.Data.DataTable> existant dans le groupe de données\).  Pour plus d'informations, consultez [Remplissage d'un DataSet à partir d'un DataAdapter](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md).  
  
## Voir aussi  
 [Remplissage de groupes de données avec des données](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)
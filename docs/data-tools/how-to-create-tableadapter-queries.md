---
title: "Comment&#160;: cr&#233;er des requ&#234;tes TableAdapter | Microsoft Docs"
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
  - "données (Visual Studio), requêtes TableAdapter"
  - "requêtes (Visual Studio), créer"
  - "requêtes (Visual Studio), TableAdapters"
  - "TableAdapters, créer des requêtes"
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Comment&#160;: cr&#233;er des requ&#234;tes TableAdapter
Les requêtes TableAdapter sont des instructions SQL ou des procédures stockées que votre application peut exécuter sur une base de données.  
  
 Ajoutez autant de requêtes à un TableAdapter que l'exige votre application.  Les requêtes TableAdapter apparaissent en tant que méthodes sur un TableAdapter.  Lorsque vous créez une requête appelée `FillByCity` qui prend un paramètre représentant la valeur City, cette requête est ajoutée au TableAdapter.  Elle est ajoutée en tant que méthode typée qui prend le type correct de paramètre comme argument \(dans ce cas\-ci, une chaîne représentant la valeur City\).  Vous pouvez appeler la requête TableAdapter de la même façon qu'une méthode quelconque pour n'importe quel objet.  Par exemple, le code suivant exécute la requête `FillByCity` et remplit la table `Customers` avec tous les clients possédant une valeur City de `Seattle` :  
  
 [!CODE [VbRaddataTableAdapters#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#1)]  
  
 Les requêtes TableAdapter peuvent remplir une table de données \(requêtes `Fill` et `FillBy`\) ou retourner de nouvelles tables de données remplies avec les données retournées par la requête \(requêtes `GetData` et `GetDataBy`\).  
  
 Vous pouvez ajouter des requêtes à des TableAdapters existants en exécutant l' [Configuration de requête TableAdapter \(Assistant\)](../data-tools/editing-tableadapters.md).  \(Cliquez avec le bouton droit sur un TableAdapter et choisissez **Ajouter une requête**.\)  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Créez une requête dans le Concepteur de DataSet  
  
#### Pour ajouter une requête à un TableAdapter dans le Concepteur de DataSet  
  
1.  Ouvrez un groupe de données dans le **Concepteur de DataSet**.  Pour plus d'informations, consultez [Comment : ouvrir un groupe de données dans le Concepteur de DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Cliquez avec le bouton droit sur le TableAdapter souhaité et sélectionnez **Ajouter une requête**.  
  
     ou  
  
3.  Faites glisser une **Requête** depuis l'onglet **DataSet** de la **Boîte à outils** jusqu'à une table dans le concepteur.  
  
     L'**Assistant Configuration de requêtes TableAdapter** s'ouvre.  
  
4.  Une fois l'Assistant terminé, la requête est ajoutée au TableAdapter.  
  
## Créez directement une requête dans un formulaire de votre application Windows  
 Si vous avez une instance d'un TableAdapter sur votre formulaire, vous pouvez ajouter une requête à l'aide du [Générateur de critères de recherche, boîte de dialogue](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md) qui ajoute un contrôle <xref:System.Windows.Forms.ToolStrip> au formulaire qui accepte tous les paramètres d'entrée requis par la requête, ainsi qu'un bouton pour exécuter celle\-ci.  
  
#### Pour ajouter une requête à un TableAdapter à l'aide de la boîte de dialogue Critère de recherche  
  
1.  Sélectionnez un TableAdapter dans la barre d'état des composants.  
  
2.  Cliquez sur la balise active du TableAdapter et choisissez **Ajouter une requête**.  
  
3.  Complétez la boîte de dialogue afin d'ajouter la requête au TableAdapter.  Pour plus d'informations, consultez [Générateur de critères de recherche, boîte de dialogue](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
## Voir aussi  
 [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Comment : modifier des requêtes TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Comment : établir une connexion à des données d'une base de données](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Comment : naviguer parmi les données avec le contrôle BindingNavigator Windows Forms](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [Procédure pas à pas : affichage de données sur un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Procédure pas à pas : création d'un TableAdapter avec plusieurs requêtes](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)
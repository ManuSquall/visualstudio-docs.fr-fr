---
title: "Modification des donn&#233;es dans les groupes de donn&#233;es | Microsoft Docs"
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
  - "données (Visual Studio), modifier dans les groupes de données"
  - "groupes de données (Visual Basic), modifier des données"
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 15
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Modification des donn&#233;es dans les groupes de donn&#233;es
La modification de données dans un <xref:System.Data.DataSet> est le processus de manipulation des données effectives dans les objets <xref:System.Data.DataTable> individuels qui composent un groupe de données.  Vous modifiez les données dans les tables de données de la même façon que vous modifiez les données d'une table dans une base de données quelconque ; ce processus peut inclure l'insertion, la mise à jour et la suppression d'enregistrements dans la table.  
  
 En plus de modifier les données effectives, vous pouvez également interroger une <xref:System.Data.DataTable> pour qu'elle retourne des lignes de données spécifiques, par exemple, des lignes individuelles, des versions spécifiques de lignes \(d'origine et proposé\), uniquement les lignes qui ont changé et lignes contenant des erreurs.  
  
## Tâches courantes sur les tables de données  
 Le tableau suivant fournit des liens vers les tâches courantes associées à la modification et à l'interrogation de données dans un groupe de données :  
  
|Tâche|Description|  
|-----------|-----------------|  
|Insérer de nouveaux enregistrements dans une table de données.|Créez une <xref:System.Data.DataRow> et ajoutez\-la à la collection de lignes de la table.  Pour plus d'informations, consultez [Comment : ajouter des lignes à un DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md).|  
|Mettre à jour des enregistrements existants dans une table de données.|Assignez directement une valeur à la colonne spécifique d'une ligne de données.  Pour plus d'informations, consultez [Comment : modifier des lignes dans un DataTable](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md).|  
|Supprimer des enregistrements d'une table de données|Appelez la méthode <xref:System.Data.DataRow.Delete%2A> de la ligne de données que vous voulez supprimer de la table.  Pour plus d'informations, consultez [Comment : supprimer des lignes d'un DataTable](../Topic/How%20to:%20Delete%20Rows%20in%20a%20DataTable.md).|  
|Localiser des enregistrements modifiés dans une table de données.|Appelez la méthode <xref:System.Data.DataTable.GetChanges%2A> d'une table de données.  Pour plus d'informations, consultez [Comment : récupérer des lignes modifiées](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).|  
|Accéder aux différentes versions d'une ligne dans une table de données.|Accédez aux colonnes individuelles d'une ligne de données en passant la <xref:System.Data.DataRowVersion> que vous voulez visualiser.  Pour plus d'informations, consultez [Comment : obtenir des versions spécifiques d'un DataRow](../Topic/How%20to:%20Get%20Specific%20Versions%20of%20a%20DataRow.md).|  
|Localiser des lignes contenant des erreurs dans une table de données.|Inspectez la propriété <xref:System.Data.DataTable.HasErrors%2A> d'une table de données.  Pour plus d'informations, consultez [Comment : trouver des lignes contenant des erreurs](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md).|  
  
## Voir aussi  
 [DataTable, objets](../Topic/DataTables.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [DataTable, objets](../Topic/DataTables.md)   
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vue d'ensemble d'applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)
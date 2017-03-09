---
title: "Relations dans les groupes de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbData.Microsoft.VSDesigner.DataSource.DesignRelation"
  - "vbdata.Microsoft.VSDesigner.DataSource.DesignRelation"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "groupes de données (Visual Basic), relations"
  - "relations, à propos des relations"
  - "relations, groupes de données"
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Relations dans les groupes de donn&#233;es
Un groupe de données peut contenir des tables connexes comme une base de données relationnelle.  L'objet **DataRelation** facilite la relation entre des tables de données.  Les rubriques suivantes présentent les objets **DataRelation** de ADO.NET et vous expliquent comment les créer et les utiliser pour manipuler les données des tables liées.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Dans cette section  
 [Introduction aux objets DataRelation](../Topic/Introduction%20to%20DataRelation%20Objects.md)  
 Explique comment les groupes de données vous permettent de spécifier des relations entre les tables et comment vous pouvez tirer profit de ces relations.  
  
 [Comment : créer des DataRelations avec le Concepteur de DataSet](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)  
 Explique comment ajouter un objet <xref:System.Data.DataRelation> à un groupe de données à l'aide du **Concepteur de DataSet**.  
  
 [Comment : accéder aux enregistrements dans les DataTables connexes](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md)  
 Explique comment retourner par programme des enregistrements liés dans un groupe de données typé avec les tables dans une relation un\-à\-plusieurs.  
  
 [Procédure pas à pas : création d'une relation entre des tables de données](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)  
 Fournit des instructions pas à pas pour la création de deux tables de données à l'aide du **Concepteur de DataSet** et l'ajout d'une relation entre eux.  
  
## Référence  
 <xref:System.Data.DataRelation>  
 Représente une relation parent\/enfant entre deux objets T:System.Data.DataTable.  
  
 <xref:System.Data.DataRow.GetChildRows%2A>  
 Obtient les lignes enfants d'un T:System.Data.DataRow.  
  
 <xref:System.Data.DataRow.GetParentRow%2A>  
 Obtient les lignes parentes d'un T:System.Data.DataRow.  
  
 <xref:System.Data.Rule>  
 Indique l'action qui se produit lors de l'application de <xref:System.Data.ForeignKeyConstraint>.  
  
 <xref:System.Data.DataColumn.Unique%2A>  
 Obtient ou définit une valeur qui indique si les valeurs contenues dans chaque ligne de la colonne doivent être uniques.  
  
 <xref:System.Data.Constraint>  
 Représente une contrainte qui peut être appliquée à un ou plusieurs objets <xref:System.Data.DataColumn>.  
  
## Rubriques connexes  
 [Ajout d'objets DataRelation](../Topic/Adding%20DataRelations.md)  
 Explique comment créer des relations entre différentes tables d'un <xref:System.Data.DataSet>.  
  
 [Exploration des DataRelations](../Topic/Navigating%20DataRelations.md)  
 Explique comment utiliser les relations entre différentes tables d'un <xref:System.Data.DataSet> afin de retourner les lignes enfants ou parentes d'une relation parent\-enfant.  
  
 [Imbrication de DataRelations](../Topic/Nesting%20DataRelations.md)  
 Explique l'importance des objets <xref:System.Data.DataRelation> imbriqués lorsqu'il s'agit de représenter le contenu d'un <xref:System.Data.DataSet> sous forme de données XML, et décrit la façon de les créer.
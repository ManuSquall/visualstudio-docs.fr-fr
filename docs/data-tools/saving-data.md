---
title: "Enregistrement des donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataRow.RowState"
  - "DataSet.GetChanges"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "données (Visual Studio), enregistrer"
  - "données (Visual Studio), mettre à jour"
  - "bases de données, mettre à jour"
  - "DBDirect (méthodes)"
  - "enregistrer les données"
  - "TableAdapter (méthodes DBDirect)"
  - "TableAdapter.Update (méthode)"
  - "mise à jour de données"
  - "mettre à jour les bases de données"
ms.assetid: 21d2b115-62e4-4ac9-a873-dcbb535b8af8
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Enregistrement des donn&#233;es
L'enregistrement des données est le processus consistant à rendre persistantes des données modifiées dans un modèle de données d'une application en les consignant à nouveau dans le magasin de données d'origine, en général une base de données relationnelle telle que SQL Server.  
  
 La mise à jour d'une source de données au moyen d'un modèle de données s'effectue généralement en deux étapes.  La première étape consiste à mettre à jour le modèle de données avec les nouvelles informations \(nouveaux enregistrements, enregistrements modifiés ou supprimés\).  La deuxième étape consiste à enregistrer les modifications apportées à votre modèle de données dans la base de données.  
  
 Les rubriques suivantes décrivent les concepts et les tâches liés à l'enregistrement de données.  
  
## Rubriques connexes  
 [Enregistrement de données dans des groupes de données](../data-tools/save-data-back-to-the-database.md)  
 Présente la façon dont les modifications sont effectuées dans un groupe de données et la façon dont le groupe de données effectue le suivi des informations relatives à ces modifications afin d'enregistrer ces dernières dans une base de données.  
  
 [Enregistrement d'Entity Data](../data-tools/saving-entity-data.md)  
 Explique comment enregistrer des modifications dans [ADO.NET Entity Framework](../Topic/ADO.NET%20Entity%20Framework.md) et les applications des [WCF Data Services 4.5](../Topic/WCF%20Data%20Services%204.5.md).
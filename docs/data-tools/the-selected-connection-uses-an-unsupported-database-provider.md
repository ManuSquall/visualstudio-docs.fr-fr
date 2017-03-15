---
title: "La connexion s&#233;lectionn&#233;e utilise un fournisseur de base de donn&#233;es non pris en charge | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# La connexion s&#233;lectionn&#233;e utilise un fournisseur de base de donn&#233;es non pris en charge
Ce message apparaît lorsque vous faites glisser des éléments qui n'utilisent pas le fournisseur de données .NET Framework pour SQL Server de l'**Explorateur de serveurs**\/**Explorateur de bases de données** dans le [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 Le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] prend uniquement en charge les connexions de données qui utilisent le fournisseur .NET Framework pour SQL Server.Seules les connexions à Microsoft SQL Server ou aux fichiers de base de données Microsoft SQL Server sont valides.  
  
### Pour corriger cette erreur  
  
-   Ajoutez uniquement des éléments des connexions de données qui utilisent le fournisseur de données .NET Framework pour SQL Server au [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## Voir aussi  
 <xref:System.Data.SqlClient>   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/fr-fr/360c340d-e5a6-4a7e-a569-e95d500be43d)   
 [Fournisseurs de données .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [Procédure pas à pas : création de classes LINQ to SQL \(Concepteur O\/R\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Création d'applications de données](../data-tools/creating-data-applications.md)
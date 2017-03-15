---
title: "Vous avez s&#233;lectionn&#233; un objet de base de donn&#233;es dans un fournisseur de base de donn&#233;es non pris en charge | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vous avez s&#233;lectionn&#233; un objet de base de donn&#233;es dans un fournisseur de base de donn&#233;es non pris en charge
Le [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) prend uniquement en charge le fournisseur de données .NET Framework pour SQL Server \(<xref:System.Data.SqlClient>\).Bien que vous puissiez cliquer sur **OK** et continuer d'utiliser des objets de fournisseurs de base de données non pris en charge, vous risquez de rencontrer des comportements inattendus au moment de l'exécution.  
  
> [!NOTE]
>  Seules les connexions de données qui utilisent le fournisseur de données .NET Framework pour SQL Server sont prises en charge.  
  
### Pour corriger cette erreur  
  
-   Cliquez sur **OK** pour continuer de concevoir les classes d'entité qui mappent à la connexion utilisée par le fournisseur de bases de données non pris en charge.Vous risquez de rencontrer des comportements inattendus en utilisant des fournisseurs de base de données non pris en charge.  
  
     \- ou \-  
  
-   Cliquez sur **Annuler**.  
  
     L'action est arrêtée.Créez ou utilisez une connexion de données qui utilise le fournisseur .NET Framework pour SQL Server.  
  
## Voir aussi  
 [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Fournisseurs de données .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)
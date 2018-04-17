---
title: La connexion sélectionnée utilise un fournisseur de base de données non pris en charge | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 199bd6ba18f9ac2e7eecbc13868c8c4bc8e829f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La connexion sélectionnée utilise un fournisseur de base de données non pris en charge
Ce message apparaît lorsque vous faites glisser des éléments qui n’utilisent pas le fournisseur de données .NET Framework pour SQL Server à partir de **l’Explorateur de serveurs**/**l’Explorateur de base de données** sur la [LINQ to SQL Outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 Le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] prend uniquement en charge les connexions de données qui utilisent le fournisseur .NET Framework pour SQL Server. Seules les connexions à Microsoft SQL Server ou aux fichiers de base de données Microsoft SQL Server sont valides.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajoutez uniquement des éléments des connexions de données qui utilisent le fournisseur de données .NET Framework pour SQL Server au [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## <a name="see-also"></a>Voir aussi
<xref:System.Data.SqlClient>  
[Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

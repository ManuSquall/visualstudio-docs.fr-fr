---
title: La connexion sélectionnée utilise un fournisseur de base de données non pris en charge | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4e717bf0f1da2b7b25d62d4639690ae1cce0273
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49241356"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La connexion sélectionnée utilise un fournisseur de base de données non pris en charge
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Ce message apparaît lorsque vous faites glisser des éléments qui n’utilisent pas le fournisseur de données .NET Framework pour SQL Server à partir de **Explorateur de serveurs**/**Database Explorer** sur la [LINQ to SQL Outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 Le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] prend uniquement en charge les connexions de données qui utilisent le fournisseur .NET Framework pour SQL Server. Seules les connexions à Microsoft SQL Server ou aux fichiers de base de données Microsoft SQL Server sont valides.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajoutez uniquement des éléments des connexions de données qui utilisent le fournisseur de données .NET Framework pour SQL Server au [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.SqlClient>   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Fournisseurs de données .NET framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Création d’applications de données](../data-tools/creating-data-applications.md)


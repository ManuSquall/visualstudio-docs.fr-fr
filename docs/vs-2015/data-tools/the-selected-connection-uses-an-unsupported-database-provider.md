---
title: La connexion sélectionnée utilise un fournisseur de base de données non pris en charge | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4e79d8408fba54cf192d51f9d2ead8c0ffafe1f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667195"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La connexion sélectionnée utilise un fournisseur de base de données non pris en charge
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce message s’affiche lorsque vous faites glisser des éléments qui n’utilisent pas la .NET Framework fournisseur de données pour SQL Server de **Explorateur de serveurs** / **Explorateur de base de données** sur les [outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

 Le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] prend uniquement en charge les connexions de données qui utilisent le fournisseur .NET Framework pour SQL Server. Seules les connexions à Microsoft SQL Server ou aux fichiers de base de données Microsoft SQL Server sont valides.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Ajoutez uniquement des éléments des connexions de données qui utilisent le fournisseur de données .NET Framework pour SQL Server au [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

## <a name="see-also"></a>Voir aussi
 <xref:System.Data.SqlClient>[.NET Framework des fournisseurs](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) [de données procédure pas à pas : création de classes LINQ to SQL (Concepteur O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)